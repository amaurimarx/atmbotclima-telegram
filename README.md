# Telegram Weather Chatbot - n8n

Este projeto é um chatbot para Telegram desenvolvido no n8n que consulta a temperatura atual de cidades utilizando a API da OpenWeather.

## 🚀 Funcionalidades
- Recebe nomes de cidades via Telegram.
- Consulta a api do Geocoding validando nome da cidade e estado e obtendo as localizações de latitude e longitude para maior precisão.
- Consulta o clima em tempo real utilizando os dados obtidos anteriormente.
- Retorna mensagens formatadas com emojis.
- Tratamento de erro para cidades não encontradas.

## 📦 Requisitos
- Instalação do **n8n** (Local, Docker ou Cloud).
- Token de Bot do Telegram (obtido via [@BotFather](https://t.me/botfather)).
- Chave de API da **OpenWeather** (plano gratuito).

## 📥 Como Importar o Workflow
1. No seu n8n, clique no ícone de engrenagem ou menu principal e selecione **"Import from File"**.
2. Selecione o arquivo `workflow-chatbot-telegram.json` presente neste repositório.
3. O workflow aparecerá na sua tela.

## 🔑 Configuração de Credenciais
O workflow utiliza duas credenciais principais:

1.  **Telegram API**:
    - No nó `Telegram Trigger`, clique em "Select Credential" > "Create New".
    - Insira o `Access Token` fornecido pelo BotFather.
2.  **OpenWeather API**:
    - O nó HTTP Request está configurado para ler a variável de ambiente `OPENWEATHER_API_KEY`. 
    - Caso prefira não usar variáveis de ambiente, você pode substituir o campo `appid` diretamente no nó HTTP Request pela sua chave.

## 🛠️ Como Executar
1. Ative o workflow no n8n (botão **Active** no canto superior direito).
2. Abra o seu bot no Telegram.
3. Envie o nome de uma cidade e estado (Ex: `Maravilha, SC`).
4. **Resultado esperado**: `🌤️ A temperatura em Maravilha é de 24°C.`

## ⚠️ Fallback e Erros
Caso a cidade seja digitada incorretamente ou não exista na base da OpenWeather, o bot responderá:
> ❌ Cidade não encontrada. Use o formato Cidade, UF (ex.: Maravilha, SC).
