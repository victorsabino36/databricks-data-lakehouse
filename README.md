# Databricks Data Lakehouse 

## 📖 Visão Geral
Este projeto implementa uma arquitetura de **Data Lakehouse** completa utilizando a plataforma **Databricks**. O objetivo é transformar dados brutos valiosas para negócio, seguindo a **Arquitetura Medalhão** para garantir a qualidade, linhagem e governança dos dados através do formato **Delta Lake**.

## 🏗️ Arquitetura Medalhão
O pipeline está estruturado em três camadas lógicas para garantir a integridade dos dados:

1. **Bronze (Raw):** Ingestão dos arquivos CSV originais para tabelas Delta. Mantém a fidelidade total aos dados de origem, incluindo metadados de carga.
2. **Silver (Cleaned):** Limpeza de dados, tratamento de nulos, deduplicação e normalização de tipos (ex: conversão de strings para timestamps).
3. **Gold (Business):** Agregações de negócio, KPIs e tabelas dimensionais prontas para consumo por ferramentas de BI.

## 🛠️ Stack Tecnológica
* **Processamento:** PySpark.
* **Transformação SQL:** Databricks SQL.
* **Armazenamento:** Delta Lake (Transações ACID, Schema Enforcement e Time Travel).
* **Versionamento:** Databricks Git Folders (Repos).

## 🚀 Etapas Implementadas 

### 1. Extração (Camada Bronze)
* **Extração:** Ingestão de dados de diversas fontes e formatos.
* **Carga:** Escrita dos dados em formato Delta.
* **Transformação Inicial:** Criação de `Views` em SQL para exploração rápida e padronização de esquemas iniciais.

### 2. Tratamento de Dados (Camada Silver)
* **Normalização Schema:** Conversão de colunas para tipo de dados correto e padronizacao no nome das colunas.
* **Qualidade:** Implementação de regras para evitar o erro de *Schema Mismatch* e e duplicidade dos dados `Data Quality`.

### 3. Calculo de KPIs e aplicação da regra de negocio (Camada Gold)
* **Business Intelligence:** criar novos indicadores e tabelas e disponibilizar para ferramentas da dataviz.

## 📁 Estrutura do Repositório
```text
├── pipeline/
│   ├── olist # Ingestão de dados de um Ecommerce
│   │    ├── bronze 
│   │    ├── silver
│   │    ├── gold
│   │    ├── setup # criação do schema
│   │
│   ├── 02_conjunto_dados 
│   └── 03_conjunto_dados       
├── data/
│   └── landing/                     # Localização dos arquivos CSV brutos
└── README.md
