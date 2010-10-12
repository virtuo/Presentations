!SLIDE section
# Browser #

!SLIDE
# Principle #

  * Same core code
    * Only back end code is changing
  * Same API ('distinct' not available)
    * Same tests
  * Uses nodetk to make node modules available to the browser


!SLIDE
# Schema augmented #

    schema = {
      "Person": {
        resource: "/people",
        schema: {
          id: "Person",
          description: "someone, blablabla",
            type: "object",
           
            properties: {
              ...
            }
          }
        }
      }

!SLIDE
# Server augmented #

    var http = require("http"),
      , rest_mongo = require('rest-mongo/core')
      , mongo_backend = require('rest-mongo/mongo_backend')
      , schema = require('rest-mongo/tests/schema').schema
      ;
  
    var backend = mongo_backend.get_backend({db_name: 'rest-mongo'});
    var RFactory = rest_mongo.getRFactory(schema, backend);
  
    var server = http.createServer();
    rest_server.plug(server, schema, RFactory);
    // ... do whatever you want with the server
    server.listen(8549);




!SLIDE
# Example #

  cf. [github.com/AF83/rest-mongo/blob/master/src/rest-mongo/browser_tests/demo.html](http://github.com/AF83/rest-mongo/blob/master/src/rest-mongo/browser_tests/demo.html)
  



