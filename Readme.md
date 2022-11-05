## Installation
1. Clone repository
2. Run ```docker compose up```  (it takes 3-4 minutes due to cluster election)
3. Open browser http://localhost:8091/nifi/

This creates all necessary services (nifi, registry, kafka, ftp, postgre, redis, zookeeper)

## Run test
**Test flow over ftp**

upload any .txt file to ftp root folder (host=localhost:21,user=username,pass=mypass)

**Test http request**
send http request to ```localhost:5055/localListener```
json body ```{"name":"TestName", "age":33,height:"183"}```

at the end we have file in the ```outputfolder``` and content in corresponding ```kafka topic```.

**TODO**
* add convertorServices such as FileContent to Line Collection or CSV to JSON
* convert record to sql columns and add DB connection as component of flow

**Basic perf result:**

| Node Count | mb/sec | count/sec|
|---|---|---|
| 1 | 96MB | 472_000 |
| 4 | 320MB | 1_200_000 |
| 8 | 530MB | 1_987000 |
| 16 | ~ 520MB | ~ 1_900000 |