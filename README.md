# Exemplo: execute o Airflow 2.0 com Celery via docker-compose

Exemplo mostrando como executar o Airflow 2.0 (usando a imagem docker oficial) com docker-compose.

Observe que o Airflow 2.0 conterá alterações incompatíveis com versões anteriores,
por exemplo, encontrei as seguintes alterações de CLI de fluxo de ar:

|    Antes   |    Agora      |
|------------|---------------|
| initdb     | db init       |
| flower     | celery flower |
| worker     | celery worker |
|----------------------------|

Na primeira execução, você precisará inicializar o banco de dados, o que pode ser feito executando este comando. Você só precisa
para executar isso uma vez ou toda vez que você excluir os contêineres/volumes - os dados devem persistir entre a parada e início do contêiner.
```
docker-compose run webserver db init
docker-compose run webserver users create -r Admin -u admin -e admin@example.com -f admin -l user -p admin
```
Depois execute o comando abaixo
```
docker-compose up
```
