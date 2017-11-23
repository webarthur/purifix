# purifix
Sanitize functions for node

```javascript
var app = express()
var purify = require('purifix')

app.post('/users/:id', function (req, res, next) {
  var user_id = purifix.objectId(req.params.id),
  var payload = {
    name: purifix.string(req.body.name).trim(),
    age: purifix.int(req.body.age, 0),
    working: purifix.bool(req.body.working, false),
  }

  // validation
  ...

  // mongodb update
  User.update({_id: user_id}, {$set: payload}, function () {
    // callback
    ...
  })
})
```

## API

* `.string(rawValue, defaultValue)`
* `.objectId(rawValue, defaultValue)`
* `.email(rawValue, defaultValue)`
* `.url(rawValue, defaultValue)`
* `.bool(rawValue, defaultValue)`
* `.boolean(rawValue, defaultValue)`
* `.isTrue(rawValue, defaultValue)`
* `.ifFalse(rawValue, defaultValue)`
* `.number(rawValue, defaultValue)`
* `.int(rawValue, defaultValue)`
* `.interger(rawValue, defaultValue)`
* `.float(rawValue, defaultValue)`
