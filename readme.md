# Search for everything
```json
GET kibana_sample_data_logs/_search
{
  "query": {
    "match_all": {}
  }
}
```

# Match a word
```json
GET kibana_sample_data_logs/_search
{
  "query": {
    "match": {
      "extension": "css"
    }
  },
  "size": 20
}
```

# Query by IP address
```json
GET kibana_sample_data_logs/_search
{
  "from": 0, 
  "size": 200,
  "query": {
    "term": {
      "ip": "120.49.0.0/16"
    }
  }
}
```

# Get by ID
```json
GET kibana_sample_data_logs/_doc/Iqxsp3QBGneKe13DLmjI
```

# Wildcard search
```json
GET kibana_sample_data_logs/_search
{
  "from": 0, 
  "size": 20,
  "query": {
    "wildcard": {
      "referer": {
        "value": "*twitter*"
      }
    }
  }
}
```

# AND query
```json
GET kibana_sample_data_logs/_search
{
  "from": 0,
  "size": 20,
  "query": {
    "bool": {
      "must": [
        {
          "match": {
          "geo.src": "IN"
          }
        },
        {
          "match": {
            "geo.dest": "US"
          }
        },
        {
          "match": {
            "extension": "css"
          }
        },
        {
          "wildcard": {
            "machine.os": {
              "value": "*7*"
            }
          }
        }
      ]
    }
  }
}
```

# Only specific fields
```json
GET kibana_sample_data_logs/_search
{
  "from": 0,
  "size": 20,
  "_source": ["clientip", "extension", "host", "referer", "url"],
  "query": {
    "match_all": {}
  }
}
```
