## 🎯 5. Elevando os 9s da Disponibilidade: Guia da Atividade

> 1. **Melhoria dos 9s de Disponibilidade**: As equipes são desafiadas a avaliar e melhorar a disponibilidade dos componentes críticos de um prédio após um incidente simulado.
> 2. **Avaliação e Classificação**: As equipes começam avaliando a infraestrutura atual, identificando os componentes críticos e seus níveis de disponibilidade. Em seguida, elas classificam cada componente com base nos 9s de disponibilidade desejados.
> 3. **Propostas e Testes**: Com as classificações em mente, as equipes propõem melhorias para aumentar a disponibilidade e, em seguida, desenvolvem testes para validar a eficácia dessas melhorias.
> 4. **Objetivo Principal**: Utilizar práticas de Engenharia de Confiabilidade (SRE) para elevar os níveis de disponibilidade em um ambiente simulado, culminando em um plano de ação claro visualizado no quadro.


### 🚨 Desafio
Com base nos incidentes anteriores e nas características do prédio, identifique melhorias na infraestrutura que podem aumentar os 9s de disponibilidade do SLA durante uma ocorrência como as precedentes.

### Componentes Críticos:

1. **Elevadores**: Equipamentos vitais para transporte vertical, facilitando o acesso e a evacuação dos andares.
    - Disponibilidade Atual: 99.9% (3 Noves)
2. **Sprinklers (Sistema de Aspersão de Água)**: Atuam automaticamente na presença de fogo, dispersando água para conter ou retardar as chamas.
    - Disponibilidade Atual: 99.9% (3 Noves)
3. **Sistemas de Controle de Acesso**: Englobam catracas, portas automáticas, leitores biométricos e outros dispositivos que controlam o acesso a áreas restritas.
    - Disponibilidade Atual: 99.99% (4 Noves)
4. **Sistemas de Alarme e Detecção de Fumaça**: Sensores e dispositivos que alertam sobre a presença de fumaça ou fogo, garantindo tempo para evacuação.
    - Disponibilidade Atual: 99% (2 Noves)
5. **Sistema de Iluminação de Emergência**: Luzes de emergência que são ativadas automaticamente em situações adversas, garantindo a visibilidade nos corredores e saídas.
    - Disponibilidade Atual: 90% (1 Nove)
### 📋 Instruções

1. **🏢 Avalie a Infraestrutura Atual**:
    - Relembre os incidentes anteriores e identifique áreas críticas que precisam de melhorias.
    - Use post-its para listar os componentes críticos e coloque-os no quadro.

2. **📊 Classifique por 9s de Disponibilidade**:
    - Classifique cada componente crítico em termos de 9s de disponibilidade necessários.
    - **ATENÇÃO! A EQUIPE SÓ POSSUI UM MÁXIMO DE 15 NOVES PARA DISTRIBUIR!**
    - Use post-its para listar os níveis de disponibilidade e associe-os a cada componente no quadro.

3. **💡 Proponha Melhorias**:
    - Liste melhorias que podem aumentar a disponibilidade da infraestrutura.
    - Use post-its para cada melhoria proposta e coloque-as no quadro.
    - Considere aspectos como redundância, escalabilidade e pontos de falha.

4. **🔄 Automatize e Reduza Toil**:
    - Identifique tarefas que podem ser automatizadas para melhorar a eficiência.
    - Use post-its para listar tarefas automatizadas e coloque-as no quadro.

5. **🧪 Realize Testes de Confiabilidade**:
    - Com as melhorias propostas em mente, é essencial testá-las para validar sua eficácia.
    - Desenvolva cenários de teste que simulem falhas, picos de tráfego e outros eventos adversos.
    - **Exemplo de Teste**:
        - **Cenário**: Simule uma falha de energia no prédio.
        - **Objetivo**: Verificar se o Sistema de Iluminação de Emergência é ativado imediatamente e se mantém operacional durante o período desejado.
        - **Resultado Esperado**: O Sistema de Iluminação de Emergência deve atender ao nível de disponibilidade definido após as melhorias.
    - Use post-its para listar os cenários de teste, os objetivos, os resultados esperados e os resultados reais, e coloque-os no quadro.

---

## Exemplos de 9s de Disponibilidade

- **90% (1 Nove)**: Permite 36 dias, 12 horas e 43 minutos de tempo de inatividade por ano.
- **99% (2 Nove)**: Permite 3 dias, 15 horas e 39 minutos de tempo de inatividade por ano.
- **99.9% (3 Nove)**: Permite 8 horas, 45 minutos e 57 segundos de tempo de inatividade por ano.
- **99.99% (4 Nove)**: Permite 52 minutos e 35,7 segundos de tempo de inatividade por ano.
- **99.999% (5 Nove)**: Permite 5 minutos e 15,6 segundos de tempo de inatividade por ano.
