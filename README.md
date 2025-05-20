# 🔍 Azure AI Search Index UI — Ingestão, Índices Inteligentes e Exploração de Dados

## 📘 Introdução

O **Azure AI Search** é um serviço de pesquisa em nuvem com recursos de inteligência artificial que permite transformar dados não estruturados em **informações pesquisáveis**, integrando **IA Generativa**, **machine learning** e **indexação semântica**.

A ferramenta **Search Index UI** facilita a ingestão, indexação e consulta de conteúdo por meio de uma interface visual e intuitiva.

---

## 🔄 Ingestão de Conteúdo para IA

### 🔷 O que é?

A **ingestão de conteúdo** é o processo de conectar fontes de dados ao Azure AI Search para que o conteúdo seja analisado, enriquecido e indexado.

### 📥 Fontes Comuns de Ingestão:

| Fonte                     | Descrição                               |
|--------------------------|-------------------------------------------|
| Azure Blob Storage       | Arquivos PDF, DOCX, JSON, HTML, etc.     |
| Azure SQL Database       | Dados relacionais estruturados           |
| SharePoint Online        | Documentos organizacionais               |
| Data Lake                | Dados em escala corporativa              |

### ⚙️ Pipelines de Enriquecimento com AI

Durante a ingestão, o Azure pode aplicar **Habilidades Cognitivas** como:

- Extração de texto e metadados
- OCR (Reconhecimento óptico de caracteres)
- Detecção de linguagem
- Análise de sentimento e entidades
- Divisão em chunks para IA generativa (semântica)

---

## 🧠 Criação de Índices Inteligentes

### 🔷 O que é um Índice?

Um **índice de pesquisa** funciona como um catálogo que armazena representações organizadas dos dados, permitindo pesquisas rápidas e relevantes.

### 🛠️ Como criar um índice no UI:

1. Acesse o **Azure AI Search** via [portal.azure.com](https://portal.azure.com)
2. Crie um recurso de **Azure AI Search**
3. Use o **Assistente de Criação de Índice** (Index wizard):
   - Escolha a fonte de dados
   - Configure o *skillset* (opcional)
   - Defina campos do índice (chave, texto, filtro, faceta)
   - Inicie a indexação

---

### ✨ Tipos de Campos em um Índice:

| Campo     | Função                         |
|-----------|--------------------------------|
| Key       | Identificador único            |
| Searchable | Pode ser pesquisado em texto  |
| Filterable | Suporta filtros e facetas     |
| Sortable  | Permite ordenação              |
| Retrievable | Pode ser retornado via query |

---

### 💡 Indexação Semântica (Semantic Search)

Com a IA integrada, o Azure permite:

- **Compreensão de intenção**, não apenas por palavras-chave
- Classificação semântica de resultados
- **Respostas naturais** via integração com modelos de linguagem (RAG: Retrieval-Augmented Generation)

---

## 🔎 Exploração na Prática: Pesquisa Inteligente

### 1. Usando a Search UI

Após criar o índice:

- Acesse a **Search Explorer** no portal
- Teste buscas com palavras-chave ou frases naturais
- Visualize os documentos retornados
- Filtre por metadados, categorias e facetas

### 2. Integração com Aplicações (SDK/API)

```bash
az search query --service-name meu-servico-search \
  --index-name indice-documentos \
  --search "contrato confidencial"

### Ou via SDK:

from azure.search.documents import SearchClient
from azure.core.credentials import AzureKeyCredential

search_client = SearchClient(
    endpoint="https://<servico>.search.windows.net",
    index_name="documentos",
    credential=AzureKeyCredential("<chave>")
)

results = search_client.search("relatório financeiro 2024")
for result in results:
    print(result["titulo"], result["resumo"])

