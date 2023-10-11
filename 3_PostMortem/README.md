## 3.1 A Fundamentação da Análise Pós-Incidente em Engenharia de Confiabilidade (SRE)
O postmortem é uma ferramenta central na Engenharia de Confiabilidade (SRE), permitindo:
- **Aprender com erros**: Cada incidente oferece uma oportunidade única de aprendizado. Compreender o que deu errado e por quê é o primeiro passo para a prevenção.
- **Fomentar a cultura de transparência**: Abordar incidentes abertamente e sem culpar promove a confiança e incentiva a comunicação franca e transparente.
- **Melhorar sistemas e processos**: Ao identificar falhas e áreas de melhoria, podemos fortalecer continuamente nossos sistemas e processos.
- **Prevenir reincidências**: Ao agir sobre as descobertas de um postmortem, reduzimos a probabilidade de recorrência de incidentes semelhantes.

### Conceitos Chave
- **Postmortem**: Um registro detalhado de um incidente, abordando seu impacto, ações tomadas, causas raiz e medidas preventivas.
- **Cultura sem Culpa**: Uma abordagem que se concentra em identificar causas sistêmicas em vez de culpar indivíduos. Promove a aprendizagem e a melhoria contínua.
- **Ações Corretivas**: Medidas implementadas para evitar a recorrência de um incidente.

### Postmortem na Prática
A condução eficaz de um postmortem não é apenas sobre documentar o que aconteceu. Trata-se de uma investigação profunda, colaborativa e construtiva sobre o incidente. Envolve a identificação de causas raiz, o entendimento de fatores contribuintes e a formulação de ações claras e eficazes para prevenir reincidências.

### Importância da Colaboração e Compartilhamento
O processo de postmortem é altamente colaborativo. Através da colaboração, equipes podem unir perspectivas, compartilhar conhecimentos e garantir que todos os aspectos do incidente sejam abordados. Além disso, compartilhar amplamente as descobertas e aprendizados de um postmortem fortalece toda a organização, ajudando a evitar incidentes similares em diferentes partes do sistema.

##### 3.2 Abordagem Prática da Análise Pós-Incidente
A análise pós-incidente é essencial para entender os desafios enfrentados e para prevenir futuras ocorrências. Através de um exercício prático, os participantes terão a oportunidade de aplicar os conceitos aprendidos e desenvolver habilidades valiosas para lidar com incidentes reais.

- **Desafio**: Em um ambiente de simulação, os participantes serão desafiados a conduzir uma análise completa pós-incidente, abordando todas as fases desde a identificação até a implementação de medidas corretivas.
- **Passo-a-Passo**:
  1. **Apresentação do Cenário**: Uma simulação detalhada de um incidente, como uma falha de segurança ou uma situação de emergência, é apresentada aos participantes. Eles receberão informações sobre o que foi observado, os sistemas ou áreas afetadas e o impacto inicial.
  2. **Coleta de Dados**: Os participantes coletam informações relevantes sobre o incidente a partir dos detalhes fornecidos. Esta fase envolve a análise de informações, como registros de eventos, testemunhos e quaisquer outros dados disponíveis.
  3. **Identificação de Causas Raiz**: Com as informações coletadas, as equipes trabalham juntas para identificar as causas subjacentes do incidente. Isso envolve a análise dos eventos que levaram ao incidente e a identificação de falhas ou vulnerabilidades que possam ter contribuído para a ocorrência.
  4. **Elaboração de Recomendações**: Após identificar as causas raiz, os participantes formulam recomendações para evitar a recorrência do incidente. Isso pode envolver mudanças nos processos, implementação de novas medidas de segurança ou treinamento adicional para a equipe.
  5. **Apresentação das Descobertas**: Cada equipe apresenta suas descobertas, detalhando o que ocorreu, por que ocorreu e o que sugerem para prevenir incidentes futuros. Este é um momento de compartilhamento e aprendizado mútuo.

Através desta atividade prática, os participantes terão uma compreensão mais aprofundada da importância da análise pós-incidente e estarão melhor preparados para lidar com situações reais em seus ambientes de trabalho.

##### 3.3 Plataforma e Ferramentas
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

##### 3.4 Abordagem Prática: Jogo de Simulação de Desastres (Opcional)
Ao lidar com sistemas complexos e cenários de incidentes potenciais, a prática e a preparação são fundamentais. Nesta abordagem prática, os participantes serão submetidos a um exercício interativo de simulação de desastres, projetado para testar e aprimorar suas habilidades de resposta a incidentes em um ambiente controlado.

## 3.4.1 Desafio:
Conduzir uma análise pós-incidente após um incidente simulado. 

## 3.4.2 Passo-a-Passo:
1. **Apresentação do Cenário**: O facilitador apresentará um cenário de incidente simulado, como uma falha crítica no sistema ou uma violação de segurança. Esse cenário será baseado em situações reais ou hipotéticas relevantes para o contexto da equipe.
2. **Responder ao Incidente**: Os participantes, agindo como a equipe de resposta, começarão a abordar o incidente. Eles devem comunicar suas ações, fazer perguntas e tomar decisões sobre como investigar, mitigar e, eventualmente, resolver o incidente.
3. **Revisão e Análise**: Uma vez que o incidente simulado seja "resolvido", o grupo discutirá as ações tomadas, identificando pontos fortes, áreas de melhoria e lições aprendidas.
4. **Elaboração de Recomendações**: Os participantes colaborarão para elaborar recomendações baseadas em sua resposta ao incidente simulado. Isso pode incluir mudanças em procedimentos, melhorias em sistemas ou ferramentas, ou áreas de treinamento adicional.
5. **Conclusão**: Concluir a atividade com um resumo das principais descobertas, lições aprendidas e próximos passos. 

## 3.4.3 Objetivos da Abordagem Prática:
- **Melhorar a Preparação**: Através da simulação, os participantes podem praticar suas habilidades de resposta a incidentes em um ambiente seguro, preparando-se melhor para incidentes reais.
- **Promover o Trabalho em Equipe**: Ao trabalhar juntos em um cenário desafiador, os participantes fortalecem sua coesão e habilidades de colaboração.
- **Identificar Áreas de Melhoria**: A simulação ajuda a identificar lacunas em conhecimento, ferramentas ou procedimentos, proporcionando oportunidades claras para melhorias.
- **Reforçar a Cultura de Resposta a Incidentes**: Ao participar regularmente de simulações, os participantes internalizam a importância de uma resposta rápida e eficaz a incidentes, reforçando a cultura de prontidão.

Ao integrar esta abordagem prática em seu treinamento ou atividades regulares, as equipes estarão mais bem preparadas para responder eficazmente a incidentes reais, minimizando impactos e promovendo a resiliência do sistema.

# 3. Postmortem: Utilizando OpenShift para Análise de Incidentes

