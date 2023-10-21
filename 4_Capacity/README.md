#### 4. "Automação, Gestão de Capacidade e Otimização de Evacuação"
A Engenharia de Confiabilidade (SRE) representa uma abordagem transformadora para a gestão de sistemas em grande escala. Ela não apenas otimiza a operação, mas também redefine como vemos a confiabilidade, a performance e a entrega de sistemas.

## 4.1 A Fundamentação da Automação em Engenharia de Confiabilidade (SRE)
A automação é um elemento central na Engenharia de Confiabilidade (SRE), permitindo:
- **Consistência**: A automação garante que ações repetidas sejam executadas da mesma forma, evitando erros humanos e melhorando a confiabilidade.
- **Plataforma Extensível**: Sistemas automatizados podem ser estendidos para acomodar novas funções e adaptar-se a diferentes sistemas, tornando-os mais versáteis.
- **Reparos Mais Rápidos**: A capacidade de detectar e corrigir problemas de forma automática reduz significativamente o tempo de inatividade.
- **Economia de Tempo**: Libera engenheiros e operadores para se concentrarem em tarefas mais estratégicas e inovadoras.

### Conceitos Chave
- **Automação Precisa**: Implementar automação de forma pensada, garantindo que ela resolva problemas reais e não crie novos desafios.
- **Sistemas Autônomos**: A meta final da automação, onde os sistemas são projetados para operar com mínima intervenção humana.
- **Consistência**: A garantia de que as ações são executadas da mesma forma todas as vezes, melhorando a confiabilidade e a previsibilidade.
- **Gestão de Capacidade**: Monitorar e garantir que os sistemas tenham os recursos necessários para atender à demanda, equilibrando a eficiência e a disponibilidade.
- **9s de Disponibilidade**: Um padrão para medir a disponibilidade de um sistema. Quanto mais 9s, mais disponível é o sistema.

### Automação na Prática
A automação não é apenas sobre escrever scripts ou usar ferramentas. É sobre compreender profundamente os processos, identificar áreas de melhoria e implementar soluções que tornem os sistemas mais eficientes, confiáveis e autônomos.

### A Importância da Medição e Monitoramento
Assim como a análise pós-incidente, a automação também requer uma abordagem metódica. É crucial medir e monitorar a eficácia da automação, garantir que ela atenda às expectativas e fazer ajustes conforme necessário. Isso garante que a automação continue relevante e eficaz à medida que os sistemas e os requisitos evoluem.

### A Força da Automação em SRE

A automação é considerada um multiplicador de força em SRE, mas não é uma panaceia por si só. A automação sem reflexão pode criar tantos problemas quanto resolve. O verdadeiro valor da automação vem da consistência que ela traz. Uma ação realizada manualmente centenas de vezes terá variações, enquanto uma máquina pode realizar a mesma ação com precisão todas as vezes. Esta consistência evita erros, problemas de qualidade de dados e problemas de confiabilidade.

Adicionalmente, a automação não se limita à consistência. Bem projetados, os sistemas automáticos também oferecem uma plataforma extensível, centralizando erros, permitindo correções rápidas, e proporcionando uma operação contínua. Uma plataforma automatizada pode exportar métricas, proporcionando insights valiosos sobre processos e desempenho.

### Disponibilidade

A disponibilidade é uma métrica fundamental em SRE. Representa a proporção de tempo que um sistema está operacional e acessível. Para garantir que os sistemas atendam aos padrões de disponibilidade, é vital medir e monitorar essa métrica regularmente, correlacionando-a com a percepção do usuário e os objetivos de negócios.

A seguir, uma tabela demonstrando os níveis de disponibilidade em termos de "9s" e o tempo de indisponibilidade associado:

| Nível de Disponibilidade | Indisponibilidade por ano | Indisponibilidade por mês | Indisponibilidade por dia |
|--------------------------|---------------------------|---------------------------|---------------------------|
| 90% (um 9)               | 36,5 dias                 | 3 dias                    | 2,4 horas                 |
| 99% (dois 9s)            | 3,65 dias                 | 7,2 horas                 | 14,4 minutos              |
| 99,9% (três 9s)          | 8,76 horas                | 43,2 minutos              | 1,44 minutos              |
| 99,99% (quatro 9s)       | 52,6 minutos              | 4,32 minutos              | 8,64 segundos             |
| 99,999% (cinco 9s)       | 5,26 minutos              | 25,9 segundos             | 0,87 segundos             |

Estes números demonstram como cada aumento no nível de disponibilidade exige uma redução significativa no tempo de inatividade permitido. A escolha do nível de disponibilidade alvo depende do serviço específico, das expectativas do usuário e dos objetivos de negócios.

##### 4.2 Abordagem Prática da Automação em SRE
A prática da automação em SRE é essencial para garantir sistemas escaláveis e confiáveis. Através de um exercício prático, os participantes terão a oportunidade de experimentar a implementação da automação, entender seus desafios e benefícios e desenvolver habilidades práticas em automação.

#### ATIVIDADE - Automação no Complexo SkyTower
- **Desafio**: No ambiente simulado do "Complexo SkyTower", os participantes serão desafiados a identificar processos que podem ser automatizados, projetar e implementar soluções de automação.
- **Passo-a-Passo**:
  1. **Identificação de Processos**: Comece identificando tarefas repetitivas ou processos que são candidatos à automação dentro do Complexo SkyTower.
  2. **Projeto da Solução**: Com os processos em mãos, os participantes projetarão uma solução de automação, considerando as ferramentas disponíveis e as necessidades específicas do complexo.
  3. **Implementação**: Com um projeto definido, os participantes implementarão sua solução, testando-a em um ambiente controlado do Complexo SkyTower.
  4. **Medição e Feedback**: Após a implementação, avalie a eficácia da solução, colete feedback e faça ajustes conforme necessário.
  5. **Apresentação das Soluções**: Cada grupo compartilhará sua abordagem, discutindo os desafios enfrentados, as soluções implementadas e as lições aprendidas.

#### ATIVIDADE - Definindo 9S de Disponibilidade no Complexo SkyTower
- **Desafio**: Ainda dentro do cenário do "Complexo SkyTower", os participantes agora terão o desafio de definir os 9S de disponibilidade para o sistema de segurança e elevadores, considerando um orçamento específico e a importância destes sistemas para o funcionamento do complexo.
- **Passo-a-Passo**:
  1. **Contextualização do Complexo SkyTower**:
     - Entenda o contexto e a importância dos sistemas de segurança e elevadores dentro do Complexo SkyTower.
  2. **Introdução aos 9S de Disponibilidade**:
     - Aprenda sobre o que significa cada 'nove' em termos de tempo de inatividade por ano, mês, semana e dia.
     - Discuta a importância de atingir altos níveis de disponibilidade, especialmente em sistemas críticos como os do SkyTower.

##### 4.3 Plataforma e Ferramentas

A Engenharia de Confiabilidade de Site (SRE) é potencializada pelo uso adequado de plataformas e ferramentas. Elas permitem a automação, observabilidade e escalabilidade. No contexto do "firefighters SRE", vamos explorar a implementação de práticas SRE usando Kubernetes, uma plataforma de orquestração de contêineres, e OpenShift, uma plataforma Kubernetes empresarial.

### Testes Unitários com Quarkus
Além dos testes unitários padrão, um dos testes a ser observado é o `testAccess` no arquivo [`AccessLogResourceTest.java`](
https://github.com/firefighters-sre/concierge-app/blob/main/src/test/java/com/redhat/quarkus/resources/AccessLogResourceTest.java). Vamos detalhar este teste:
##### testAccess: Verificando a Integração com Kafka
Este teste valida a capacidade do serviço `concierge-app` de enviar registros de acesso ao tópico Kafka `entrance` e, em seguida, consumir esses registros para verificação.

1. **Inicialização e Subscrição ao Tópico Kafka**:
    ```java
    logConsumer.subscribe(Collections.singleton("entrance"));
    ```
   O teste começa se inscrevendo no tópico Kafka `entrance` para ouvir as mensagens que serão produzidas.

2. **Preparação dos Dados**:
    ```java
    AccessLog logToSend = new AccessLog(1L, "1");
    ```
   Um novo objeto `AccessLog` é criado para simular um registro de acesso que será enviado ao tópico Kafka.

3. **Chamada ao Endpoint e Envio de Dados**:
    ```java
    given()
      .when()
      .contentType(ContentType.JSON)
      .body(logToSend)
      .post("/access")
      .then()
      .statusCode(204);
    ```
   Aqui, o endpoint `/access` é chamado com o objeto `AccessLog` preparado. A resposta esperada é um HTTP 204, indicando sucesso sem retorno.

4. **Consumo e Verificação dos Dados**:
    ```java
    ConsumerRecords<String, MoveLog> records = logConsumer.poll(Duration.ofMillis(10000));
    MoveLog receivedLog = records.records("entrance").iterator().next().value();
    ```
   O teste aguarda até 10 segundos para consumir a mensagem do tópico `entrance`. Uma vez consumida, ele extrai o valor da mensagem como um objeto `MoveLog`.

5. **Validação**:
    ```java
    assertEquals(logToSend.getPersonId(), receivedLog.getPersonId());
    assertEquals(logToSend.getDestination(), receivedLog.getDestination());
    assertEquals("elevator", receivedLog.getPreferredRoute());
    ```
   Finalmente, o teste valida se os dados consumidos do tópico Kafka correspondem aos dados enviados originalmente, verificando o ID da pessoa, o destino e a rota preferida.

Este teste garante que o serviço `concierge-app` esteja corretamente integrado com o Kafka, sendo capaz de produzir e consumir mensagens conforme esperado.

#### ATIVIDADE - Implementando Probes em Kubernetes no Sistema "firefighters SRE"
- **Desafio**: Usando o ambiente OpenShift, os participantes aprenderão a automatizar exercícios de segurança e otimizar rotas de evacuação.
- **Passo-a-Passo**:
  1. **Introdução a Readiness e Liveness Probes**: 
     - Estas são ferramentas integradas em Kubernetes para verificar a saúde de um contêiner. 
     - O `readinessProbe` verifica se o contêiner está pronto para receber solicitações. 
     - O `livenessProbe` verifica se o contêiner está funcionando conforme o esperado durante sua execução.
     - Eles são essenciais para garantir que apenas contêineres saudáveis recebam tráfego e que os contêineres problemáticos sejam reiniciados.
  2. **Implementação de Probes**: 
     - Utilizando o ambiente OpenShift, os participantes serão guiados para adicionar `Readiness` e `Liveness probes` ao `mobility-app`.
      ```yaml
            readinessProbe:
            httpGet:
               path: /q/health/ready
               port: 8080
               scheme: HTTP
            livenessProbe:
            httpGet:
               path: /q/health/live
               port: 8080
               scheme: HTTP
      ```
  3. **Simulação de Falhas no `mobility-app` / Alteração do Endpoint do Liveness Probe**:
      - Modifique o endpoint que o livenessProbe verifica. Se, por exemplo, o livenessProbe verifica /q/health/live, os participantes devem alterar a rota no aplicativo para um endpoint que não exista ou esteja retornando erros. Isso força o probe a falhar e os participantes podem observar como o sistema reage a essa falha.
  4. **Validação e Observação**:
     - Com as probes implementadas, os participantes observarão como o Kubernetes reage quando detecta falhas, garantindo que o tráfego seja encaminhado apenas para pods saudáveis.