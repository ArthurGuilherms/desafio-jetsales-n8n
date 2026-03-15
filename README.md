<h1 align="center">🤖 JetFit Suplementos - IA Sales Assistant</h1>

<p align="center">
  <i>Solução de chatbot com IA Generativa desenvolvida para o Desafio Técnico da JetSales Brasil.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/n8n-FF6D5W?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />
  <img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI" />
  <img src="https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white" alt="Google Sheets" />
  <img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp" />
</p>

<hr>

## 📋 Sobre o Projeto

Este projeto consiste em um assistente virtual construído em low-code (**n8n**), integrado à plataforma omnichannel da JetSales via API e Webhooks. O bot utiliza modelos de **IA Generativa** para atuar como um consultor de vendas da "JetFit Suplementos", guiando o cliente desde a sondagem de objetivos até a simulação do checkout.

🎥 **[Assista aqui ao vídeo de apresentação e demonstração do projeto](LINK_DO_SEU_VIDEO_AQUI)**

## ✨ Principais Funcionalidades

- **🧠 Atendimento Consultivo (LLM):** Respostas dinâmicas e humanizadas, formatadas visualmente para WhatsApp (uso de emojis e quebras de linha).
- **🎙️ Voice-to-Text Integrado:** Suporte a mensagens de áudio. Utiliza a API Whisper (via Groq) para transcrever a voz do cliente e manter o contexto da conversa.
- **📊 Gestão de Inventário em Tempo Real:** Consulta ao banco de dados (Google Sheets) para validar disponibilidade. Se o estoque estiver baixo, a IA injeta gatilhos mentais de escassez na resposta.
- **🛒 Fluxo de Checkout:** O bot gera um resumo do pedido e simula a cobrança enviando a chave PIX e um QR Code dinâmico, seguido da baixa automática no estoque.
- **👨‍💻 Handoff Inteligente:** Escalonamento automático para atendimento humano no painel JetSales caso a IA identifique intenções complexas ou caso ocorra erro no fluxo.

## ⚙️ Instruções de Configuração e Execução

Siga os passos abaixo para configurar e rodar o projeto em sua máquina ou servidor:

### 1. Pré-requisitos
Certifique-se de ter em mãos:
- Instância do **n8n** (Cloud ou Self-hosted) atualizada.
- API Key da **OpenAI** (ou Google Gemini).
- API Key do **Groq** (para o modelo Whisper).
- Conta no Google Cloud com a **Google Sheets API** ativada (para autenticação OAuth2).
- URL base e Token Bearer da **JetSales API**.

### 2. Importando o Fluxo
1. Faça o download do arquivo `fluxo-jetfit.json` contido neste repositório.
2. Na interface do n8n, acesse o menu superior direito, clique em **Import from File** e selecione o arquivo.

### 3. Configurando as Credenciais
No fluxo importado, configure as credenciais nos respectivos nós:
- **Chat Model:** Insira sua chave da API de IA.
- **HTTP Request (Whisper):** Insira a chave do Groq no formato `Bearer Auth`.
- **Google Sheets:** Autentique sua conta Google para permitir leitura/escrita.
- **Nós de API JetSales:** Configure a credencial `httpBearerAuth` com o token da plataforma.

### 4. Configurando Destinatários (Alertas e Escalonamento)
Para que os alertas internos funcionem corretamente na sua operação, atualize os seguintes nós com os dados da sua equipe:
- **WhatsApp da Equipe (Handoff):** Nos nós `Escalonamento Solicitado`, `Escalonamento Solicitado por Erro` e `Informa Venda WhatsApp`, altere o parâmetro `number` para o número de WhatsApp do responsável (ex: gerente ou suporte).
- **E-mails de Log:** Nos nós do Gmail (`Informa Venda E-mail` e `Informa Erro ao Suporte`), altere o campo `Send To` para o e-mail da sua equipe.

### 5. Configurando o Banco de Dados (Sheets)
Crie uma planilha no Google Sheets com as seguintes colunas:
`Produto` | `Preço` | `Estoque` | `Descricao` | `Imagem`

*Dica: Após criar a planilha, entre nos nós do Google Sheets dentro do fluxo e selecione o seu arquivo.*

### 6. Ativando o Webhook
1. Dê um duplo clique no nó inicial `Webhook: Entrada WhatsApp`.
2. Copie a URL gerada na aba **Production URL**.
3. Acesse o painel da JetSales em `Configurações > API/Webhook` e cole a URL para habilitar o recebimento de eventos.
4. Salve o fluxo e altere a chave principal no canto superior direito do n8n para **Active**.

---

## 👨‍💻 Autor

**Arthur Guilherme Guimarães Silva**
- [LinkedIn](https://www.linkedin.com/in/arthur-guilherms)
- [GitHub](https://github.com/arthur-guilherms)
- Contato: arthurguilhermss@gmail.com
