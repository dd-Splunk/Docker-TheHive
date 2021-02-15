#Integration Cortex - TheHive

##Cortex

Port: 9001

Backend: ElasticSearch

##TheHive

Port: 9000

Backend: Cassandra

## Steps

### Check elasticsearch

```
curl -X GET "localhost:9200/_cat/health"
```

<timestamp> elasticsearch green 1 1 0 0 0 0 0 0 - 100.0%

```
curl -X GET "localhost:9200/_cat/nodes"
```

```
curl -X GET "localhost:9200/_cat/shards"
```

```
curl -X GET "localhost:9200/_cat/indices?v"
```

## Start with cortex + elasticsearch

- `docker-compose up -d cortex elasticsearch ; docker-compose logs -f`

- http://localhost:9001

- Update (create DB)

- Create Admin user

- Login as admin

- Create Organisation ButterCup

- Create user dd in the ButterCup organisation with OrgAdmin role

- Set user dd password

- Logout admin / login dd

- Create user thehive-cortex with read, analyze role

- Create Cortex API Key for user thehive-cortex

- Update `.env` file with  

  ```
  CORTEX_KEY=<Cortex API Key>
  ```

  

### Continue with TheHive + Cassandra

- `docker-compose up -d thehive cassandra ; docker-compose logs -f`
- http://localhost:9000
- Update (create DB)
- Update 

xxx

##References

https://github.com/dd-Splunk/TheHive.git

https://medium.com/@ibrahim.ayadhi/case-management-20d8fd815ee2

