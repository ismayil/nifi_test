## Sample flow
**Group1:**
1. Read file from FTP and push both Kafka and FileWriter\
2. FileWriter also send HTTP request if file saved successfully

**Group2:**
1. Receive request by HttpServer
2. Publish to Kafka topic


```
group1 and group2 connected virtually by httpClient and HttpServer. it means group2 can receive request either from any external client or
from group1
```
