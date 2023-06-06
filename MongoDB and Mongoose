require('dotenv').config();
const mongoose = require('mongoose');//1 (Step 1)
const { Schema } = require('mongoose');//2 (Step 1)

//2 (Step 2: Defininfing Schema)
const personSchema = Schema({
  name: {
    type: String,
    required: true
  },
  age: Number, 
  favoriteFoods: [String]
})

//2 (Step 3: Defining Person)
const Person = mongoose.model('Person', personSchema)

mongoose.connect(process.env.MONGO_URI, { useNewUrlParser: true, useUnifiedTopology: true });//1 (Step 2)


//3 (Step 3: Creating document instance)
const createAndSavePerson = (done) => {
  const person = new Person({
    name: 'Bhekizwe',
    age : 38,
    favoriteFoods: ['chips', 'chicken']
  });

//3 (Step 4: Using Node callback function)
  person.save(function(err, data) {
    if (err) {
      done(err);
      return;
    }
    console.log(data);
    done(null, data);
  });
//  done(null /*, data*/);
};

//4 (Step1: Creating ManyPeople array)
const arrayOfPeople = [
  {name: 'James', age: 36, favoriteFoods: ['fat cakes']},
  {name: 'Terry', age: 39, favoriteFoods: ['vodka']},
  {name: 'Jack', age: 37, favoriteFoods: ['pie']}
];

//4 (Step 2: Create ManyPeople Function and console)
const createManyPeople = (arrayOfPeople, done) => {
  Person.create(arrayOfPeople, (err, people) => {
    if (err) {
      done(err);
      return;
    } else {
      console.log(data);
      done(null, data);
  }
  });
};

//4
const findPeopleByName = (personName, done) => {
  Person.find({ name: personName }, (err, data) => {
    if (err) {
      done(err);
      return;
    } else {
      console.log(data);
      done(null, data);
  }
  });//done(null /*, data*/);
};

//5
const findOneByFood = (food, done) => {
  Person.findOne({ favoriteFoods: food }, (err, data) => {
    if (err) {
      done(err);
      return;
    } else {
      console.log(data);
      done(null, data);
  }
  });//done(null /*, data*/);
};

//6
const findPersonById = (personId, done) => {
  Person.findById(personId, (err, data) => {
    if (err) {
      done(err);
      return;
    } else {
      console.log(data);
      done(null, data);
  }
  });//done(null /*, data*/);
};

//7 (Part 1: Edit)
const findEditThenSave = (personId, done) => {
  const foodToAdd = "hamburger";
  Person.findById(personId, (err, person) => {
    if (err) {
      done(err);
      return;
    }
//7 (Part 2: Save)
    console.log(person);
    person.favoriteFoods.push(foodToAdd);
    person.save((err, savedDoc) => {
      if (err) {
        done(err);
        return;
      }
      console.log(savedDoc);
      done(null, savedDoc);
    });
  });
};

//8
const findAndUpdate = (personName, done) => {
  const ageToSet = 20;
  Person.findOneAndUpdate(
    { name: personName }, // filter to find the document
    { age: ageToSet }, // object specifying the fields to update
    { new: true }, // options object to return the updated document
    (err, data) => {
      if (err) {
        done(err);
        return;
      }
      console.log(data);
      done(null, data);
    }
  );
};//The third arguement tells Mongoose to return to the original);

//9
const removeById = (personId, done) => {
  Person.findByIdAndRemove(personId, (err, data) => {
    if (err) {
      done(err);
      return;
    }
    console.log(data);
    done(null, data);
  });
};//Similar "return to original" condition in #8);

//10
const removeManyPeople = (done) => {
  const nameToRemove = "Mary";
  Person.remove({ name: nameToRemove}, (err, data) => {
    if (err) {
      done(err);
      return;
    }
    console.log(data);
    done(null, data);
  });
};

//11
const queryChain = (done) => {
  const foodToSearch = "burrito";
  Person
    .find({ favoriteFoods: foodToSearch })
    .sort({ name: 1 })
    .limit(2)
    .select('name favoriteFoods')
    .exec((err, data) => {
      if (err) {
        done(err);
        return;
      }
      console.log(data);
      done(null, data);
    });
};

/** **Well Done !!**
/* You completed these challenges, let's go celebrate !
 */

//----- **DO NOT EDIT BELOW THIS LINE** ----------------------------------

exports.PersonModel = Person;
exports.createAndSavePerson = createAndSavePerson;
exports.findPeopleByName = findPeopleByName;
exports.findOneByFood = findOneByFood;
exports.findPersonById = findPersonById;
exports.findEditThenSave = findEditThenSave;
exports.findAndUpdate = findAndUpdate;
exports.createManyPeople = createManyPeople;
exports.removeById = removeById;
exports.removeManyPeople = removeManyPeople;
exports.queryChain = queryChain;
