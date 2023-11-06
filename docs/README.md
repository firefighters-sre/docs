# Firefighters SRE Workshop docs

Este repositório é dedicado à documentação do workshop Firefighters SRE, que simula um sistema de gestão e monitoramento de edifícios. Através de cenários realistas, os participantes são imersos em desafios que replicam a dinâmica de um ambiente de Engenharia de Confiabilidade de Site (SRE). Múltiplos componentes e microserviços colaboram para garantir a segurança, eficiência e confiabilidade do edifício, e os participantes são encorajados a aplicar melhores práticas de SRE para gerenciar e resolver incidentes.

## 📁 Estrutura do Repositório

- **`/changelogs`**: Contém registros de mudanças feitas no projeto, incluindo backlog e notas de lançamento.
- **`/docs`**: Diretório principal com toda a documentação do workshop, estruturada da seguinte forma:
  - **0_Platform**: Introdução à plataforma e às tecnologias utilizadas no workshop.
  - **1_Incidentes**: Aborda a gestão de incidentes, desde a identificação até a resolução.
  - **2_Monitoramento**: Foca nas melhores práticas de monitoramento, permitindo a detecção precoce de problemas e a análise aprofundada de métricas.
  - **3_PostMortem**: Discute a importância da análise pós-incidente e como realizar uma análise de causa raiz.
  - **4_Disponibilidade**: Explora o conceito de disponibilidade, demonstrando como alcançar altos níveis de uptime e confiabilidade.
  - **5_Testes**: Discute a importância dos testes em um ambiente SRE e como eles podem prevenir incidentes.
  - **`_sidebar.md`**: Contém a barra lateral de navegação do site da documentação.
  - **`index.html`**: O arquivo HTML principal para o site de documentação Docsify.
- **`/docs/desafios`**: Diretórios de desafios que fornecem detalhes sobre os desafios específicos enfrentados durante o workshop.
- **`/docs/images`**: Contém imagens, diagramas e outros recursos visuais relevantes para a documentação e desafios.

Os módulos do workshop Firefighters SRE são criados usando o **Docsify**. Escreva a documentação em Markdown e use o CLI do Docsify para servi-los. Armazene a documentação de cada módulo no diretório `docs/<numero-do-modulo>`.

## 📘 O que é o Docsify?
Docsify é uma ferramenta leve para gerar sites de documentação diretamente de arquivos markdown. Diferentemente de alguns outros geradores de sites estáticos, o Docsify não requer que você compile o markdown em HTML com antecedência. Em vez disso, ele gera dinamicamente o conteúdo do site quando a página é carregada, tornando-o bastante ágil. Com uma variedade de plugins e temas disponíveis, o Docsify oferece uma maneira flexível e fácil de criar documentação interativa e amigável.

### 🔍 Pré-requisitos:
1. Certifique-se de ter o [Node.js](https://nodejs.org/) instalado. Ele virá com o npm (gerenciador de pacotes do node) que é usado para instalar o Docsify.

### 1. Instale o Docsify CLI:
Se você ainda não instalou o Docsify CLI, pode fazê-lo usando o npm:

```bash
npm install -g docsify-cli
```

### 2. Inicialize e Sirva os Documentos:
Sirva os documentos:

```bash
docsify serve docs
```

Isso iniciará um servidor local, geralmente em http://localhost:3000. Abra este link no seu navegador para ver sua documentação.

### 3. Acessando a Documentação ao Vivo:
Depois de iniciar o servidor Docsify usando o comando acima, você pode acessar sua documentação ao vivo navegando para a URL local fornecida (normalmente http://localhost:3000).

#### 🛠️ Dicas:

- Sempre que fizer alterações nos arquivos de documentação, simplesmente atualize o navegador para ver o conteúdo atualizado.
- Você pode personalizar a aparência e funcionalidade do seu site Docsify editando o arquivo index.html na raiz do seu diretório de documentação. O Docsify oferece uma infinidade de opções para melhorar e personalizar sua experiência de documentação.

#### 📜 Configurações e Personalizações:
Se você precisar de configurações específicas, personalizações ou quiser adicionar plugins, temas, etc., pode fazê-lo editando o arquivo index.html na raiz do seu diretório de documentação.

🧠 Lembre-se, o Docsify carrega o conteúdo dinamicamente, então não há necessidade de recompilar ou reconstruir toda vez que você fizer alterações. Uma simples atualização do navegador resolverá!

## 🤝 Contribuindo

Se você deseja contribuir para esta documentação, sinta-se à vontade para fazer um fork, fazer suas alterações e enviar um pull request.

## 📬 Contato

Para quaisquer perguntas ou feedback, entre em contato com Gabriel Sampaio em gsampaio@redhat.com.
