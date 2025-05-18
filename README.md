# Chatbot de Busca de Imóveis com Gemini e Google Search

## Sobre o Projeto

Este é um projeto de chatbot simples desenvolvido em Python que demonstra como criar um assistente conversacional capaz de buscar informações sobre empreendimentos imobiliários. O chatbot utiliza a API do Google Gemini para entender as perguntas dos usuários em linguagem natural e busca por imóveis em um catálogo interno fictício ou, quando necessário, na internet através da ferramenta Google Search.

O objetivo principal é ilustrar a integração de modelos de linguagem (LLMs) com dados internos e ferramentas de busca externa para criar aplicações úteis em um ambiente como o Google Colab.

## Funcionalidades

* **Interpretação de Linguagem Natural:** Entende as perguntas do usuário sobre busca de imóveis (tipo, status, bairro) usando a API do Google Gemini.
* **Catálogo Interno de Imóveis:** Possui um catálogo fictício de empreendimentos (casas, apartamentos, etc.) com detalhes e status (à venda, locação).
* **Busca Dinâmica:** Realiza buscas primeiro no catálogo interno. Se não encontrar o imóvel específico no bairro ou se o bairro não existir no catálogo, busca na internet usando a ferramenta Google Search.
* **Busca Web Integrada:** Apresenta resultados da busca na web com links clicáveis (em ambientes que suportam Markdown, como o Google Colab).
* **Além do catalogo:** Ao pesquisar por imoveis fora do catalogo interno, faz perguntads como orçamento, se prefere perto de transporte publico, para sugerir sites de pesquisa de imoveis.
* **Gestão de Conversa:** Lida com saudações e permite conversas fora do contexto de busca de imóveis por um número limitado de vezes, encerrando a conversa cordialmente se o foco em imóveis for perdido.
* **Output Formatado:** Apresenta as respostas formatadas em Markdown para melhor legibilidade na saída do console ou notebook.

## Como Funciona (Simplificado)

1.  O usuário digita uma pergunta no console.
2.  A pergunta é enviada para a API do Google Gemini para identificar se o usuário quer buscar um imóvel e extrair informações como tipo (casa, apartamento), status (comprar, alugar) e bairro.
3.  Se a intenção for buscar um imóvel:
    * O chatbot verifica se o bairro existe no catálogo interno.
    * Se existir, busca no catálogo pelos imóveis que se encaixam nos critérios.
    * Se não encontrar o imóvel específico no catálogo para os critérios solicitados (seja porque o bairro não existe ou porque a combinação específica não foi encontrada no bairro), uma query é gerada e a ferramenta Google Search é utilizada para buscar na internet.
4.  Se a intenção não for buscar imóvel (uma saudação ou pergunta aleatória), o Gemini responde de forma conversacional por algumas vezes.
5.  A resposta (resultados do catálogo, resultados da web, ou resposta conversacional) é formatada em Markdown e exibida para o usuário no console.
6.  O chat mantém um histórico da conversa para que o Gemini possa ter contexto nas respostas subsequentes.

## Primeiros Passos

Para executar este projeto no ambiente Google Colab:

1.  Certifique-se de ter acesso a um notebook Google Colab.
2.  Instale as bibliotecas Python necessárias executando os seguintes comandos em uma célula de código:
    ```bash
    !pip install google-generativeai markdown google-adk
    ```
3.  Obtenha uma **Chave de API do Google Gemini** no [Google AI Studio](https://aistudio.google.com/).
4.  No Google Colab, armazene sua chave de API usando a ferramenta `userdata`:
    ```python
    from google.colab import userdata
    # Será solicitada a sua chave de API
    userdata.set('GOOGLE_API_KEY', 'SUA_CHAVE_DE_API_AQUI')
    ```
    (Substitua `'SUA_CHAVE_DE_API_AQUI'` pela sua chave real ou use a interface segura do Colab para armazenar segredos).
5.  Copie o código completo do chatbot em uma célula de código separada no seu notebook Colab.
6.  Execute a célula do código do chatbot.

## Como Usar

1.  Após executar a célula do código, o chatbot irá iniciar e você verá a mensagem de boas-vindas.
2.  Digite suas perguntas na linha de entrada que aparece no console (ou na área de entrada da célula do Colab).
3.  Experimente perguntar sobre imóveis com diferentes tipos, status e bairros (alguns existem no catálogo, outros não).
4.  Teste fazer perguntas fora do contexto de busca de imóveis.
5.  Digite `fim` a qualquer momento para encerrar a conversa.

## Estrutura do Código (Opcional, para quem quiser se aprofundar)

* `CatalogoEmpreendimentosFicticio`: Classe que simula um catálogo de imóveis interno.
* `interpretar_pergunta`: Função que usa o Gemini para extrair critérios de busca ou identificar se a pergunta está fora do tópico.
* `generar_resposta_catalogo`: Função para formatar os resultados encontrados no catálogo interno em Markdown.
* `buscar_na_web`: Função que utiliza a ferramenta `Google Search` para buscar na internet e formata os resultados em Markdown.
* Loop principal (`while True`): Contém a lógica central para gerenciar a conversa, decidir entre busca interna/web, controlar o contador de perguntas fora do contexto e imprimir as respostas.

## Melhorias Futuras (Opcional)

* Incluir filtros de busca mais avançados (preço, número de quartos, área, etc.) tanto no catálogo interno quanto na query para a busca web.
* Integrar com um banco de dados real para o catálogo de imóveis, ou carregar os dados de um arquivo (CSV, JSON).
* Desenvolver uma interface gráfica ou web mais amigável para o chat.
* Expandir os tipos de imóveis e critérios de busca reconhecidos pelo interpretador.
* Melhorar o tratamento de erros e a experiência do usuário em caso de falhas na busca ou API.
* Permitir que o usuário selecione um imóvel específico dos resultados para ver mais detalhes (se disponíveis).

## Autor

Sandro Neri de Paiva
SandroPaiva (https://github.com/SandroPaiva)


## Repositório

https://github.com/SandroPaiva/projeto_chatbot_alura/edit/main/README.md
