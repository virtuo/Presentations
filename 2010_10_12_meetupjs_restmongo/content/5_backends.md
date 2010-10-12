!SLIDE section
# Backends #

!SLIDE
# Interface #

  * index(RestClass, query, callback, fallback)
  * gets(RestClass, ids, callback, fallback)
  * update(RestClass, ids, data, callback, fallback)
  * delete(RestClass, ids, callback, fallback)
  * insert(RestClass, json_obj, callback, fallback)
  * clear_all(RestClass, callback, fallback)


!SLIDE
# Browser backend #

    var backend = 
      ...
      update: function(RestClass, ids, data, callback, fallback) {
        ajax('PUT', RestClass.resource + '/' + ids.join(','), 
             JSON.stringify(data), callback, fallback);
      },
      delete_: function(RestClass, ids, callback, fallback) {
        ajax('DELETE', RestClass.resource + '/' + ids.join(','), {}, 
             callback, fallback);
      },
      clear_all: function(RestClass, callback, fallback) {
        ajax('DELETE', RestClass.resource, {}, callback, fallback);
      }
    }
