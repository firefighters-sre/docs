# 4. "Automação, Gestão de Capacidade e Otimização de Evacuação"
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

