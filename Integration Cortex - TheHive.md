# Integration Cortex - TheHive

## Cortex

- Port: 9001

- Backend: ElasticSearch


## TheHive

- Port: 9000

- Backend: Cassandra


## Steps

## Start with cortex + elasticsearch

- `docker-compose up -d cortex elasticsearch ; docker-compose logs -f`

- http://localhost:9001

- Update (create DB)

- Create `admin` user

- Login as `admin`

- Create Organisation *ButterCup*

- Create user `myself` in the *ButterCup* organisation with OrgAdmin role

- Set user `myself` password

- Logout `admin` 

- Login `myself`

- Create user `thehive-cortex` user with read, analyze role

- Create  API key for user `thehive-cortex`

- Update `thehive/application.conf` file with the API key just created

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

- Configure Analyzers like Virus Total

- ...

### Continue with TheHive + Cassandra

- `docker-compose up -d; docker-compose logs -f`
- http://localhost:9000
- Default credentials: `admin / secret` 
- Check Integration:
  - Top right -> About
- Create Organisation *ButterCup*
- Create your own user `myself@splunk.com` within *ButterCup* with org-admin role
- Set password for `myself@splunk.com` 
- Create user `phantom@splunk.com`  within *ButterCup*  with read, analyze role
- Create  API key for user `phantom@splunk.com` 
  This key will be used by the corresponding Phantom application
- ...

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

## References

- https://github.com/dd-Splunk/TheHive.git
- https://medium.com/@ibrahim.ayadhi/case-management-20d8fd815ee2
- https://blog.agood.cloud/posts/2019/09/27/integrate-thehive-and-cortex/

