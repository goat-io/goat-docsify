### Your first Model

To start using Fluent your will need to create a Fluent Model.
Every Fluent Model is a @stampit, so you can further compose it as you like.
If you only defined one connector it will be used as default, so no need to configure your models

```javascript
const Mymodel = Fluent.model({
  properties: {
    name: "Mymodel"
  }
});
```

In case you defined multiple connectors, your model will need to choose where to get its data from

```javascript
const Mymodel = Fluent.model({
  properties: {
    name: "Mymodel",
    config: {
      remote: {
        connector: "formio"
      },
      local: {
        connector: "loki"
      }
    }
  }
});
```

Onother way of defining a connector as default when using multiple connectors, is to set it on the Fluent.config

```javascript
import {Fluent} from 'fast-fluent';
import formio from '@gotlab/fluent-formio'

Fluent.config(
		    {
          REMOTE_CONNECTORS: [{
              default: true,
              name: 'formio',
              baseUrl: 'https://ydrahgggqviwquft.form.io/',
              connector: formio
          }, {...}, {...}],
        }
    );


```

# Using a Fluent Model

## Remote, Local or Merge?

Every Fluent Model can pull/push data from those 3 sources. All Fluent methods are ASYNC functions
be patient and AWAIT for them ;)

```javascript
const Mymodel = Fluent.model({
  properties: {
    name: "Mymodel"
  }
})();

// Option 1
let model = await Mymodel.remote();
// Option 2
let model = await Mymodel.local();
// Option 3
let model = await Mymodel.merge();
```

After deciding where to pull/push the data from you will have access to quite a few helpful methods

## Basic CRUD methods

### Creating

```javascript
const Mymodel = Fluent.model({
  properties: {
    name: "Mymodel"
  }
})();
const myObj = { foo: "bar", pin: "pon" };
const myArrayOfObjs = [
  { foo: "bar", pin: "pon" },
  { foo: "bar", pin: "pon" }
];
// Single insert example
let inserted = await Mymodel.remote().insert(myObj);

// Multiple insert example
let inserted = await Mymodel.remote().insert(myArrayOfObjs);
```

### Updating

All Fluent models identify records by de \_id identifier. To update a record you MUST give it the \_id

```javascript
const Mymodel = Fluent.model({
  properties: {
    name: "Mymodel"
  }
})();
// Single insert example
let updated = await Mymodel.remote().update({
  _id: "abcdefghjklmnopqrsuvwxyz",
  myNewData: "SomeNewData"
});
```

### Deleting

To remove a records you must provide its ID

```javascript
const Mymodel = Fluent.model({
  properties: {
    name: "Mymodel"
  }
})();
// Single insert example
let updated = await Mymodel.remote().remove("abcdefghjklmnopqrsuvwxyz");
```

# Reading - Query Builder

Here is where we start having fun with Fluent.
Fluent offers a powerful QueryBuilder HEAVILY inspired in Laravel (Thanks Taylor Otwell!!)

## Get all Objects (rows)

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let users = await Users.remote().get();
```

Unlike Laravel, Fluent get() Method returns and Array with the requested Objects, ready for you to use.

```javascript
users.forEach(user => console.log(user.name));
```

## Get a single Object (row)

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let user = await Users.remote().first();
```

In this case Fluent will return a single Object

```javascript
user.name;
```

## Get a list of Column Values

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let names = await Users.remote().pluck("name");
```

## Select

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let users = await Users.remote()
  .select("name", "last_name as lastName")
  .get();

// Its also possible to pass it as an Array
let users = await Users.remote()
  .select(["name", "last_name as lastName"])
  .get();
```

## Ordering, Grouping, Limit & Offset

### orderBy

```javascript
const Users = Fluent.model({
  properties: {
    name: 'Users',
  }
})()
// Single insert example
let users = await Users.remote().select('name', 'last_name as lastName').orderBy('lastName', 'asc')get()

```

### skip / take

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let users = await Users.remote()
  .select("name")
  .skip(10)
  .take(10)
  .get();
```

Is the same as

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let users = await Users.remote()
  .select("name")
  .offset(10)
  .limit(10)
  .get();
```
