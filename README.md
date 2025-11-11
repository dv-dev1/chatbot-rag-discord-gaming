# Estudo de Caso: Agente de Suporte (RAG) para Comunidade Gamer no Discord

Este projeto é um estudo de caso de um agente de IA autônomo, construído em n8n, para atuar como um moderador de suporte 24/7 em um servidor de Discord de um jogo online.

---

## 🎯 O Problema de Negócio

Servidores de Discord de jogos online recebem um fluxo constante de perguntas repetitivas dos jogadores (FAQs) sobre mecânicas do jogo, regras, NFTs, etc. A moderação humana é limitada por horário e custo, gerando respostas lentas e jogadores frustrados.

O desafio era criar uma solução que fornecesse:
* Respostas instantâneas e precisas, 24/7.
* Informações consistentes, baseadas *apenas* na documentação oficial do jogo.
* Uma experiência de conversa natural para os jogadores.

## solution 🛠️ A Arquitetura da Solução

Desenvolvi um agente de IA no n8n que utiliza uma arquitetura **RAG (Retrieval-Augmented Generation)** para garantir que as respostas sejam 100% baseadas nos fatos.

O fluxo lógico funciona da seguinte maneira:

1.  **Webhook + Classificação (Gemini):** A mensagem do Discord é recebida. Um primeiro modelo de IA classifica a intenção do usuário (ex: "CONVERSA FIADA" ou "DÚVIDA SOBRE O JOGO").
2.  **Busca Vetorizada (RAG):** Se for uma dúvida, o sistema busca em um **Banco de Dados Vetorial (Pinecone)** os trechos mais relevantes da documentação oficial do jogo que correspondam à pergunta.
3.  **Memória (PostgreSQL):** O agente acessa um banco de dados SQL para lembrar o histórico da conversa com aquele jogador, permitindo que ele entenda o contexto.
4.  **Geração da Resposta (Agente OpenAI):** O agente principal recebe a pergunta original, o histórico da conversa e os "documentos" encontrados pelo Pinecone. Ele então formula uma resposta coesa e precisa.
5.  **Ação (Discord API):** A resposta final é enviada de volta ao canal do Discord.

## 🖼️ Visualização do Fluxo

Abaixo está um screenshot da arquitetura do workflow construído no n8n. (Informações sensíveis como nomes de bancos de dados e chaves de API foram omitidas por questões de confidencialidade).

(PARE AQUI POR UM SEGUNDO)
