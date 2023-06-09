# Quiz 2 (KsqlDB)
## Member
1. 6420412006 Natthawit Chairatanatrai 
2. 6420412008 Sirirat Lueprasert 
3. 6420412009 Sapon Sarub 
4. 6420412010 Natnicha Sabdasen 
5. 6510412009 Jirapat Atikomtrirat


## Follow these step

1. Download the folder Quiz2 and extract files

2. Open Command Prompt at folder Quiz2 directory and run the following command:

```sh

$ docker-compose up

```

3. Once the services are running, open another tab and run file 

```sh

$ python CSV_PostgreSQL.py

```

4. On the same tab, log into the ksqlDB CLI using the following command:

```sh

$ docker-compose exec ksqldb-cli  ksql http://ksqldb-server:8088

```

If you see a `Could not connect to the server` error in the CLI, wait a few seconds and try again. ksqlDB can take several seconds to start.

5. run the ksqlDB statements to setup the connectors using the following command:

```sql

ksql> RUN SCRIPT '/etc/sql/connector.sql';

```

6. Once the connectors are created, run the following command:

```sql

ksql> RUN SCRIPT '/etc/sql/all.sql';

```

7. Therefore, verifying that the connectors worked simply involves checking to see if the Postgres data made it's way to Elasticsearch. We can verify by opening a third tab, and running a simple query against the Elasticsearch container:

```sh

$ docker-compose exec elasticsearch curl -XGET "localhost:9200/topic3/_search?format=json&pretty"

```

8. Once you're finished, tear everything down using the following command:

```sh

docker-compose down

```

## Visualization

![Weight person with nutrition checking by gender](https://user-images.githubusercontent.com/115805661/236526320-a7165dca-eb06-4cfe-b3e2-8bfd7b1d8ab6.png)
https://public.flourish.studio/visualisation/13657815/

![snapshot-1683308332085](https://user-images.githubusercontent.com/115805661/236528011-55306cf5-8236-4dc9-88f2-b0d62e948418.png)
https://public.flourish.studio/visualisation/13658321/
