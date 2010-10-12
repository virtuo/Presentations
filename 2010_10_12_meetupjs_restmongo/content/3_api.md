!SLIDE section
# API #

!SLIDE

# Create and save an object #

    var lilly = new R.Person({firstname: "Lilly"});
    lilly.save(function() {
      console.log("Lilly saved in DB with id " + lilly.id());
    }, function(err) {
      // do something with the error.
    });


!SLIDE
# Get one or more objects #

    R.Person.get({
     ids: lilly.id()
    }, function(lilly2){
      // lilly and lilly2 are the same
    });


!SLIDE
# Search #

    R.Person.index({
     query: {firstname: "Lilly"}
    }, function(objs){
      var lilly = objs[0];
    });

!SLIDE
# Delete #

    lilly.delete_(function(){
      console.log('Lilly deleted from DB!');
    }, function(err) {
      console.log('You can not delete Lily!');
    });

    R.Person.clear_all(function() {
      // All Person objects removed from DB
    });

!SLIDE
# References #

    var harry = new R.Person({firstname: "Harry", mother: lilly});
    harry.save(function() {
      // Only the id of Lilly has been saved in harry.mother in DB
    });

!SLIDE
# Massive updates #

    R.Person.update({
      ids: [lilly.id(), harry.id()], 
      data: {firstname: 'anonymous'}
    }, function() {
      console.log("Voldemort cannot find them anymore...");
    });

!SLIDE
# Massive update / creation #

    var p1 = new R.Person({firstname: 'Hermione'});
    var p2 = new R.Person({firstname: 'Ron'});
    R.save([p1, p2], function() {
      console.log('Now Harry has friends.')
    }, function(error) {
      console.log('Harry has no friends, because of ', error);
    });


!SLIDE
# Distinct #

    var p1 = new R.Person({firstname: 'Pierre'});
    var p2 = new R.Person({firstname: 'Ori'});
    var p3 = new R.Person({firstname: 'Pierre'});
    R.save([p1, p2, p3], function() {
      R.Person.distinct({key: 'firstname'}, function(vals) {
        console.log(vals); // ['Pierre', 'Ori']
      });
    });

!SLIDE
# Clear the cache(s) #

    R.Person.clear_cache(); // cache associated with Person objects
    
    R.clear_caches(); // caches of every object

