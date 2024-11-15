# ELT de Dados do SteamDB Sales com BigQuery e Google Sheets

Este projeto realiza um processo de **ELT (Extract, Load, Transform)** dos dados de promoções de jogos disponíveis no site [SteamDB Sales](https://steamdb.info/sales/). 

O fluxo automatiza a extração de dados com **Playwright**, realiza a carga no **Google BigQuery**, e finalmente disponibiliza os dados em uma **[planilha do Google Sheets](https://docs.google.com/spreadsheets/d/1V8AsvW6Z6zQCE5Gedhbn-yQFxjeYRe3ynlyXXpZ3XPw/edit?usp=sharing)** para consulta e visualização.

---

## 📋 **Fluxo do Processo**

### 1. **Extração dos Dados**
- **Tecnologia Utilizada**: [Playwright](https://playwright.dev/).
- Os dados da página de promoções do SteamDB foram extraídos automaticamente.
- Após a extração, os dados foram salvos localmente em arquivos no formato CSV.

### 2. **Carga no BigQuery**
- Os arquivos CSV foram carregados em um dataset no **Google BigQuery**.
- Foi configurada a criação automática de tabelas com base no schema detectado nos arquivos CSV.
- O BigQuery agora contém os dados centralizados e prontos para consultas SQL.

### 3. **Transformação e Disponibilização no Google Sheets**
- Os dados do BigQuery foram lidos e carregados em uma **planilha do Google Sheets**.
- Caso a planilha ou aba não existissem, elas foram criadas dinamicamente pelo script.

---

## 📦 **Estrutura do Projeto**

```plaintext
project/
|
├── beanalytics_venv        # Diretório onde o ambiente virtual é criado (diretório não versionado no Git)
│
├── configs/                # Arquivos de credenciais (não versionados no Git)
│   └── credentials.json    # Arquivo com as credenciais de acesso ao BigQuery
│
├── jobs/                    # Diretório onde os Jupyter Notebooks estão salvos
│   ├── extract.ipynb       # Extração de dados usando Playwright
│   ├── load.ipynb          # Carga dos dados no Google BigQuery
│   └── transform.ipynb     # Exportação para o Google Sheets
│
├── raw/                    # Diretório onde os arquivos CSV são salvos (não versionados no Git)
│   ├── steam_sales_1.csv
│   ├── steam_sales_2.csv
│   └── ...
│
├── .gitignore              # Lista de arquivos ignorados pelo Git
├── 00_install_requirements # Script bash para instalação do pip e venv
├── 01_create_venv          # Script bash para criação do ambiente virtual e instalação do pacotes necessários
├── README.md               # Documentação do projeto
└── requirements.txt       # Dependências do projeto
```

## 🚀 Pré-requisitos

### 1. Sistema Linux

### 2. Python 3.8+
Certifique-se de ter o Python instalado. Você pode verificar a versão executando:
```bash
python3 --version
```

### 3. Execução dos scripts Bash
```bash
./00_install_requirements
```
```bash
./01_create_venv
```