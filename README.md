# Aplicativo Web com Relatório Climático Orquestrado com Airflow

Este é um aplicativo web desenvolvido com Streamlit e cujos dados são alimentados por um pipeline orquestrado com Airflow, responsável por extrair e processar informações climáticas da API disponibilizada pela [Visual Crossing](https://www.visualcrossing.com/).

### Pré-requisitos

Certifique-se de ter o Python 3.11 instalado em seu sistema.

Instale o suporte ao ambiente virtual:

```bash
sudo apt update && sudo apt install python3.11-venv
```

### Instalação

Clone o repositório, crie o ambiente virtual e instale as dependências:

```bash
#clonar o repositório
git clone https://github.com/jorgeplatero/climate_report_airflow.git
cd climate_report_airflow

#criar o ambiente virtual
python -m venv venv

#ativar o ambiente virtual
source venv/bin/activate

#instalar as dependências
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

| Componente | Tecnologia | Versão | Descrição |
| :--- | :--- | :--- | :--- |
| **Frontend/App** | **Streamlit** | `1.32.2` | Framework utilizado para o desenvolvimento do aplicativo web |
| **Orquestração** | **Apache Airflow** | `3.1.5` | Framework para gerenciamento e agendamento de pipelines |
| **Análise de Dados** | **Pandas** | `2.2.1` | Biblioteca utilizada para manipulação de dados |
| **Visualização** | **Plotly** | `5.20.0` | Biblioteca para criação de gráficos dinâmicos e interativos |
| **Linguagem** | **Python** | `>=3.11` | Linguagem de programação base para o desenvolvimento dos scripts |
| **Gerenciamento** | **Venv** | `-` | Gerenciador de pacotes e ambientes virtuais utilizado para garantir a reprodutibilidade das dependências do projeto |

### Integrações

O fluxo de dados é alimentado pela [Weather API](https://www.visualcrossing.com/weather-api), garantindo que as previsões e dados históricos exibidos no dashboard estejam sempre atualizados conforme o cronograma definido no Airflow.

### Deploy

O aplicativo web está disponível via Streamlit Cloud.

Link para o aplicativo: [https://climatereportairflow.streamlit.app/](https://climatereportairflow.streamlit.app/)
