# Aplicativo Web com Relatório Climático Orquestrado com Airflow

Este é um aplicativo web desenvolvido com Streamlit e cujos dados são alimentados por um pipeline orquestrado com Airflow, responsável por extrair e processar informações climáticas da [Visual Crossing Weather API](https://www.visualcrossing.com/weather-api).

### Pré-requisitos

Certifique-se de ter o Python 3.11 instalado em seu sistema.

### Instalação

Clone o repositório, crie o ambiente virtual e instale as dependências:

```bash
# Clonar o repositório
git clone https://github.com/jorgeplatero/climate_report_airflow.git
cd climate_report_airflow

# Criar o ambiente virtual (venv)
python -m venv venv

# Ativar o ambiente virtual
# No Windows:
venv\Scripts\activate
# No Linux/Mac:
source venv/bin/activate

# Instalar as dependências
pip install -r requirements.txt
```

Instale o Apache Airflow:

```bash
export AIRFLOW_VERSION=3.1.5
export PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
export CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"

pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
```

### Como Rodar a Aplicação

Com o ambiente virtual ativado, execute os comandos abaixo.

Para iniciar o dashboard Streamlit:

```bash
streamlit run app.py
```

Para iniciar o orquestrador Airflow localmente:
```bash
airflow standalone
```

### Funcionalidades

*   **Orquestração com Airflow:** Agendamento e execução confiável de tarefas de extração, transformação e carregamento de dados (ETL).
*   **Integração com API:** Captura automatizada de dados meteorológicos em tempo real via Visual Crossing Weather API.
*   **Interface Interativa:** Visualizações dinâmicas e monitoramento de progresso através de um relatório intuitivo no Streamlit.

### Tecnologias

| Componente | Tecnologia | Versão (Especificada) | Descrição |
| :--- | :--- | :--- | :--- |
| **Frontend/App** | **Streamlit** | `1.32.2` | Framework para criação do dashboard interativo. |
| **Orquestração** | **Apache Airflow** | `3.1.5` | Plataforma para gerenciamento e agendamento de pipelines. |
| **Análise de Dados** | **Pandas** | `2.2.1` | Manipulação e tratamento de dados estruturados. |
| **Visualização** | **Plotly** | `5.20.0` | Criação de gráficos dinâmicos e interativos. |
| **Processamento** | **NumPy** | `1.26.4` | Computação numérica e suporte a arrays. |
| **Linguagem de Programação** | **Python** | `>=3.11` | Linguagem base do projeto. |
| **Gerenciamento** | **Venv/Pip** | `-` | Ferramentas padrão para ambientes virtuais e pacotes. |

### Integrações

O fluxo de dados é alimentado pela API da **Visual Crossing**, garantindo que as previsões e dados históricos exibidos no dashboard estejam sempre atualizados conforme o cronograma definido no Airflow.

### Deploy

O dashboard está disponível publicamente via Streamlit Cloud.

Link para o aplicativo: [https://climatereportairflow.streamlit.app/](https://climatereportairflow.streamlit.app/)
