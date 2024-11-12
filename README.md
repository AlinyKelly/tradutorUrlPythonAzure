# URL Translator

Este repositório contém um código Python que realiza a extração e tradução automática de artigos do site Dev.to, utilizando a API do Azure OpenAI para traduzir apenas o conteúdo relevante, excluindo seções desnecessárias como comentários e formatando o resultado para Markdown.

Desenvolvido durante o Bootcamp Microsoft AI-102 promovido pela DIO.

## Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Configuração](#configuração)
- [Como Usar](#como-usar)
- [Pré-requisitos](#pré-requisitos)
- [Contribuição](#contribuição)
- [Licença](#licença)

## Visão Geral

Este script permite extrair conteúdo de artigos do Dev.to e traduzi-los automaticamente para o idioma de sua escolha. Ele elimina seções desnecessárias (como comentários e modais) e envia o conteúdo para tradução através da API Azure OpenAI.

## Funcionalidades

- **Extração de Conteúdo**: Extrai o conteúdo principal do artigo, excluindo seções desnecessárias como `comments` e `hide-comments-modal`.
- **Limpeza do Texto**: Remove scripts, estilos e espaços desnecessários para manter apenas o texto do artigo.
- **Divisão em Blocos**: Divide o conteúdo em blocos menores para evitar exceder o limite de tokens da API Azure.
- **Tradução com API Azure OpenAI**: Envia o texto para a API para tradução, com lógica de controle para evitar limites de requisição.

## Configuração

### 1. Clonar o repositório

```
git clone https://github.com/AlinyKelly/tradutorUrlPythonAzure.git
cd tradutorUrlPythonAzure
```

### 2. Configurar a API Azure OpenAI

Este projeto requer uma conta na Azure OpenAI Service. Configure suas chaves de API e o endpoint no código Python.

Atualize as variáveis de configuração na instância `AzureChatOpenAI`:

```
client = AzureChatOpenAI(
    azure_endpoint="YOUR_AZURE_ENDPOINT",
    api_key="YOUR_API_KEY",
    api_version="YOUR_API_VERSION",
    azure_deployment="YOUR_DEPLOYMENT_NAME",
    max_retries=0
)
```

### 3. Instalar Dependências

Este projeto utiliza `requests` e `beautifulsoup4`. Instale as dependências com:
```
pip install requests beautifulsoup4 openai langchain-openai
```

## Como Usar

Defina a URL do Artigo: Insira a URL do artigo do Dev.to que deseja traduzir.

Execute o Script: Execute o código para extrair o conteúdo e traduzir o artigo para o idioma desejado.

```
url = 'https://dev.to/exemplo-de-artigo'
text = extract_text_from_url(url)

if text:
    article = translate_text_in_chunks(text, "pt-br")
    print(article)
```

## Pré-requisitos
- Python 3.7 ou superior
- Conta e chave de API no Azure OpenAI
- Dependências: `requests`, `beautifulsoup4`, `langchain_openai`

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir Issues para sugestões ou dúvidas, e faça um fork para enviar Pull Requests com melhorias.

## Licença

Este projeto é licenciado sob a licença MIT.

### Ajustes a Fazer

- Substitua `"YOUR_AZURE_ENDPOINT"`, `"YOUR_API_KEY"`, `"YOUR_API_VERSION"` e `"YOUR_DEPLOYMENT_NAME"` com os valores de configuração da sua conta Azure.
- Personalize o repositório, caso tenha alguma configuração extra ou requisitos específicos.
