# BotFlix

Assistente de filmes que recebe uma descrição de humor ou preferência e apresenta uma recomendação com informações do filme.

## Sobre o projeto

O BotFlix propõe uma forma simples de encontrar um filme a partir do que a pessoa deseja assistir. A interface coleta uma descrição em texto e a envia para um webhook local; a resposta é exibida em um cartão com pôster, título, sinopse e avaliação.

## Funcionalidades

- **Busca por descrição:** informe seu humor, gênero ou tipo de filme desejado em um campo de texto.
- **Envio da busca:** use o botão “Encontrar Filmes Perfeitos” ou pressione `Enter`. `Shift + Enter` mantém a quebra de linha no campo.
- **Validação do campo:** uma mensagem é exibida se a busca for enviada sem texto.
- **Exemplos de pesquisa:** a página mostra sugestões de frases para orientar o preenchimento. Elas são exemplos visuais, não botões.
- **Exibição de recomendação:** a interface apresenta o primeiro filme recebido, incluindo pôster, título, sinopse e nota. Caso a sinopse não esteja disponível, mostra uma mensagem alternativa; caso a avaliação não seja numérica, mostra `N/A`.
- **Efeitos visuais:** fundo com gradientes animados, entrada gradual do conteúdo, imagem do robô flutuante, realce do botão e elevação do cartão de filme ao passar o cursor.

> A busca depende de um fluxo criado no **n8n**, acessível em `http://localhost:5678/webhook-test/botflix`. O código envia o texto como `userPrompt` em uma requisição `POST` e espera uma resposta JSON com uma lista `results`. A implementação do fluxo do n8n não está incluída neste repositório.

## Tecnologias utilizadas

- **HTML5** para a estrutura da página.
- **CSS3** para estilos, layout, efeitos visuais, animações e regras responsivas.
- **JavaScript** para capturar interações, enviar a busca com `fetch` e montar o cartão de resultado.
- **n8n** para criar o fluxo de automação que recebe a busca pelo webhook e integra a recomendação de filmes.
- **Google Fonts (Inter)** como fonte externa.
- **TMDB Image CDN** como origem das imagens dos pôsteres (`image.tmdb.org`).

## Layout e responsividade

A página usa uma área centralizada com largura máxima de 1200 px, cartão de busca limitado a 600 px e cartões de resultado organizados em um grid flexível. Em telas menores, os cartões de filmes passam a ocupar uma largura proporcional à tela e ficam empilhados; imagens e espaçamentos também se ajustam. Há regras específicas para larguras abaixo de 600 px, até 900 px e a partir de 768 px.

## Como executar o projeto

1. Clone o repositório:

   ```bash
   git clone https://github.com/KhaledSilva/botflix.git
   ```

2. Entre na pasta:

   ```bash
   cd botflix
   ```

3. Abra `index.html` no navegador ou sirva a pasta com um servidor HTTP estático local.

Para realizar buscas, o webhook esperado pelo código também precisa estar acessível em `http://localhost:5678/webhook-test/botflix` e responder no formato utilizado pela página. Sem esse serviço, a interface pode ser aberta, mas a recomendação não será obtida.
