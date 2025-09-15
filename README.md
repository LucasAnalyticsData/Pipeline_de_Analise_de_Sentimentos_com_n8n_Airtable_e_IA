# 🤖 Projeto de Pipeline Automatizada com n8n + IA + Airtable

## 🎯 Visão Geral

Este projeto implementa uma **pipeline automatizada de classificação de sentimentos** utilizando:

- **n8n**: orquestração e automação do fluxo de trabalho.  
- **Agente de IA (LLM)**: classificação de sentimento em **Positivo | Negativo | Neutro**.  
- **Airtable**: base de dados em nuvem para coleta e organização estruturada dos resultados.  

📌 O objetivo é transformar **feedbacks brutos de usuários** em **dados estruturados e inteligentes**, prontos para dashboards, relatórios e insights de negócio.

---

## ⚖️ Componentes do Projeto

| Componente | Função | Destaques |
|------------|--------|-----------|
| **🔗 n8n** | Automação de workflows | Open Source, +200 integrações, IA Agents, condicional/looping, webhooks |
| **📊 Airtable** | Base de dados no-cloud | Interface simples como planilha, mas com poder de banco relacional |
| **🧠 Agente IA** | Classificação de sentimentos | Interpretação de feedbacks, JSON estruturado com sentimento classificado |

---

## 🛠️ Arquitetura da Pipeline

    A[📝 Formulário - Feedback] --> B[📡 Trigger n8n (Polling Airtable)]
    B --> C[🧠 Agente IA - Classificação Sentimento]
    C --> D[🔧 Parse JSON - Nó Set/Edit Fields]
    D --> E[📊 Airtable - Gravar em Base Estruturada]
    E --> F[📈 Dashboard & Insights]
```

---

## 🔄 Fluxo da Pipeline

1. ✍️ Usuário envia **feedback** via formulário (Airtable Forms).  
2. 🔔 **Trigger n8n** detecta nova entrada na tabela de origem.  
3. 🤖 **Agente IA** classifica sentimento (**Positivo / Negativo / Neutro**) e retorna JSON estruturado.  
4. 🔧 **Nó Set/Edit Fields** converte a string JSON para objeto manipulável.  
5. 📊 **Airtable - Create Record** grava feedback + classificação em uma tabela de resultados.  

---

## 🧠 Exemplo de Saída (Mensagem + JSON)


O cliente {{ $json["Nome "] }} avaliou o produto {{ $json["Produto"] }} em {{ $json["Data"] }}.
Avaliação: "{{ $json["Avaliação do Produtos"] }}"
Data/Hora: {{ $json["Carimbo de data/hora"] }}
```

**JSON Estruturado:**
```json
{
  "Nome": "Lucas Sousa",
  "Produto": "Notebook X",
  "Comentário": "Excelente desempenho e bateria",
  "Data": "2025-09-15",
  "Sentimento": "Positivo"
}
```

---

## 📊 Usos e Benefícios

| Caso de Uso | Benefício |
|-------------|-----------|
| **📈 Análise de Produto** | Identificar produtos mais elogiados ou criticados |
| **📉 Monitorar Tendências** | Detectar variações de satisfação ao longo do tempo |
| **🎯 Marketing Direcionado** | Mensagens ajustadas conforme percepção do cliente |
| **⚡ Resposta Rápida** | Ações imediatas para feedbacks negativos |

---

## ⚙️ Considerações Técnicas

- 🔑 **API Key do Airtable** precisa de escopos:  
  `data.records:read`, `data.records:write`, `schema.bases:read`.  
- 🌐 **n8n** deve rodar com acesso à internet para consumir APIs externas.  
- 🔧 **Edit Fields / Function Node** essencial para parsear saída do Agente IA.  
- ✅ Fluxo **idempotente e escalável**, pronto para múltiplos casos de uso.  

---

## 🧩 Resultado Final

✔️ Feedbacks capturados automaticamente.  
✔️ Sentimento classificado em **Positivo | Negativo | Neutro**.  
✔️ Dados salvos em **Airtable** com governança mínima.  
✔️ Pronto para **dashboards, alertas e decisões estratégicas**.  

---

## 🧠 Conclusão

Este projeto mostra como integrar **Automação + IA + Governança de Dados** de forma **simples, visual e escalável**.  
Demonstra domínio em:  
- 🔗 **Integrações low-code/no-code** (n8n + Airtable)  
- 🤖 **IA aplicada a dados de negócio**  
- 📊 **Transformação de feedbacks em insights acionáveis**  
- 🛡️ **Boas práticas de governança e documentação**  


