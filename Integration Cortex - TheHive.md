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

- Update `thehive/application.conf` file with  

  ```
  cortex {
    servers = [
      {
        name = local
        url = "http://cortex:9001"
        auth {
          type = "bearer"
          key = "<CORTEX_API_KEY>"
        }
      }
    ]
  ```

### Continue with TheHive

- `docker-compose up -d thehive; docker-compose logs -f`
- http://localhost:9000
- Default credentials: `admin / secret` 
- Check Integration:
  - Top right -> About

##References

- https://github.com/dd-Splunk/TheHive.git
- https://medium.com/@ibrahim.ayadhi/case-management-20d8fd815ee2
- https://blog.agood.cloud/posts/2019/09/27/integrate-thehive-and-cortex/

