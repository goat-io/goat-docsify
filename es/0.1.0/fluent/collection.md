# Collections

To further operate your data, you can turn your results into Collections (Yes, Thanks again Taylor!)
Just make sure to call the collect method instead of the get()

```javascript
const Users = Fluent.model({
  properties: {
    name: "Users"
  }
})();
// Single insert example
let users = await Users.remote()
  .limit(10)
  .collect();
```

You can also turn any array into a Fluent Collection by using the collect method

```javascript
let users = [
  { name: "John", age: 20 },
  { name: "Michael", age: 40 }
];
// Single insert example
let users = Fluent.collect(users);
```

Now with the collection on hand, you can use the following operators

## average

Alias for avg()

```javascript
users.average("age");

// 30
```

## avg

```javascript
users.avg("age");

// 30
```

## Chunk

Chunk will just get all results and then separate them in smaller Arrays.

```javascript
users.chunk(1);

// [[{name: 'John', age: 20}],[{name: 'Michael', age: 40}]]
```

## Collapse

```javascript
let collection = Fluent.collect(users.chunk(1));
collection.collapse();
// [{name: 'John', age: 20}, {name: 'Michael', age: 40}]
```
