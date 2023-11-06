# Firefighters SRE Workshop Platform Provisionamento

## Componentes da Arquitetura

1. **Kafka (AMQ Streams)**: Plataforma distribuída para construção de pipelines de dados em tempo real. Usada para mensagens e streaming entre microservices.
2. **Prometheus**: Ferramenta open-source de monitoramento e alerta. Coleta métricas de targets configurados, avalia expressões de regra e dispara alertas conforme as condições.
3. **Grafana**: Plataforma open-source para monitoramento e observabilidade. Visualiza métricas do Prometheus.
4. **Jaeger**: Ferramenta de tracing distribuído para monitorar e solucionar transações em sistemas distribuídos.
5. **KEDA (Kubernetes Event-Driven Autoscaling)**: Permite autoscaling avançado, incluindo baseado em eventos. **!OPCIONAL**
6. **Red Hat OpenShift Pipelines**: Solução Kubernetes-native de CI/CD baseada no Tekton, integrante da CD Foundation. **!OPCIONAL**

## Microsserviços

1. 🛎️ [**Access Microservice (concierge-app)**](https://github.com/firefighters-sre/concierge-app): Gerencia entrada e saída de indivíduos do edifício.
2. 🚶‍♂️🔝 [**Mobility Microservice (mobility-app)**](https://github.com/firefighters-sre/mobility-app): Monitora uso de escadas e elevadores.
3. 🏠 [**Building Microservice (building-app)**](https://github.com/firefighters-sre/building-app): Informações do edifício como temperatura e ocupação.

## Pré-requisitos

- OpenShift Cluster (OCP)
- Helm 3.x
- OpenShift CLI (`oc`)

## Quick Start

### 1. Namespaces

1. **quarkus-dev**: Aloca microservices Quarkus.
2. **kafka-streaming**: Para componentes Kafka.
3. **kafka-logging**: Para monitoramento com Prometheus e Grafana.
4. **openshift-distributed-tracing**: Para componentes de tracing distribuído. (*Não precisa ser criado!*)

#### 1.1.1 Criar Namespaces
1. Criando os namespaces no cluster:

```bash
# Desenvolvimento Quarkus: Aloca os microservices Quarkus.
oc new-project quarkus-dev

# Kafka Streaming: Para clusters e tópicos Kafka.
oc new-project kafka-streaming

# Monitoramento (Prometheus & Grafana): Para registro e monitoramento.
oc new-project kafka-logging
```

2. Validando:

```bash
# Verifica se o namespace quarkus-dev foi criado corretamente.
oc get namespace quarkus-dev

# Verifica se o namespace kafka-streaming foi criado corretamente.
oc get namespace kafka-streaming

# Verifica se o namespace kafka-logging foi criado corretamente.
oc get namespace kafka-logging
```

### 2. Instalar Operators
Um **Operator** no contexto do OpenShift e Kubernetes é uma forma de empacotar, implantar e gerenciar aplicações Kubernetes. Os Operators seguem os princípios do Kubernetes, especialmente o controle de aplicações, que são implantadas automaticamente. Isso permite que os desenvolvedores e administradores de cluster se concentrem na lógica e nos recursos específicos da aplicação, enquanto o Operator cuida de tarefas comuns e repetitivas.

Para instalar os operators a partir do OperatorHub no OpenShift, siga os passos abaixo:

1. Acesse o console web do OpenShift.
2. No menu de navegação à esquerda, clique em "Operators" e selecione "OperatorHub".
3. Use a barra de pesquisa para encontrar e selecionar os operators desejados.
4. Siga as instruções na tela para instalar cada operator.

Instale os seguintes operators a partir do OperatorHub do OpenShift:

- **Red Hat Integration AMQ Streams**: Fornece uma plataforma de streaming distribuída.
- **Prometheus Operator**: Ferramenta de monitoramento e alerta. **(Nota: Instale no namespace kafka-logging)**
- **Red Hat OpenShift distributed tracing platform**: Fornece ferramentas para tracing distribuído.

### 3. Instalar Helm Charts

Helm é uma ferramenta que auxilia na gestão de aplicações Kubernetes através de pacotes chamados "charts". Estes charts definem e fornecem dependências para aplicações Kubernetes de forma consistente.

**Clone o repositório:**
```bash
git clone https://github.com/quarkus-sre/charts
```

**Navegue até o diretório dos charts para instalar:**
```bash
cd charts
```

1. **AMQ Streams**
```bash
helm template -f amqstreams/values-cluster-with-metrics.yaml amqstreams | oc apply -f-
```
2. **Prometheus**
```bash
helm template -f prometheus/values.yaml prometheus | oc apply -f-
```
3. **Grafana**
```bash
helm template -f grafana/values.yaml grafana | oc apply -f-
```
- Configure manualmente a fonte de dados Prometheus no Grafana.
  - **URL**: `http://prometheus-operated:9090`
- Configure manualmente a fonte de dados AlertManager no Grafana.
  - **URL**: `alertmanager:9093`
- Importe os dashboards do Grafana:
  - Vá para a seção "Dashboards" no Grafana.
  - Clique em "Import" e selecione os arquivos JSON:
    - Strimzi Kafka Exporter Dashboard (grafana-dashboards/kafka-exporter.json)
    - Quarkus SRE Dashboard (grafana-dashboards/sre-quarkus.json)
  
4. **Jaeger**
```bash
helm template -f jaeger/values.yaml jaeger | oc apply -f-
```

#### Passos de Validação

Após a instalação dos components, é crucial validar se tudo foi configurado corretamente. Siga os passos abaixo para validar cada componente:

1. **AMQ Streams:**
   - Execute o seguinte comando para listar todos os clusters Kafka:
   ```bash
   oc get kafka -n kafka-streaming
   ```
   - Você deve ver o seu cluster Kafka listado.

2. **Prometheus:**
   - Abra um navegador e navegue até a URL especificada na rota Prometheus. Você pode obter a URL executando:
   ```bash
   oc get route prometheus -n kafka-logging -o jsonpath='{.spec.host}'
   ```
   - No UI do Prometheus, verifique os targets para garantir que estejam ativos e coletando métricas.

3. **Grafana:**
   - Abra um navegador e navegue até a URL especificada na rota Grafana. Você pode obter a URL executando:
   ```bash
   oc get route grafana -n kafka-logging -o jsonpath='{.spec.host}'
   ```
   - Faça login e verifique se as fontes de dados Prometheus e AlertManager estão configuradas corretamente.
   - Valide se os dashboards importados estão disponíveis e exibindo dados.

4. **Jaeger:**
   - Abra um navegador e navegue até a URL especificada na rota Jaeger. Você pode obter a URL executando:
   ```bash
   oc get route jaeger -n openshift-distributed-tracing -o jsonpath='{.spec.host}'
   ```
   - Valide se os traces estão sendo coletados e exibidos no UI do Jaeger.

### 4. Implantando as Aplicações

Para implantar os microserviços individuais, você precisará clonar seus repositórios e aplicar os respectivos Helm charts localizados nas pastas .chart. Assegure-se de estar no namespace correto (quarkus-dev) antes de prosseguir:

```bash
oc project quarkus-dev
```

Siga os passos para cada microserviço:
#### Access Microservice (concierge-app)
1. Clone o repositório:
```bash
git clone https://github.com/firefighters-sre/concierge-app.git
```

2. Navegue até o diretório clonado e implante o Helm chart:
```bash
cd concierge-app
helm dependency update .chart
helm template .chart/ | oc apply -f-
```

#### Mobility Microservice (mobility-app)
1. Clone o repositório:
```bash
git clone https://github.com/firefighters-sre/mobility-app.git
```

2. Navegue até o diretório clonado e implante o Helm chart:
```bash
cd mobility-app
helm dependency update .chart
helm template .chart/ | oc apply -f-
```

#### Configurando o Banco de Dados PostgreSQL para o Building Microservice
O Building Microservice (building-app) requer um banco de dados PostgreSQL para armazenamento persistente. Veja como configurá-lo:

**Implantando PostgreSQL no OpenShift**
1. Criar Implantação PostgreSQL:

```bash
#O OpenShift fornece modelos para implantar o PostgreSQL. Você pode instanciar um desses modelos para implantar uma instância PostgreSQL:
oc new-app postgresql-persistent --param POSTGRESQL_USER=userWPM --param POSTGRESQL_PASSWORD=Oiu5HI4nBLDbYtHo --param POSTGRESQL_DATABASE=firefighters

#Verifique se o pod PostgreSQL está em execução:
oc get pods | grep postgresql
```

#### Building Microservice (building-app)
1. Clone o repositório:
```bash
git clone https://github.com/firefighters-sre/building-app.git
```
2. Navegue até o diretório clonado e implante o Helm chart:
```bash
cd building-app
helm dependency update .chart
helm template .chart/ | oc apply -f-
```

Após implantar os Helm charts, os microserviços devem estar em execução em seu cluster Kubernetes. Você pode verificar o status da implantação usando oc get pods.
