# 4. Testes

Os Engenheiros de Confiabilidade de Site (SREs) têm a vital tarefa de quantificar a confiabilidade dos sistemas sob sua gestão. Testes são essenciais nessa missão.

## 4.1 Testes em SRE: Uma Pedra Angular da Confiabilidade

Cada teste que passa antes e depois de uma mudança no sistema reduz incertezas. Testes meticulosos antecipam a confiabilidade futura de um site, guiando equipes por caminhos seguros.

### Tipos de Testes de Software

Os testes variam desde os tradicionais, realizados offline, até os de produção, feitos em sistemas ao vivo.

#### Testes Tradicionais

- **Testes Unitários**: Avaliam pequenas unidades de software, como classes ou funções.
- **Testes de Integração**: Confirmam a funcionalidade de componentes integrados.
- **Testes de Sistema**: Avaliam a funcionalidade global do sistema.
  - **Smoke Tests**: Testes rápidos que verificam o comportamento crítico básico do sistema.
  - **Performance Tests**: Verificam se o desempenho do sistema se mantém aceitável ao longo de seu ciclo de vida.
  - **Regression Tests**: Evitam que bugs antigos retornem ao código, garantindo que erros passados não se repitam.

#### Testes de Produção

Estes garantem que um sistema ao vivo esteja funcionando conforme o esperado, sendo cruciais para a confiabilidade do serviço.

- **Rollouts Entangle Tests**: Estes testes lidam com as complexidades de mudanças em produção, considerando que os lançamentos podem não ser herméticos e podem ocorrer em etapas.
- **Configuration Test**: Estes testes examinam a produção em relação à configuração atual, identificando discrepâncias.
- **Stress Test**: Determina os limites de um sistema, identificando como os componentes reagem sob estresse.
- **Canary Test**: Uma parte dos servidores é atualizada para uma nova versão ou configuração. Se tudo correr bem, o restante é atualizado. Esta técnica "baking the binary" minimiza riscos.

### Relação entre Testes e MTTR

Testes que falham geralmente sinalizam falta de confiabilidade. O Tempo Médio para Reparo (MTTR) reflete a rapidez com que um bug é corrigido após ser identificado.

##### 4.2 Plataforma e Ferramentas

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
