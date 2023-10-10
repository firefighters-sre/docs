# 2. Monitoramento, SLIs, SLOs, SLAs
## 2.1 A Fundamentação do Monitoramento em Engenharia de Confiabilidade (SRE)
No universo da Engenharia de Confiabilidade (SRE), o monitoramento é um pilar fundamental. Ele permite que as equipes de engenharia mantenham um pulso constante na saúde e no desempenho de seus sistemas, garantindo que os serviços atendam às expectativas definidas em termos de confiabilidade e disponibilidade. O monitoramento eficaz é vital para identificar rapidamente problemas potenciais e agir antes que esses problemas afetem adversamente os usuários ou a integridade do sistema.

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
Especificamente, vamos focar na métrica `processLobbyPostTime` e `processLobbyEventTime` definidas nas classes [`AccessLogResource`](https://github.com/firefighters-sre/concierge-app/blob/main/src/main/java/com/redhat/quarkus/resources/AccessLogResource.java) e [`AccessLogService`](https://github.com/firefighters-sre/concierge-app/blob/main/src/main/java/com/redhat/quarkus/services/AccessLogService.java), respectivamente.
   1. 
    ```java
    @Timed(name = "processLobbyPostTime", description = "Time taken to process a lobby POST call.", unit = MetricUnits.MILLISECONDS)
    ```
    ```java
    @Timed(name = "processLobbyEventTime", description = "Time taken to process a lobby event.", unit = MetricUnits.MILLISECONDS)
    ```
   A anotação `@Timed` define a métrica, especificando seu nome, descrição e unidade de medida. Ela informa ao Quarkus para coletar dados sobre o tempo que leva para executar o método anotado.

2. **Coleta de Dados**:
   Sempre que os métodos anotados são chamados, Quarkus coleta os dados de tempo de execução e os expõe no endpoint `/q/metrics`.

3. **Integração com OpenShift**:
   Quando o serviço `concierge-app` é implantado no OpenShift, o `PodMonitor` e `ServiceMonitor` detecta automaticamente os endpoints de métricas expostos e os integra com o sistema de monitoramento Prometheus. Isso permite que os operadores vejam as métricas em tempo real no painel do OpenShift.

4. **Visualização e Alertas**:
   `Dashboar Grafana` `Prometheus Rules`
   Com as métricas sendo coletadas pelo Prometheus, os operadores podem definir alertas com base em limites específicos ou anormalidades detectadas. Além disso, as métricas podem ser visualizadas em dashboards para uma análise mais detalhada.

5. **Importância**:
   Monitorar o tempo de processamento dos eventos do lobby é crucial para garantir que o serviço esteja respondendo de maneira eficiente. Qualquer atraso ou inconsistência pode ser rapidamente identificado e resolvido antes de se tornar um problema maior.

[`AccessLogResourceTest.java`](
https://github.com/firefighters-sre/concierge-app/blob/main/src/test/java/com/redhat/quarkus/resources/AccessLogResourceTest.java). Vamos detalhar este teste:ópico Kafka `entrance` para ouvir as mensagens que serão produzidas.


<dependency>
        <groupId>org.eclipse.microprofile.metrics</groupId>
        <artifactId>microprofile-metrics-api</artifactId>
      </dependency>
      <dependency>
        <groupId>io.quarkus</groupId>
        <artifactId>quarkus-smallrye-openapi</artifactId>
      </dependency>
      <dependency>
        <groupId>io.quarkus</groupId>
        <artifactId>quarkus-micrometer</artifactId>
      </dependency>
      <dependency>
        <groupId>io.quarkus</groupId>
        <artifactId>quarkus-micrometer-registry-prometheus</artifactId>
      </dependency> 
      <dependency>
        <groupId>io.quarkus</groupId>
        <artifactId>quarkus-smallrye-health</artifactId>
      </dependency>