---  
title: IA & ML para Transformar a Experiência dos Associados da CROOP  
theme: black  
transition: fade   # transição esmaecida entre slides  
backgroundTransition: fade  
---  

<!-- .slide: data-background-color="#1e1e1e" -->

## Visão Geral da Proposta

- **Objetivo:** aumentar a personalização no atendimento, reduzir a exposição ao risco e elevar a eficiência operacional.  
- **Benefícios esperados:** agilidade nas decisões de crédito, ofertas de produtos mais relevantes para o produtor e ganho de eficiência operacional.  
- **Escopo do projeto:** mapeamento das 5 necessidades de negócio, propostas de IA/ML, integração sistêmica, gestão de riscos e definição de KPIs.  

> **Nota de melhoria:** *Decisões mais rápidas → aumento de receita e redução de inadimplência* (adicione este bullet se desejar reforçar o valor estratégico).

---

## Principais Necessidades & Desafios

| **Desafio**                     | **Impacto Operacional / Estratégico** |
|--------------------------------|----------------------------------------|
| Avaliação de risco de crédito  | Análise manual lenta, alta taxa de inadimplência |
| Recomendação de produtos       | Oferta genérica, baixa conversão de vendas |
| Monitoramento da saúde financeira | Falta de visão preventiva e gestão reativa |
| Carga operacional documental   | Erros humanos, morosidade e retrabalho |
| Transparência e confiança      | Insegurança do associado e risco regulatório |

---

## Soluções de IA/ML (Algoritmos) & Justificativas

- 🧩 **Scoring de crédito** – *Gradient Boosting* (XGBoost / LightGBM) + **SHAP** → alta performance em tabelas estruturadas e explicabilidade.  
  > *Por que XGBoost?* Melhor desempenho em dados tabulares; *Por que SHAP?* Garante transparência regulatória.  

- 🛒 **Recomendação de produtos** – *Matrix Factorization* (SVD) com filtros híbridos → captura afinidades entre associados mesmo com dados escassos.  
  > *Por que SVD?* Lida bem com matrizes esparsas; filtros híbridos aumentam a acurácia.  

- 📄 **Extração automática de documentos** – OCR avançado (Tesseract + LayoutLM) + classificação **BERT** → transforma PDFs/scans em dados estruturados com alta acurácia.  

- 📈 **Previsão de fluxo de caixa** – *Prophet* ou **LSTM** multivariado → modela sazonalidade agrícola e variáveis macroeconômicas.  

- 🔍 **Explainable AI (XAI)** – **SHAP / LIME** e *model cards* → gera explicações locais e globais para aumentar a confiança.

---

## Integração nos Processos da CROOP

- **Arquitetura centralizada** com **API Gateway** que expõe três serviços críticos:  

  1️⃣ **Scoring de crédito** – conectado ao módulo de **Originação de Crédito**; decisão automática ou encaminhamento ao analista.  

  2️⃣ **Sistema de Recomendação** – consumo via API no site e aplicativo móvel, entrega de sugestões em tempo real.  

  3️⃣ **Motor OCR** – alimenta o **GED** (gerenciamento eletrônico de documentos) e atualiza campos de demonstrações financeiras.  

<!-- .slide: data-background-image="https://raw.githubusercontent.com/<usuario>/<repo>/main/diagrama.png" data-background-size="contain" data-background-color="#1e1e1e" -->
> **Mini‑diagrama sugerido** (inserir imagem `diagrama.png` no repo):  
> `API Gateway → (Scoring) → Sistema de Originação`  
> `API Gateway → (Recomendação) → App Mobile`  
> `API Gateway → (OCR) → GED`

---

## Roadmap, Recursos & Equipe

### Roadmap de 12 meses (Q1‑Q4)

- **Q1** – PoC OCR, coleta e limpeza de dados, definição de requisitos de negócio.  
- **Q2** – Desenvolvimento e validação do modelo de Scoring, início de piloto interno.  
- **Q3** – Implementação do motor de Recomendação, teste A/B no app, integração completa ao GED.  
- **Q4** – Go‑live pleno, treinamento dos usuários, monitoramento de KPIs e ajustes finais.  

### Equipe necessária

- 2 Data Scientists  
- 1 Engenheiro de Dados  
- 2 Engenheiros Full‑Stack  
- 1 Analista de Compliance  
- 1 Product Owner (PO)  

### Infraestrutura tecnológica

- Cloud (AWS ou GCP)  
- ML‑Ops (SageMaker ou Vertex AI)  
- Banco de Dados **PostgreSQL**  
- Orquestração/Deploy: **Airflow**, **Docker**, **Kubernetes**  

> **Sugestão visual:** usar ícones de calendário ou barras de progresso para destacar cada *milestone*.

---

## Riscos, Mitigações & Considerações Éticas

| **Risco**                | **Mitigação** |
|--------------------------|---------------|
| Qualidade dos dados      | Rotinas de validação automática, data‑profiling e auditoria de entrada. |
| Viés algorítmico         | Testes de fairness, auditoria de disparidades regionais, revisão humana de decisões críticas. |
| Segurança & LGPD         | Criptografia em trânsito e repouso, controle de acesso, consentimento explícito. |
| Arquitetura rígida       | Design modular e containers (Docker/K8s) para atualizações ágeis. |
| Falta de transparência   | Uso de **SHAP/LIME** e *model cards* para explicar cada decisão. |

**Notas adicionais**  

- Capacitação cultural das equipes para práticas responsáveis.  
- Monitoramento proativo de impactos geográficos e ajustes de modelo.

> **Dica de formatação:** mantenha a tabela em duas colunas (Risco → Mitigação) para leitura rápida.

---

## Métricas de Sucesso (KPIs) & Próximos Passos

| **KPI**                                   | **Meta (12 meses)** |
|-------------------------------------------|---------------------|
| Performance do modelo (AUC‑ROC)           | ≥ 88 % |
| NPS – Experiência do cliente              | + 10 pts |
| CTR das recomendações                     | ≥ 12 % |
| Redução da inadimplência                  | − 15 % |
| Decisões explicáveis                     | 100 % com **SHAP** |
| Tempo médio de análise de crédito         | − 40 % (até 1,5 dias) |

### Próximos passos

- Workshop de validação de requisitos (Crédito, TI, Compliance).  
- Definição do ambiente piloto (ex.: cidade de Cascavel).  
- Criação do backlog de desenvolvimento alinhado ao roadmap.  

> **Sugestão visual:** inserir um pequeno painel “Meta × Resultado Atual” que será preenchido após o piloto.

---

## 3️⃣ Estrutura de pastas recomendada (para o repo)

