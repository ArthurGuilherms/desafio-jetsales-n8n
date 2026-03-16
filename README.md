<h1 align="center">🤖 JetFit Suplementos - IA Sales Assistant</h1>

<p align="center">
  <i>Solução de chatbot com IA Generativa desenvolvida para o Desafio Técnico da JetSales Brasil.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/n8n-FF6D5W?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />
  <img src="https://img.shields.io/badge/Groq-F55036?style=for-the-badge&logo=groq&logoColor=white" alt="Groq" />
  <img src="https://img.shields.io/badge/Meta_Llama_3-046A38?style=for-the-badge&logo=meta&logoColor=white" alt="Llama 3" />
  <img src="https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white" alt="Google Sheets" />
  <img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp" />
</p>

<hr>

## 📋 Sobre o Projeto

Este projeto consiste num assistente virtual construído em low-code (**n8n**), integrado na plataforma omnichannel da JetSales via API e Webhooks. O bot utiliza o modelo **Llama 3.3 70B (via Groq API)** para atuar como um consultor de vendas da "JetFit Suplementos", guiando o cliente desde a sondagem de objetivos até à simulação do checkout com altíssima velocidade e estabilidade na geração de dados estruturados (JSON).

🎥 **[Assista aqui ao vídeo de apresentação e demonstração do projeto](https://www.youtube.com/watch?v=e8DAL8ewqrg)**

## ✨ Principais Funcionalidades

- **🧠 Atendimento Consultivo (LLM):** Respostas dinâmicas e humanizadas, formatadas visualmente para o WhatsApp (uso de emojis e quebras de linha).
- **🎙️ Voice-to-Text Integrado:** Suporte a mensagens de áudio. Utiliza a API Whisper (via Groq) para transcrever a voz do cliente e manter o contexto da conversa.
- **📊 Gestão de Inventário em Tempo Real:** Consulta à base de dados (Google Sheets) para validar disponibilidade. Se o stock estiver em baixo, a IA injeta gatilhos mentais de escassez na resposta.
- **🛒 Fluxo de Checkout:** O bot gera um resumo do pedido e simula a cobrança enviando a chave PIX, seguido da baixa automática no stock.
- **👨‍💻 Handoff Inteligente:** Escalonamento automático para atendimento humano no painel JetSales caso a IA identifique intenções complexas, dúvidas pós-venda ou caso ocorra algum erro no fluxo.

## ⚙️ Instruções de Configuração e Execução

Siga os passos abaixo para configurar e correr o projeto na sua máquina ou servidor:

### 1. Pré-requisitos
Certifique-se de ter em mãos:
- Instância do **n8n** (Cloud ou Self-hosted) atualizada.
- API Key da **Groq** (usada tanto para o modelo Whisper quanto para o Llama 3).
- Conta no Google Cloud com a **Google Sheets API** ativada.
- URL base e Token Bearer da **JetSales API**.

### 2. Importar o Fluxo
1. Faça o download do ficheiro `fluxo-jetfit.json` contido neste repositório.
2. Na interface do n8n, aceda ao menu superior direito, clique em **Import from File** e selecione o ficheiro.

### 3. Configurar as Credenciais
No fluxo importado, configure as credenciais nos respetivos nós:
- **Groq Chat Model:** Insira a sua chave da API da Groq.
- **HTTP Request (Whisper):** Insira a mesma chave da Groq no formato `Bearer Auth`.
- **Google Sheets / Gmail:** Autentique a sua conta Google.
- **Nós de API JetSales:** Configure a credencial `httpBearerAuth` com o token da plataforma e atualize os URLs com o seu ID de integração.

### 4. Configurar Destinatários (Alertas e Escalonamento)
Para que os alertas internos funcionem corretamente na sua operação, atualize os seguintes nós com os dados da sua equipa:
- **WhatsApp da Equipa (Handoff):** Nos nós de requisição HTTP (como `Escalonamento Solicitado` e `Informa Venda WhatsApp`), altere o parâmetro `number` para o número de WhatsApp do responsável.
- **E-mails de Registo (Log):** Nos nós do Gmail (`Informa Venda E-mail` e `Informa Erro ao Suporte`), altere o campo `Send To` para o e-mail da sua equipa.

### 5. Ativar o Webhook
1. Dê um duplo clique no nó inicial `Webhook: Entrada WhatsApp`.
2. Copie o URL gerado no separador **Production URL**.
3. Aceda ao painel da JetSales em `Configurações > API/Webhook` e cole o URL para ativar a receção de eventos.
4. Guarde o fluxo e altere a chave principal no canto superior direito do n8n para **Active**.

---

## 👨‍💻 Autor

**Arthur Guilherme**
- [LinkedIn](https://www.linkedin.com/in/arthur-guilherms)
- [GitHub](https://github.com/arthur-guilherms)
