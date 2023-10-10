## Workshop SRE
-  **HORA INICIAL**: 09:00
-  **HORA INICIAL**: 18:00

## Formatos
- PALESTRA
- ATIVIDADE
- OPENSHIFT

---
### Agenda

#### APRESENTAÇÃO SRE 101
-  **HORA INICIAL**: 09:15
-  **HORA INICIAL**: 09:30
-  **FORMATO**: PALESTRA
-  **DESCRIÇÃO**: Apresentação sobre os conceitos iniciais de SRE.

### 2. "Planejando a resposta a um incidente."
- **Horário de Início**: 09:30
- **Horário de Término**: 10:00
- **Formato**: ATIVIDADE
- **Objetivo da Atividade**: Esta atividade visa capacitar os participantes a pensar estrategicamente e adaptar-se rapidamente a mudanças em situações de emergência. O foco é combinar o planejamento prévio com a capacidade de reagir a novas informações em tempo real, uma habilidade crucial em SRE.
- **Tags SRE**: Incident Response
- **Nível na Hierarquia SRE**: Incident Response

##### 2.1 METODOLOGIA
- **Desafio**: Simular uma situação de emergência no edifício e identificar as melhores rotas de evacuação.
- **Passo-a-Passo**:
    1. Distribuir um mapa impresso do edifício para cada participante ou equipe. Este mapa deve detalhar o layout, saídas, escadas, elevadores e possíveis obstáculos (por exemplo, locais de incêndio).
    2. Informar os participantes sobre uma situação de emergência simulada (como um incêndio) e desafiá-los a marcar as rotas de evacuação mais rápidas e seguras no mapa.
    3. Eles têm um tempo definido (por exemplo, 10 minutos) para planejar e marcar suas rotas.
    4. Após o planejamento, cada participante ou equipe explica brevemente sua rota escolhida e sua justificativa.
    5. Os facilitadores discutem escolhas comuns, possíveis gargalos e estratégias de evacuação ideais com base nas rotas desenhadas.
    6. Os facilitadores podem introduzir mudanças repentinas (por exemplo, "A escada oeste agora está bloqueada!") para testar a adaptabilidade dos participantes.
    
##### 2.2 TECNOLOGIA
- **Passo-a-Passo**:
  1. **Visão Geral**: Introdução ao sistema Firefighters SRE, um sistema projetado para simular a gestão e monitoramento de um edifício. Diferentes microserviços são responsáveis por monitorar e gerenciar aspectos específicos, como acesso de pessoas, mobilidade, ambiente e segurança do edifício.
    - **Pilha Tecnológica**:
       - Microserviços: Quarkus
       - Plataforma de Mensagens: AMQ Streams (Kafka) e Red Hat Fuse (Apache Camel)
       - Banco de Dados: PostgreSQL
       - Implantação: OpenShift (Kubernetes com Helm charts)
       - Monitoramento e Rastreamento: Prometheus, Jaeger e Grafana
    - **Microserviços**:
       - 🛎️ `Access Microservice (concierge-app)`: Gerencia a entrada e saída de indivíduos do edifício.
       - 🚶‍♂️🔝 `Mobility Microservice (mobility-app)`: Monitora e gerencia a utilização de escadas e elevadores.
       - 🏠 `Building Microservice (building-app)`: Gerencia informações relacionadas ao edifício, como temperatura, qualidade do ar e ocupação do piso.
    - **Tópicos Kafka**:
       - `Lobby (lobby)`: Coleta eventos relacionados às atividades no saguão do edifício.
       - `Lobby (lobby)`: Coleta eventos relacionados às atividades no saguão do edifício.
       - `Entrance (entrance)`: Manipula eventos pós-processamento do Lobby, marcando a entrada de indivíduos no edifício.
       - `Elevator (elevator)`: Captura eventos associados às operações do elevador.
       - `Stairs (stairs)`: Coleta dados sobre o uso de escadas.
       - `Exit (exit)`: Coleta eventos relacionados à saída de indivíduos do edifício.
       - `External (external)`: Coleta eventos originados de sistemas ou dispositivos externos ao edifício.
  2. **Testes Unitários com Quarkus**:
    - Demonstração de como configurar e executar `testes unitários` na aplicação quarkus `concierge-app`. 
#### 3. "Monitoramento, SLIs, SLOs, SLAs."
- **Horário de Início**: 10:00
- **Horário de Término**: 11:00
- **Formato**: ATIVIDADE, OPENSHIFT
- **Tags SRE**: Monitoramento, SLIs, SLOs, SLAs, Incidente, Resposta
- **Nível na Hierarquia SRE**: Monitoring
- **Descrição**: Nesta sessão, os participantes trabalharão para estabelecer monitoramento eficaz, definir SLIs, SLOs e SLAs para serviços críticos do edifício, e responder a incidentes com base em dados de monitoramento.

##### 3.1 ATIVIDADE
- **Desafio**: Estabelecer monitoramento eficaz para serviços críticos do edifício, como disponibilidade de elevadores e condições ambientais.
- **Passo-a-Passo**:
  1. Grupos recebem um cenário para ser analisado.
  2. Discussão sobre KPIs que devem ser monitorados.
  3. Discussão sobre que SLIs e SLOs seriam criados.
  4. Criação de um dashboard físico em um quadro. Os participantes representam pontos de dados e devem mover-se para diferentes áreas do dashboard em resposta a comandos vocais (por exemplo, 'Falha no elevador!').
    - Esta atividade simula visualmente o monitoramento em tempo real.

##### 3.2 OPENSHIFT
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

#### 4. "Análise Pós-Incidente"
- **Horário de Início**: 11:15
- **Horário de Término**: 12:00
- **Formato**: ATIVIDADE, OPENSHIFT
- **Tags SRE**: Post-Mortem, RCA, Segurança, Incidente
- **Nível na Hierarquia SRE**: PostMortem/RCA
- **Descrição**: Nesta sessão, os participantes conduzirão uma análise pós-incidente após um incidente simulado no edifício, identificando causas raiz, fatores contribuintes e áreas de melhoria.

##### 4.1 ATIVIDADE
- **Desafio**: Conduzir uma análise pós-incidente após um incidente simulado no edifício.
- **Passo-a-Passo**:
  1. Apresentação do cenário do incidente simulado, como uma violação de segurança ou perigo ambiental.
  2. Acesso ao sistema Firefighters SRE para obter dados do incidente, logs e informações relevantes.
  3. Identificação de causas raiz e análise de fatores contribuintes.
  4. Colaboração na elaboração de recomendações e criação de um relatório de incidente detalhado.
  5. Apresentação das descobertas e melhorias propostas por cada equipe.

##### 4.2 OPENSHIFT
- **Desafio**: Utilizar o OpenShift para acessar e analisar dados do incidente.
- **Passo-a-Passo**:
  1. Introdução aos recursos do OpenShift relacionados ao acesso e análise de logs e dados de incidentes. `Logs, EFK`
  2. Uso prático do OpenShift para recuperar `logs` e dados específicos do incidente simulado.
  3. Discussão sobre como o OpenShift pode ajudar a identificar rapidamente causas raiz e facilitar a análise pós-incidente.
  5. Demonstração de como recuperar ou revertir para uma configuração anterior usando `ConfigMaps` e `Secrets` em caso de uma configuração problemática.
  6. Como o `Jaeger` e tracing pode ajudar a identificar rapidamente pontos problemáticos ou falhas em microserviços interconectados.

#### 5. "Gestão de Capacidade, Segurança e Otimização de Evacuação"
- **Horário de Início**: 13:30
- **Horário de Término**: 14:30
- **Formato**: ATIVIDADE, OPENSHIFT
- **Tags SRE**: Gestão de Capacidade, Segurança, Automação, Otimização de Evacuação, 9S de Disponibilidade
- **Nível na Hierarquia SRE**: Capacidade + Testes + Procedimentos de Release + Reduzir Toil + 9S de Disponibilidade
- **Descrição**: Nesta sessão, os participantes trabalharão na gestão eficaz da capacidade do edifício e na alocação de recursos durante situações de emergência. Além disso, eles irão simular exercícios de segurança automatizados e otimizar rotas de evacuação.

##### 5.1 ATIVIDADE - Definindo 9S de Disponibilidade no Complexo SkyTower
- **Desafio**: Utilizando um cenário fictício do "Complexo SkyTower", os participantes terão que definir os 9S de disponibilidade de seu sistema de segurança e elevadores, considerando um orçamento específico.
- **Passo-a-Passo**:
  1. **Contextualização do Complexo SkyTower**:
     - O "Complexo SkyTower" é um conjunto de três edifícios corporativos interconectados no coração da cidade. 
     - O sistema de segurança é vital, controlando o acesso de milhares de pessoas diariamente, além de gerenciar os elevadores inteligentes que otimizam o transporte entre os andares.
  2. **Introdução aos 9S de Disponibilidade**:
     - Explicação sobre o que significa cada 'nove' em termos de tempo de inatividade por ano, mês, semana e dia.
     - Discussão sobre a importância de atingir altos níveis de disponibilidade em sistemas críticos como os do SkyTower.
  3. **Definindo o Orçamento de Erro**:
     - Os participantes recebem um orçamento fictício de $500.000, que representa o custo operacional do sistema de segurança e elevadores por ano.
     - Cada minuto de inatividade do sistema custa ao Complexo $1.000 em perdas operacionais.
     - Os participantes devem calcular o custo total de inatividade com base nos diferentes níveis de disponibilidade (por exemplo, 99%, 99,9%, 99,99%).
  4. **Impacto de Não Cumprir os 9S**:
     - Discussão sobre o impacto operacional e de segurança de falhas no sistema.
     - E se um diretor estiver preso no elevador durante uma falha? E se uma falha de segurança permitir o acesso de pessoas não autorizadas?
  5. **Tomada de Decisão**:
     - Com os dados em mãos, os participantes devem decidir:
       - Quanto do orçamento devem alocar para melhorias no sistema, visando aumentar a disponibilidade.
       - Quais áreas são prioritárias (por exemplo, redundância de sistema, treinamento da equipe, infraestrutura melhorada).
     - A ideia é equilibrar o orçamento disponível com o nível de disponibilidade desejado, levando em consideração os riscos e impactos.
  6. **Apresentação das Soluções**:
     - Cada grupo apresenta sua estratégia, justificando suas escolhas e defendendo a eficácia de sua abordagem perante os desafios apresentados.
  
##### 5.2 OPENSHIFT
- **Desafio**: Automatizar exercícios de segurança e otimizar rotas de evacuação usando OpenShift.
- **Passo-a-Passo**:
  1. Demonstração de como o microserviço `mobility-app` otimiza as rotas com base em dados em tempo real.
  2. **Introdução a Readiness e Liveness Probes**: Breve explicação sobre sua importância em ambientes Kubernetes.
  3. **Simulação de Falhas no `mobility-app`**: Criar um cenário onde o `mobility-app` enfrenta problemas e não está pronto para receber tráfego ou está falhando durante sua execução.
  4. **Implementação de Probes**: Os participantes serão guiados para adicionar Readiness e Liveness probes ao `mobility-app`.
  5. **Validação e Observação**: Após a implementação, os participantes poderão observar como o Kubernetes reage às falhas e como os probes ajudam a garantir que o tráfego só seja enviado para pods saudáveis.

#### 6. "Design de Sistema em Larga Escala" (Opcional)
- **Horário de Início**: [DEFINIR HORA]
- **Horário de Término**: [DEFINIR HORA]
- **Formato**: ATIVIDADE, OPENSHIFT
- **Tags SRE**: Design de Sistema, Consenso Distribuído, Paxos, Alta Disponibilidade, Integridade de Dados
- **Nível na Hierarquia SRE**: Development
- **Descrição**: Nesta sessão, os participantes serão desafiados a projetar um sistema em larga escala que possa lidar com estado crítico e consenso distribuído.

##### 6.1 ATIVIDADE
- **Desafio**: Projetar um sistema em larga escala que incorpore princípios de consenso distribuído (como Paxos) e possa escalar para suportar operações distribuídas globalmente.
- **Passo-a-Passo**:
  1. Introdução aos conceitos de consenso distribuído e a sua importância em sistemas em larga escala.
  2. Discussão sobre desafios comuns em design de sistemas de grande escala, como manter a alta disponibilidade e integridade dos dados.
  3. Os participantes trabalharão em equipes para esboçar um design de sistema que atenda aos requisitos fornecidos.
  4. Cada equipe apresentará seu design, justificando suas escolhas e como elas garantem a confiabilidade do sistema.
  5. Feedback será fornecido para cada design, com discussão sobre melhores práticas e possíveis otimizações.

##### 6.2 OPENSHIFT
- **Desafio**: Implementar um componente do sistema projetado no OpenShift e observar sua escalabilidade e robustez.
- **Passo-a-Passo**:
  1. Introdução sobre como o OpenShift pode suportar sistemas de grande escala e distribuídos.
  2. Implementação de um componente ou serviço básico do design proposto usando recursos do OpenShift.
  3. Monitoramento da solução implementada, observando métricas de desempenho e confiabilidade.
  4. Discussão sobre otimizações e ajustes para melhorar a eficiência e confiabilidade do componente/serviço.
  5. Discussão sobre o uso de `HPA (Horizontal Pod Autoscaling)` e budgets de interrupção de pod para garantir a resiliência e eficiência das aplicações.
  6. **HPA e KEDA:** Uso do `HPA` (Horizontal Pod Autoscaler) e `KEDA` para escalabilidade dinâmica conforme a demanda durante evacuações.

#### 7. "Pipelines de Processamento de Dados" (Opcional)
- **Horário de Início**: [DEFINIR HORA]
- **Horário de Término**: [DEFINIR HORA]
- **Formato**: ATIVIDADE, OPENSHIFT
- **Tags SRE**: Processamento de Dados, Pipelines, Batch Processing, Real-time Data Streams, Escalabilidade, Integridade de Dados
- **Nível na Hierarquia SRE**: Development
- **Descrição**: Nesta sessão, os participantes aprenderão a construir e gerenciar pipelines de processamento de dados para diferentes casos de uso, lidando com desafios de escalabilidade e integridade de dados.

##### 7.1 ATIVIDADE
- **Desafio**: Construir e gerenciar pipelines de processamento de dados que possam atender diferentes requisitos, desde processamento em lote até fluxos de dados em tempo real.
- **Passo-a-Passo**:
  1. Introdução aos conceitos de pipelines de processamento de dados, diferenciando processamento em lote e fluxos de dados em tempo real.
  2. Discussão sobre desafios comuns, como escalabilidade e garantia de integridade dos dados.
  3. Usando objetos físicos como bolas ou mármores, os participantes formam uma linha de montagem, simulando um pipeline de processamento de dados. O objetivo é garantir que nenhum "dado" seja perdido e lidar com "gargalos".
  4. Reflexão sobre a atividade, discutindo os desafios enfrentados e como eles se relacionam com pipelines de processamento de dados reais.

##### 7.2 OPENSHIFT
- **Desafio**: Implementar e testar um pipeline de processamento de dados no OpenShift.
- **Passo-a-Passo**:
  1. Introdução à implementação de pipelines de processamento de dados no OpenShift.
  2. Os participantes trabalharão em equipes para configurar e testar um pipeline básico no OpenShift.
  3. Discussão sobre otimizações e melhores práticas ao trabalhar com pipelines de processamento de dados no OpenShift.

---
#### 8. "Lançamentos de Produtos Confiáveis" (Opcional)
- **Horário de Início**: [DEFINIR HORA]
- **Horário de Término**: [DEFINIR HORA]
- **Formato**: ATIVIDADE
- **Tags SRE**: Release de Produto, Confiabilidade, Estratégia de Release, Resposta a Incidentes
- **Nível na Hierarquia SRE**: Produto
- **Descrição**: Nesta sessão, os participantes serão preparados para um release de produto e terão que garantir que o release seja realizado com sucesso e sem interrupções, mantendo padrões de confiabilidade e experiência do usuário.

##### 8.1 ATIVIDADE
- **Desafio**: Garantir um lançamento de produto confiável em grande escala.
- **Passo-a-Passo**:
  1. Os participantes formarão equipes e criarão uma apresentação simulada de "release de produto" para um produto imaginário.
  2. Após a apresentação, outras equipes introduzirão "incidentes" (por exemplo, uma falha de energia), e a equipe apresentadora deverá adaptar sua estratégia de release em tempo real.
  3. Cada equipe apresentará um caso e deverá introduzir princípios de confiabilidade em sua estratégia.

