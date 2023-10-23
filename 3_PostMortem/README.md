# 3. Análise Pós-Incidente, Postmortem, RCA

No universo da Engenharia de Confiabilidade (SRE), compreender e aprender com incidentes é vital. Quando sistemas complexos falham, as equipes precisam não apenas resolver o problema, mas também entender suas causas subjacentes e implementar medidas preventivas. A análise pós-incidente, também conhecida como postmortem ou RCA (Root Cause Analysis), é o processo pelo qual as organizações analisam incidentes, identificam causas raiz e planejam ações corretivas. Esta abordagem sistemática e reflexiva é fundamental para melhorar a resiliência e confiabilidade dos sistemas ao longo do tempo.

## 3.1 A Fundamentação da Análise Pós-Incidente em Engenharia de Confiabilidade (SRE)
Analisar incidentes pós-ocorrência é uma prática essencial em SRE. Esta análise, frequentemente referida como postmortem ou RCA (Root Cause Analysis), tem objetivos claros:

- **Aprender com erros**: Aprender com cada incidente, entendendo suas causas raiz e implementando ações corretivas.
- **Fomentar a cultura de transparência e sem culpa**: Incidentes são tratados abertamente, focando em melhorias sistêmicas em vez de alocar culpa.
- **Identificar e Implementar Melhorias**: Refinar sistemas e processos com base nas lições aprendidas, prevenindo incidentes recorrentes.
- **Compartilhar Aprendizado**: Documentar e compartilhar insights de cada incidente para fortalecer toda a organização.

### Conceitos Chave
- **Postmortem**: Uma análise detalhada após um incidente, incluindo a descrição, causas raiz, ações tomadas e medidas preventivas.
- **Cultura sem Culpa**: Ambiente onde erros são vistos como oportunidades de aprendizado e melhoria, e não como falhas individuais.
- **Ações Corretivas**: Medidas implementadas após um incidente para evitar sua repetição.

### O Processo de Postmortem na Prática
O processo de postmortem é altamente colaborativo, envolvendo:

1. **Resumo do Incidente**: Uma visão geral do incidente, seu impacto e ações tomadas.
2. **Cronologia Detalhada**: Uma linha do tempo dos eventos, desde a detecção até a resolução.
3. **Análise da Causa Raiz**: Uma investigação profunda das causas que levaram ao incidente.
4. **Ações Corretivas**: Medidas propostas para evitar a repetição do incidente no futuro.
5. **Lições Aprendidas**: Reflexões sobre o que funcionou e o que pode ser melhorado.

### Cultura Blameless: Foco em Melhoria, Não em Culpa
A abordagem blameless, ou "sem culpa", é uma característica definidora dos postmortems no Google. Essa cultura:

- **Promove Aprendizado**: Erros são vistos como oportunidades para fortalecer o sistema, não como falhas individuais.
- **Encoraja a Colaboração**: Em um ambiente sem culpa, as equipes são mais abertas e honestas sobre incidentes, promovendo uma melhor colaboração e aprendizado.
- **Leva a Ações Mais Eficazes**: Identificando causas sistêmicas em vez de focar em erros individuais, as equipes podem implementar mudanças mais eficazes.

### Quando e Por Que Fazer Postmortems?
Postmortems são essenciais para garantir que a organização aprenda com cada incidente e melhore continuamente. O Google, por exemplo, vê postmortems como uma oportunidade não apenas para identificar e corrigir a causa imediata de um incidente, mas para tornar todo o sistema mais robusto e resiliente. Eles são conduzidos após:

- Quedas ou degradações visíveis ao usuário além de um limite definido.
- Qualquer perda de dados.
- Intervenção do engenheiro de plantão, como rollback de um lançamento.
- Tempo de resolução acima de um limite definido.
- Falhas de monitoramento.

É importante ter critérios claramente definidos para quando um postmortem é necessário, e qualquer interessado pode solicitar um postmortem após um evento.

### Colaboração e Compartilhamento: Melhorando Juntos
O processo de postmortem é colaborativo por natureza. As equipes se unem para entender o incidente, compartilhar perspectivas e garantir que todas as áreas sejam consideradas. Compartilhar as descobertas de um postmortem fortalece toda a organização, pois permite que outras equipes aprendam com o incidente e evitem erros semelhantes.

### Conclusão e Melhorias Contínuas
A prática de postmortem, quando conduzida de maneira eficaz e em uma cultura sem culpa, leva a uma melhoria contínua. No Google, a prática de postmortem ajudou a empresa a reduzir significativamente o número de interrupções e melhorar a experiência do usuário. Através de ferramentas e práticas eficazes, a análise pós-incidente se torna uma parte valiosa da cultura de engenharia, garantindo que os erros sejam aprendidos e não repetidos.

##### 3.2 Plataforma e Ferramentas
O Postmortem é uma abordagem crítica em SRE para entender, aprender e melhorar após um incidente. O OpenShift, uma plataforma de gerenciamento de contêineres baseada em Kubernetes, fornece ferramentas valiosas para facilitar essa análise. Esta seção fornecerá um guia passo a passo sobre como usar o OpenShift para realizar uma análise pós-incidente.

### Análise de Incidentes com OpenShift

Ao lidar com incidentes, é vital ter ferramentas eficazes para analisar e corrigir rapidamente o problema. O OpenShift, juntamente com suas ferramentas integradas, proporciona uma excelente base para tal análise. Aqui, descrevemos os recursos e ferramentas disponíveis para realizar uma análise pós-incidente com o OpenShift:

- **OpenShift Logs & EFK**:
  - **Descrição**: OpenShift oferece um stack EFK (Elasticsearch, Fluentd, Kibana) para lidar com logs, permitindo coletar, armazenar e visualizar logs de aplicações e sistemas.
  - **Uso Prático**: Durante o postmortem, os logs da aplicação `mobility-app` podem ser recuperados e analisados para entender o incidente simulado.

- **ConfigMaps & Secrets**:
  - **Descrição**: `ConfigMaps` e `Secrets` permitem gerenciar configurações de forma modular e segura no OpenShift.
  - **Uso Prático**: Em caso de uma configuração problemática que causou um incidente, é possível reverter ou recuperar uma versão anterior usando essas ferramentas.

- **Jaeger & Tracing**:
  - **Descrição**: `Jaeger` fornece tracing distribuído para aplicações, ajudando a identificar falhas em microserviços interconectados.
  - **Uso Prático**: Durante o postmortem, o Jaeger pode ser usado para identificar pontos problemáticos em chamadas entre microserviços.

- **Desafio**: Utilizar o OpenShift para acessar e analisar dados do incidente.
- **Passo-a-Passo**:
  1. **Introdução ao OpenShift & EFK**:
     - Visão geral dos recursos do OpenShift relacionados ao acesso e análise de logs.
     - Como usar o stack EFK para acessar e visualizar logs da aplicação `mobility-app`.
  2. **Análise de Logs & Identificação de Causas Raiz**:
     - Como os logs podem ajudar a identificar a causa do incidente.
     - Discussão sobre padrões, erros repetidos e outros insights que podem ser obtidos a partir dos logs.
  3. **Recuperação & Reversão de Configurações**:
     - Demonstração de como usar `ConfigMaps` e `Secrets` para recuperar ou reverter configurações.
  4. **Tracing com Jaeger**:
     - Introdução ao Jaeger e como ele ajuda na identificação de falhas.
     - Demonstração de como usar o Jaeger para rastrear chamadas entre microserviços e identificar falhas.

Ao final desta seção, os participantes terão uma compreensão clara de como usar o OpenShift e suas ferramentas associadas para conduzir análises pós-incidente eficazes.

## RECAP
### Importância da Análise Pós-Incidente
Após qualquer incidente significativo, a análise é crucial para entender os eventos, as causas subjacentes e as lições aprendidas. Esta análise não é sobre atribuição de culpa, mas sim sobre aprender e melhorar.

### Conceitos-Chave
Entendendo os principais termos:
- **Postmortem**: Um relato detalhado de um incidente.
- **Cultura sem Culpa**: Uma mentalidade focada na melhoria, não na culpa.
- **Ações Corretivas**: Medidas para evitar futuras recorrências.

### Blameless Postmortems
Postmortems sem culpa são essenciais para a cultura SRE. Ao entender como um erro ocorreu, em vez de quem cometeu o erro, criamos um ambiente de aprendizado contínuo, transparência e comunicação aberta.

### Quando Realizar um Postmortem
Cada incidente, independentemente de sua gravidade percebida, é uma oportunidade de aprendizado. A prática de conduzir postmortems após incidentes significativos garante uma resposta sistemática e uma melhoria contínua.

### Responsabilidade pelo Postmortem
A responsabilidade por um postmortem é colaborativa. Um indivíduo pode liderar o esforço, mas a análise e a escrita envolvem todas as partes interessadas, garantindo uma perspectiva completa e multifacetada do incidente.

### Conclusão e Melhoria Contínua
Os postmortems não são apenas uma atividade de reflexão, mas uma ferramenta para impulsionar a melhoria contínua. Ao aprender com os incidentes, fortalecemos nossos sistemas e processos, tornando nossa organização mais resiliente a longo prazo.
