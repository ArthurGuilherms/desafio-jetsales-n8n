\# 🤖 Assistente Virtual Inteligente - JetFit Suplementos (Desafio JetSales)



\## 📋 Sobre o Projeto

Este repositório contém a solução desenvolvida para o desafio técnico da vaga na JetSales Brasil. Trata-se de uma aplicação de chatbot construída em \*\*n8n\*\*, integrada à plataforma de atendimento omnichannel da JetSales via Webhook e API.



O assistente atua como um consultor de vendas para a loja fictícia "JetFit Suplementos", utilizando Inteligência Artificial Generativa para oferecer um atendimento humanizado, consultivo e focado em conversão, além de gerenciar estoque em tempo real.



🎥 \*\*\[Clique aqui para assistir ao vídeo de apresentação e demonstração do projeto]\*\* \*(Insira o link do seu vídeo aqui)\*



\## 🚀 Principais Funcionalidades (Features)

\* \*\*Atendimento Humanizado e Formatado:\*\* O bot utiliza IA para responder dúvidas comuns de forma dinâmica, formatando listas de produtos com quebras de linha e emojis (📦) para excelente UX no WhatsApp.

\* \*\*🎙️ Voice-to-Text (Acessibilidade):\*\* Integração com a API Whisper (via Groq) para transcrição imediata de áudios. O cliente pode enviar mensagens de voz, e a IA processa e responde com o mesmo nível de contexto.

\* \*\*📊 Gestão Dinâmica de Estoque:\*\* Consulta em tempo real a uma planilha do Google Sheets. O sistema identifica níveis de estoque, aplica gatilhos de urgência ("Últimas unidades!") no prompt e realiza a baixa automática do inventário após o "pagamento".

\* \*\*👨‍💻 Handoff (Escalonamento Humano):\*\* Mecanismo de roteamento inteligente. Se o cliente fizer solicitações complexas ou fora do escopo, o bot alerta a equipe internamente e transfere o atendimento via API da JetSales.

\* \*\*🛡️ Sistema Anti-Flood e Tratamento de Erros:\*\* Debounce configurado para evitar múltiplas execuções simultâneas e disparos automáticos de e-mail/WhatsApp para a equipe de TI caso a IA ou a API apresentem falhas.



\## 🏗️ Arquitetura e Tecnologias Utilizadas

\* \*\*Orquestração:\*\* n8n (Low-code)

\* \*\*IA Generativa:\*\* Gemini / OpenAI \*(Ajuste para o que você definir na versão final)\*

\* \*\*Transcrição de Áudio:\*\* Whisper-large-v3

\* \*\*Banco de Dados (Mock):\*\* Google Sheets API

\* \*\*Integração:\*\* JetSales API (Endpoints de envio de mensagem e mídia)



\## ⚙️ Como Configurar e Executar o Projeto



Siga os passos abaixo para rodar este fluxo em sua própria instância do n8n:



\### Pré-requisitos

1\. Uma instância do \*\*n8n\*\* (Cloud ou Self-hosted) rodando.

2\. Chaves de API:

&#x20;  \* IA Generativa (OpenAI ou Google Gemini).

&#x20;  \* Groq (para o nó de transcrição de áudio).

3\. Credenciais de autenticação do Google (OAuth2) para acesso ao Google Sheets.

4\. Token Bearer da \*\*JetSales\*\* para autenticação nos nós de \*HTTP Request\*.



\### Passo a Passo de Instalação

1\. \*\*Importar o Fluxo:\*\* \* Faça o download do arquivo `fluxo-jetfit.json` disponível neste repositório.

&#x20;  \* No n8n, clique em `Import from File` (ou arraste o arquivo para a área de trabalho do n8n).

2\. \*\*Configurar Credenciais:\*\* \* Abra os nós sinalizados com erro de credencial (Google Sheets, IA Model, Groq, JetSales HTTP Requests) e insira suas respectivas chaves de API.

3\. \*\*Configurar o Banco de Dados (Google Sheets):\*\*

&#x20;  \* Crie uma planilha no Google Sheets com as colunas: `Produto`, `Preço`, `Estoque`, `Descricao` e `Imagem`.

&#x20;  \* Atualize os nós do Google Sheets no fluxo selecionando a sua planilha recém-criada.

4\. \*\*Configurar o Webhook na JetSales:\*\*

&#x20;  \* Dê um duplo clique no nó inicial `Webhook: Entrada WhatsApp`.

&#x20;  \* Copie a \*\*Production URL\*\*.

&#x20;  \* Acesse o painel da JetSales, navegue até `Configurações > API/Webhook` e cole a URL copiada para receber os eventos de novas mensagens.

5\. \*\*Ativação:\*\* \* Salve o fluxo e ative a chave no canto superior direito do n8n (`Active`). 

&#x20;  \* O assistente já estará pronto para receber e responder mensagens!



\## 💡 Autor

\*\*Arthur Guilherme Guimarães Silva\*\*

\* \[LinkedIn](https://www.linkedin.com/in/arthur-guilherms) \*(Coloque o link correto do seu perfil)\*

\* E-mail: arthurguilhermss@gmail.com

