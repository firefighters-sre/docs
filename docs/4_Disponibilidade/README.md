# 4. 9s de Disponibilidade: Medindo a Confiabilidade em SRE

A Engenharia de Confiabilidade (SRE) vai além da simples manutenção de sistemas; ela redefine a maneira como percebemos e alcançamos a confiabilidade. Um dos indicadores mais reconhecidos de confiabilidade é a medida dos "9s" de disponibilidade.

## 4.1 Entendendo os 9s de Disponibilidade

O termo "9s" refere-se à porcentagem de tempo que um sistema está operacional e acessível. É uma métrica que quantifica a confiabilidade de um sistema.

### Conceitos Chave
- **Disponibilidade**: A proporção de tempo que um sistema está funcional e acessível.
- **Downtime**: O tempo durante o qual um sistema não está disponível para os usuários.
- **9s de Disponibilidade**: Uma representação percentual da disponibilidade. Quanto mais "9s", mais confiável é o sistema.

### Os Níveis de 9s e Sua Significância

| Nível de Disponibilidade | Indisponibilidade por ano | Indisponibilidade por mês | Indisponibilidade por dia |
|--------------------------|---------------------------|---------------------------|---------------------------|
| 90% (um 9)               | 36,5 dias                 | 3 dias                    | 2,4 horas                 |
| 99% (dois 9s)            | 3,65 dias                 | 7,2 horas                 | 14,4 minutos              |
| 99,9% (três 9s)          | 8,76 horas                | 43,2 minutos              | 1,44 minutos              |
| 99,99% (quatro 9s)       | 52,6 minutos              | 4,32 minutos              | 8,64 segundos             |
| 99,999% (cinco 9s)       | 5,26 minutos              | 25,9 segundos             | 0,87 segundos             |

A busca pelos 9s de disponibilidade não é apenas uma questão técnica; é um compromisso com os usuários e com a missão da empresa. Cada "9" adicional representa uma ordem de magnitude na melhoria da confiabilidade. Uma diferença aparentemente pequena na porcentagem traduz-se em uma diferença significativa no tempo de inatividade ao longo de um ano. No mundo real, isso pode significar milhares de transações ou interações de usuários perdidas.

## 4.2 Os Desafios dos 9s

Alcançar alta disponibilidade é uma tarefa complexa. Envolve:

- **Monitoramento Proativo**: Detectar e resolver problemas antes que afetem os usuários.
- **Planejamento de Capacidade**: Garantir que os sistemas possam lidar com picos de demanda.
- **Backup e Recuperação**: Ter planos e infraestrutura para recuperar de falhas rapidamente.
- **Atualizações e Manutenções**: Implementar mudanças sem afetar a disponibilidade.

### Por que escolher quatro 9s em vez de cinco?

Escolher um nível de disponibilidade é uma decisão estratégica que leva em consideração vários fatores:

1. **Natureza do Serviço**: Um sistema bancário online pode exigir cinco 9s devido à criticidade das transações, enquanto um blog pode estar bem com quatro 9s.
2. **Custo**: Atingir cada "9" adicional pode exigir um investimento significativo em infraestrutura, ferramentas e recursos humanos.
3. **Complexidade**: Sistemas com mais 9s podem necessitar de arquiteturas mais complexas, com redundância, failovers e outros mecanismos avançados.
4. **Retorno sobre o Investimento (ROI)**: Em alguns casos, o benefício adicional de um "9" extra pode não justificar o custo.

### Exemplo Prático: Diferentes Aplicações em um Sistema Bancário
Dentro de um grande sistema bancário, existem diversas aplicações que atendem a variados propósitos e, consequentemente, têm diferentes requisitos de disponibilidade:

1. **Sistema de Transações Financeiras**: Esta é a espinha dorsal do banco, gerenciando transferências, pagamentos e outras transações monetárias. Qualquer tempo de inatividade aqui pode resultar em grandes perdas financeiras, tanto para o banco quanto para seus clientes, sem mencionar a perda de confiança. Portanto, esta aplicação pode exigir cinco 9s (99,999% de disponibilidade).
2. **Portal de Internet Banking**: Usado pelos clientes para acessar suas contas, fazer pagamentos e verificar saldos. Enquanto o tempo de inatividade é indesejável, breves interrupções para manutenção programada ou atualizações podem ser aceitáveis fora do horário comercial. Aqui, quatro 9s (99,99% de disponibilidade) podem ser suficientes.
3. **Sistema de Atendimento ao Cliente**: Usado para gerenciar interações com o cliente, como consultas e reclamações. Embora seja importante, pode não exigir a mesma disponibilidade que o sistema de transações. Quatro 9s (99,99% de disponibilidade) ou até mesmo três 9s (99,9% de disponibilidade) podem ser adequados, dependendo da estratégia de negócios.
4. **Sistema de Análise de Dados Internos**: Utilizado para análises internas, geração de relatórios e tomada de decisões estratégicas. A disponibilidade crítica em tempo real pode não ser tão essencial aqui, e três 9s (99,9% de disponibilidade) podem ser suficientes.

Ao avaliar o nível adequado de disponibilidade para cada aplicação, os bancos devem considerar o impacto potencial do tempo de inatividade, tanto em termos financeiros quanto na satisfação do cliente. Também é crucial considerar os custos e a complexidade associados ao aumento da disponibilidade.

## 4.3 Conclusão

Os 9s de disponibilidade são uma representação tangível da confiabilidade em SRE. Eles são um lembrete contínuo da promessa de SREs de entregar sistemas robustos, resilientes e que os usuários podem contar.