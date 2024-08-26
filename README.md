### Passo a passo para executarmos um SELECT no Big Query via API
#### Baixe as credenciais de serviço pela Google Cloud Platform
Acesse: [Google Cloud Platform - API](https://console.cloud.google.com/apis/dashboard)
#### Instalando módulo google-cloud-bigquery através do PIP
`pip install --upgrade google-cloud-bigquery`
#### Adicionando as credenciais nas variáveis de ambiente
```
import os
os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = 'credentials.json'
```
### Primeiro Passo: Importar as libs do Google Cloud
```
#import libraries
from google.cloud import bigquery
from google.cloud.exceptions import NotFound
```
### Segundo Passo: Criar um Client para se conectar ao big query
`client = bigquery.Client()`
### Terceiro Passo: Fazer um Select a partir do Client
```
sql_query = 'SELECT * FROM bigquery-public-data.covid19_open_data.covid19_open_data LIMIT 10'

query_job = client.query(sql_query)

for row in query_job.result():
    print(row)
```
