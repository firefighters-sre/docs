# 2. Monitoramento, SLIs, SLOs, SLAs

No universo da Engenharia de Confiabilidade (SRE), o monitoramento é um pilar fundamental. Ele permite que as equipes de engenharia mantenham um pulso constante na saúde e no desempenho de seus sistemas, garantindo que os serviços atendam às expectativas definidas em termos de confiabilidade e disponibilidade. O monitoramento eficaz é vital para identificar rapidamente problemas potenciais e agir antes que esses problemas afetem adversamente os usuários ou a integridade do sistema.

## 2.1 A Fundamentação do Monitoramento em Engenharia de Confiabilidade (SRE)
O monitoramento é a espinha dorsal da Engenharia de Confiabilidade (SRE). Ele nos capacita a compreender e otimizar a saúde e o desempenho de nossos sistemas, permitindo:

- **Antecipar problemas** através de alertas proativos.
- **Diagnóstico rápido** de questões emergentes.
- **Visualização clara** do estado e comportamento do sistema.
- **Análise de tendências**, auxiliando no planejamento de longo prazo.
- **Comparação de métricas** para avaliar impactos de mudanças ou experimentos.

### SLIs, SLOs e SLAs: Medindo e Definindo a Confiabilidade
- **SLIs (Indicadores de Nível de Serviço)**: Métricas específicas que refletem a qualidade do serviço.
- **SLOs (Objetivos de Nível de Serviço)**: Metas estabelecidas para os SLIs, indicando o desempenho desejado.
- **SLAs (Acordos de Nível de Serviço)**: Compromissos formais relacionados ao nível de serviço fornecido.

### Conceitos Chave
- **SLIs (Indicadores de Nível de Serviço)**: São métricas específicas e quantificáveis que representam aspectos essenciais da qualidade do serviço, como tempo de resposta e taxa de erro.
- **SLOs (Objetivos de Nível de Serviço)**: São metas ou limites estabelecidos para os SLIs. Representam o nível mínimo aceitável de desempenho ou confiabilidade de um serviço.
- **SLAs (Acordos de Nível de Serviço)**: São compromissos contratuais que descrevem o nível de serviço esperado, normalmente associados a penalidades ou recompensas.

### Monitoramento na Prática
O monitoramento eficaz não se trata apenas de coletar métricas. Envolve interpretar esses dados, tomar decisões informadas e agir proativamente para garantir a saúde contínua dos sistemas. Através de atividades práticas, os participantes aprenderão a estabelecer um monitoramento robusto, definindo SLIs, SLOs e SLAs para serviços críticos, e a responder a incidentes usando dados de monitoramento.

### 4 SRE Golden Signals

Ao monitorar sistemas voltados para o usuário, é essencial focar nos "4 SRE Golden Signals", que são:

1. **Latência**: Refere-se ao tempo necessário para atender a uma solicitação. É crucial diferenciar entre a latência de solicitações bem-sucedidas e falhas.
2. **Tráfego**: Representa a demanda colocada no seu sistema. Pode ser medido como solicitações por segundo ou outras métricas específicas do sistema.
3. **Erros**: Indica a taxa de solicitações que falham, seja explicitamente ou implicitamente.
4. **Saturação**: Mostra quão "cheio" está o seu serviço, destacando os recursos mais restritos.

Ao medir e alertar com base nesses quatro sinais, podemos garantir que o sistema esteja bem monitorado e que quaisquer problemas sejam rapidamente identificados e resolvidos.

##### 2.2 Abordagem Prática
- **Desafio**: Estabelecer um monitoramento efetivo para os serviços essenciais do edifício, tais como a disponibilidade de elevadores e as condições ambientais.
- **Passo-a-Passo**:
  1. **Definição do Cenário**: Grupos são apresentados a um cenário específico relacionado ao edifício, como uma falha no sistema de elevadores ou uma mudança nas condições ambientais.
         - 🚨 **Alerta**: O cenário específico ainda precisa ser definido e elaborado.
  2. **Identificação de KPIs**: Discussão colaborativa sobre quais indicadores-chave de desempenho (KPIs) são críticos para o cenário apresentado. Exemplos podem incluir tempo médio de resposta de um elevador ou qualidade do ar no edifício.
  3. **Estabelecimento de SLIs e SLOs**: Com base nos KPIs, os grupos discutem e definem os Indicadores de Nível de Serviço (SLIs) que representam medidas quantitativas de qualidade. Em seguida, definem os Objetivos de Nível de Serviço (SLOs), que são metas específicas associadas aos SLIs.
  4. **Simulação de Monitoramento em Tempo Real**:
     - **Criação de um Dashboard Físico**: Utilizando um quadro, os participantes criam um dashboard que represente visualmente os SLIs e SLOs definidos.
  5. **Reflexão e Feedback**: Após a simulação, os grupos refletem sobre a eficácia de seus SLIs, SLOs e sua resposta aos comandos. Discussões podem abordar melhorias, lacunas identificadas e a aplicação dos "4 Sinais Dourados" no contexto do cenário.

##### 2.3 Plataforma e Ferramentas

### Ferramentas de Monitoramento e Alertas

Ao coletar métricas de aplicações e sistemas, é essencial ter ferramentas robustas que não apenas armazenem e visualizem esses dados, mas também forneçam mecanismos eficazes de alerta para situações anômalas. Aqui, descrevemos três ferramentas centrais usadas para esses propósitos:

- **Prometheus**:
  - **Descrição**: Prometheus é uma ferramenta de monitoramento e alerta de código aberto que se integra perfeitamente a sistemas e aplicações para coletar métricas em intervalos específicos.
  - **Repositório do Template**: O template usado para configurar e implantar o Prometheus no OpenShift está disponível [aqui](https://github.com/quarkus-sre/charts/tree/main/charts/prometheus).

- **AlertManager**:
  - **Descrição**: Gerencia os alertas enviados pelo Prometheus, agrupando-os e roteando-os para o destino correto, como e-mail, Slack ou outras integrações.
  - **Repositório do Template**: O template usado para configurar e implantar o AlertManager no OpenShift pode ser encontrado [aqui](https://github.com/quarkus-sre/charts/blob/main/charts/prometheus/templates/alertmanager.yaml).

- **Grafana**:
  - **Descrição**: Grafana é uma plataforma de visualização de métricas que permite criar e visualizar dashboards com dados coletados pelo Prometheus.
  - **Repositório dos Dashboards**: Este repositório contém configurações de dashboards Grafana personalizadas e está localizado [aqui](https://github.com/firefighters-sre/grafana-dashboards).
    - [Service Levels Dashboard](https://github.com/firefighters-sre/grafana-dashboards/blob/main/grafana-servicelevels-dashboard.json): Fornece insights sobre os níveis de serviço do aplicativo ou sistema.
    - [SRE Dashboard](https://github.com/firefighters-sre/grafana-dashboards/blob/main/grafana-sre-dashboard.json): Oferece uma visão geral da confiabilidade do sistema e outras métricas-chave de SRE.
  - **Repositório do Template Grafana**: A configuração usada para implantar o Grafana no OpenShift pode ser encontrada [aqui](https://github.com/quarkus-sre/charts/tree/main/charts/grafana).


- **Desafio**: Utilizar o OpenShift para implementar e monitorar as soluções discutidas anteriormente.
- **Passo-a-Passo**:
  1. **Integração com Quarkus**:
     - Demonstração de como usar as extensões Quarkus (`quarkus-smallrye-health`, `quarkus-micrometer-registry-prometheus`) para monitoramento e health checks do `concierge-app`.
     - Configuração de métricas(`@Timed`) nas classes (`AccessLogResource`, `AccessLogService`) usando as bibliotecas Quarkus(`microprofile-metrics-api`).
     - Visão geral de como as métricas(`/q/metrics`) e verificações de integridade do Quarkus se integram ao OpenShift e Prometheus com o `PodMonitor`.
  2. Introdução à interface do OpenShift e suas capacidades de monitoramento. (OpenShift Monitoring, Prometheus Operator, Dashboards)  
  3. **Exploração da Implementação Atual**:
     - Visão geral das três aplicações no OpenShift. `Topology`
     - Introdução às métricas existentes e como elas são coletadas e exibidas no Grafana e Prometheus. `Prometheus`, `ServiceMonitor`, `Grafana`
     - Análise da comunicação entre as aplicações através do Kafka. `Dashboard Grafana Kafka Exporter` 
  4. Implementação dos KPIs discutidos anteriormente no OpenShift, configurando alertas e dashboards.
  5. **Otimização do Monitoramento**:
     - Introdução às métricas existentes e como elas são coletadas e exibidas no Grafana e Prometheus. `Prometheus`, `ServiceMonitor`, `Grafana`
     - Avaliação das métricas atuais e identificação de possíveis lacunas ou métricas adicionais. `Dashboard Grafana Service Levels`  `Dashboard Grafana SRE` 
     - Configuração de alertas no Prometheus para métricas críticas. `Alert Manager`
     - Discussão sobre como os SLIs, SLOs e SLAs existentes se traduzem em configurações no Prometheus e Grafana. `PrometheusRules`

### Monitoramento com Quarkus e OpenShift
O serviço [`concierge-app`](https://github.com/firefighters-sre/concierge-app/blob/main/pom.xml), além de seus endpoints padrão, expõe métricas e verificações de saúde graças às extensões Quarkus.

Essas métricas monitoram o tempo que leva para processar eventos do lobby, fornecendo insights valiosos sobre a eficiência e o desempenho do sistema em situações do mundo real.

1. **Definição da Métrica**:

Vamos focar especificamente nas métricas `processLobbyPostTime` e `processLobbyEventTime`.

1. Na classe [`AccessLogResource`](https://github.com/firefighters-sre/concierge-app/blob/main/src/main/java/com/redhat/quarkus/resources/AccessLogResource.java):
    ```java
    @Timed(name = "processLobbyPostTime", description = "Time taken to process a lobby POST call.", unit = MetricUnits.MILLISECONDS)
    ```
2. Na classe [`AccessLogService`](https://github.com/firefighters-sre/concierge-app/blob/main/src/main/java/com/redhat/quarkus/services/AccessLogService.java):
    ```java
    @Timed(name = "processLobbyEventTime", description = "Time taken to process a lobby event.", unit = MetricUnits.MILLISECONDS)
    ```

A anotação `@Timed` define a métrica, especificando seu nome, descrição e unidade de medida. Ela instrui o Quarkus a coletar dados sobre o tempo que leva para executar o método anotado.
Quando os métodos anotados com `@Timed` são invocados, o Quarkus coleta automaticamente os dados de tempo de execução. Estes dados são expostos através do endpoint `[APP_URL/q/metrics](APP_URL/q/metrics)`. Esta coleta e exposição de métricas é facilitada pelo Micrometer, uma biblioteca de instrumentação de aplicativos que suporta uma variedade de sistemas de monitoramento.

2. **Micrometer Metrics**: 

O Micrometer se posiciona como uma fachada para a instrumentação de aplicações, permitindo que desenvolvedores coletem métricas sem se vincularem a uma solução de monitoramento específica. Ao integrar o Micrometer com o Quarkus, somos capazes de expor uma rica gama de métricas através do endpoint `/q/metrics`.

Apenas adicionando a extensão Micrometer, uma vasta quantidade de métricas são expostas por padrão. Estas incluem:
   - Métricas sobre a JVM, como:
     - Número de threads vivas: `jvm_threads_live_threads`
     - Uso de memória, garbage collection, e outras métricas relacionadas ao ciclo de vida da JVM.
   - Métricas sobre o sistema operacional, incluindo:
     - Uso atual da CPU: `system_cpu_usage`
     - Contagem de processadores disponíveis, carga de trabalho, entre outros.

3. **Integração com OpenShift**:
Quando o serviço `concierge-app` é implantado no OpenShift, os recursos `PodMonitor` e `ServiceMonitor` são utilizados para detectar automaticamente os endpoints de métricas expostos e integrá-los ao sistema de monitoramento Prometheus. Isso permite que os operadores visualizem as métricas em tempo real no painel do OpenShift.

#### ServiceMonitor
O recurso `ServiceMonitor` é uma definição customizada que instrui o Prometheus sobre como monitorar serviços no Kubernetes. Vamos examinar a configuração do `ServiceMonitor` para o `concierge-app`:
```yaml
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: concierge-app
  namespace: kafka-logging
  labels:
    helm.sh/chart: quarkus-app-chart-1.0.3
    app.kubernetes.io/name: concierge-app
    ...
spec:
  namespaceSelector:
    matchNames:
      - helm-test
  endpoints:
    - interval: 15s
      path: /q/metrics
      port: tcp-8080
      scheme: http
  selector:
    matchLabels:
      deploymentconfig: concierge-app
```
Nesta definição, especificamos que o Prometheus deve coletar métricas do endpoint /q/metrics a cada 15 segundos.

#### PodMonitor
O PodMonitor é semelhante ao ServiceMonitor, mas, como o nome sugere, ele se destina a monitorar pods individuais. Aqui está a configuração para o concierge-app:

```yaml
apiVersion: monitoring.coreos.com/v1
kind: PodMonitor
metadata:
  name: concierge-app
  namespace: kafka-logging
  labels:
    helm.sh/chart: quarkus-app-chart-1.0.3
    app.kubernetes.io/name: concierge-app
    ...
spec:
  namespaceSelector:
    matchNames:
      - helm-test
  podMetricsEndpoints:
    - interval: 15s
      path: /q/metrics
      targetPort: 8080
      scheme: http
  selector:
    matchLabels:
      deploymentconfig: concierge-app
```
Novamente, estamos instruindo o Prometheus para coletar métricas do endpoint /q/metrics a cada 15 segundos, mas, neste caso, diretamente dos pods.

Com essas definições em vigor, o OpenShift, juntamente com o Prometheus, pode automaticamente descobrir e monitorar as métricas do concierge-app.

4. **Visualização e Alertas**:
Com as métricas sendo coletadas pelo Prometheus, é essencial ter ferramentas que permitam visualizar essas métricas e configurar alertas para monitorar de perto a saúde e o desempenho do sistema. Grafana é uma plataforma de análise e monitoramento amplamente utilizada para visualizar métricas, enquanto PrometheusRules pode ser usada para definir condições de alerta com base nas métricas coletadas.
#### Dashboards Grafana
  - **Repositório dos Dashboards**: Este repositório contém configurações de dashboards Grafana personalizadas para monitoramento de níveis de serviço e métricas de SRE (Engenharia de Confiabilidade do Site). Está localizado [aqui](https://github.com/firefighters-sre/grafana-dashboards).
  - **Dashboards Disponíveis**:
    - [Service Levels Dashboard](https://github.com/firefighters-sre/grafana-dashboards/blob/main/grafana-servicelevels-dashboard.json): Este painel oferece insights sobre os níveis de serviço do aplicativo ou sistema. Inclui métricas como SLIs, SLOs e taxas de erro.
    - [SRE Dashboard](https://github.com/firefighters-sre/grafana-dashboards/blob/main/grafana-sre-dashboard.json): Feito para equipes de SRE, este painel fornece uma visão geral da confiabilidade do sistema, taxas de erro e outras métricas-chave de SRE.
#### Regras do Prometheus (PrometheusRules)
As regras do Prometheus são configurações que definem condições sob as quais alertas serão enviados. As regras para o `concierge-app` estão definidas como:

```yaml
apiVersion: monitoring.coreos.com/v1
kind: PrometheusRule
metadata:
  name: concierge-app-slos
  namespace: kafka-logging
  labels:
    role: alert-rules
    app: prometheus
spec:
  groups:
  - name: concierge-app.slos.rules
    rules:
    # Availability: Ensures that the application has an uptime of 99.9% over a 10-minute window.
    - alert: concierge-app Availability Below Threshold
      annotations:
        message: 'concierge-app in namespace helm-test has been unavailable for more than 0.1% in the last 10 minutes.'
      expr: (1 - avg_over_time(up{namespace="helm-test", app="concierge-app"}[10m])) > 0.001
      for: 1m
      labels:
        severity: warning

    # API Response Time: Average response time for API requests should be under 200ms.
    - alert: concierge-app High API Response Time
      annotations:
        message: 'concierge-app in namespace helm-test has an average response time of more than 200ms in the last 10 minutes.'
      expr: rate(http_request_duration_seconds_sum{namespace="helm-test", app="concierge-app"}[10m]) / rate(http_request_duration_seconds_count{namespace="helm-test", app="concierge-app"}[10m]) > 0.2
      for: 10m
      labels:
        severity: warning

    # Error Rate: Less than 0.1% of all API requests should result in errors (4xx and 5xx responses).
    - alert: concierge-app High Error Rate
      annotations:
        message: 'concierge-app in namespace helm-test has an error rate of more than 0.1% in the last 10 minutes.'
      expr: rate(http_requests_total{namespace="helm-test", app="concierge-app", status=~"4..|5.."}[10m]) / rate(http_requests_total{namespace="helm-test", app="concierge-app"}[10m]) > 0.001
      for: 10m
      labels:
        severity: warning
```

Estas regras definem condições para alertas como disponibilidade do aplicativo, tempo de resposta da API e taxas de erro. Uma vez que estas condições são atendidas, alertas são disparados.

Monitorar o tempo de processamento dos eventos do lobby é crucial para garantir que o serviço esteja respondendo de maneira eficiente. Qualquer atraso ou inconsistência pode ser rapidamente identificado e resolvido antes de se tornar um problema maior.
