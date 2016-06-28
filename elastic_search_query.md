# CREATING INDEX
POST /library

# SEARCH ALL DOCS IN INDEX 
```json
GET _search
{
  "query": {
    "match_all": {}
  }
}
```
### Above will give all indexes' result.

GET /library/books/_search

###Search queries with multiple clauses like (where in sql)
```json
GET /library/books/_search
{
  "query": {
    "bool": {
      "should or must": [
        {
          "match": {
            "title": "Effective"
          }
        },{
          "match_phrase": {
            "title": "The future"
          }
        }
      ]
    }
  },
  "highlight": {
    "fields": {
      "title": {}
    }
  }
}
```
### Filter results with some range or values
```json
GET /library/books/_search
{
  "query": {
    "filtered": {
      "filter": {
        "range": {
          "price": {
            "gte": 200,
            "lte": 999
          }
        }
      }
    }
  }
}
```

# CREATE SINGLE DOCUMENT
```json
PUT /library/books/1
{
  "title":"Elastic Search 1",
  "author":"Kuldeep",
  "detail":{
    "price":100.0
  }
}
```

# FETCH SINGLE DOCUMENT
GET /library/books/1

# UPDATE OPERATIONS
##Elastic search updating a single doc
```json
POST /library/books/1/_update
{
  "doc":{
    "detail":{
      "mrp":150.0
    }
  }
}
```

# BULK OPERATOINS
##Elastic search bulk operations
```json
POST /library/books/_bulk
{"index":{"_id":2}}
{"title":"Game Of Thrones 1","price":150.0}
{"index":{"_id":3}}
{"title":"Harry Potter and Socer's Series 1","price":250.0}
{"index":{"_id":4}}
{"title":"Rejection Therapy","price":499.0}
{"index":{"_id":5}}
{"title":"Elon Must, The Future is bright","price":150.0}
{"index":{"_id":5}}
{"title":"Effective Java","price":1500.0}
{"index":{"_id":6}}
{"title":"Chanakaya Niti","price":0.0}
{"index":{"_id":7}}
{"title":"Marhrita With Straw","price":999.0}
{"index":{"_id":7}}
{"title":"Steve Jobs","price":299.0}
{"index":{"_id":1}}
{"title":"The Vinci Code, Dan Brown","price":310.0}
```

# MAPPINGS

##Check Mappings of an Index

GET /library/_mappings

##Put a new field using mapping.
```json
PUT /library/books/_mapping
{
  "books":{
    "properties":{
      "ISBN":{
        "type":"string"
      }
    }
  }
}
```
## Specify analyser using mapping.
```json
PUT /library/books/_mapping
{
  "books":{
    "properties":{
      "ISBN":{
        "type":"string",
	"analyzer":"english"
      }
    }
  }
}
```


