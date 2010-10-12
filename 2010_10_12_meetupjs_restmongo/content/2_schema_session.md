!SLIDE section
# Usage #

!SLIDE
# General steps #

  1. Describe you data schema
  2. Create a session factory (RFactory)
  3. Get a session to work with (R)
  4. Play with R and its objects
    

!SLIDE
# 1. Data schema #

    var schema = {
      "Person": {
        schema: {
          id: "Person",
          description: "someone, blablabla",
          type: "object",
           
          properties: {
            firstname: {type: "string"},
            friends: {type: "array", items: {"$ref": "Person"}},
            mother: {"$ref": "Person"}
          }
        }
      }
    };


!SLIDE
# 2/3. Session #

    var http = require("http")
      , rest_mongo = require("rest-mongo")
      ;
    
    var RFactory = rest_mongo.getRFactory(schema, "db_name");

    http.createServer(function (req, res) {
      res.writeHead(200, {'Content-Type': 'text/plain'});

      var R = RFactory();
      ... // Do something with R

      res.end('Hello World\n');
    }).listen(8080, "127.0.0.1");

    
