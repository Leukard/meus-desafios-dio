# 🎯 Desafio Criativo: Planejando Automações com N8N

## 🧱 Passo 1: Definição da Automação

Quero criar uma automação no N8N para receber novos leads vindos de um formulário, qualificar o perfil do lead automaticamente usando IA e direcionar o contato para a equipe comercial.

* **Público ou responsável:** Equipe Comercial e SDRs (Sales Development Representatives).
* **Resultado esperado:** Registrar o lead qualificado em uma planilha do Google Sheets e enviar uma notificação imediata no Slack para os leads com alta prioridade de compra.

---

## 🧱 Passo 2: Contexto e Regras

* **Ferramentas envolvidas:** Webhook (Formulário Web), OpenAI (ChatGPT API), Google Sheets e Slack.

* **Fluxo desejado:**
  1. Receber os dados do formulário via Webhook (Nome, E-mail, Cargo, Tamanho da empresa e Orçamento).
  2. Enviar a mensagem e o orçamento do lead para o nó da OpenAI analisar e classificar o lead como "Alta Prioridade", "Média Prioridade" ou "Baixa Prioridade".
  3. Salvar as informações do lead e a classificação da IA em uma planilha do Google Sheets.
  4. Se o lead for de "Alta Prioridade", enviar um alerta formatado em tempo real em um canal do Slack do time de vendas.

* **Regras importantes:**
  * Validar se o e-mail possui um formato válido antes de prosseguir.
  * Se a API da OpenAI falhar ou demorar para responder, definir a prioridade padrão como "A Revisar" e registrar na planilha sem interromper o fluxo.
  * Não disparar notificação no Slack para leads classificados como "Baixa Prioridade".

---

## 🧱 Passo 3: Prompt Final

```text
Atue como um especialista em N8N e arquitetura de automações.
Crie uma automação para receber leads de um formulário, qualificá-los via Inteligência Artificial e direcionar os contatos mais urgentes para o time comercial.

Público:
Equipe Comercial e SDRs.

Ferramentas envolvidas:
Webhook (Formulário Web), OpenAI (ChatGPT API), Google Sheets e Slack.

Fluxo:
1. Receber o payload do formulário via Webhook.
2. Filtrar/validar o formato do e-mail recebido.
3. Chamar a API da OpenAI para qualificar o lead em "Alta Prioridade", "Média Prioridade" ou "Baixa Prioridade" com base no orçamento e cargo.
4. Registrar o lead e o resultado da análise na planilha do Google Sheets.
5. Se a prioridade for "Alta Prioridade", enviar uma mensagem de alerta formatada no canal do Slack.

Regras:
- Tratar exceções/erros na API da OpenAI atribuindo a prioridade "A Revisar".
- Disparar mensagens no Slack apenas para leads de "Alta Prioridade".

Explique quais nós do N8N devem ser utilizados e a lógica de funcionamento do workflow.
