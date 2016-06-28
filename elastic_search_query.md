GET _search
{
  "query": {
    "match_all": {}
  }
}

# SEARCH ALL DOCS IN INDEX 
GET /library/books/_search

POST /library

PUT /library/books/1
{
  "title":"Elastic Search 1",
  "author":"Kuldeep",
  "detail":{
    "price":100.0
  }
}

GET /library/books/1

# UPDATE OPERATIONS
##Elastic search updating a single doc
POST /library/books/1/_update
{
  "doc":{
    "detail":{
      "mrp":150.0
    }
  }
}

# BULK OPERATOINS
##Elastic search bulk operations

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
