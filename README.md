# Require Fields

An express middleware that makes it easy to check that certain values are present in a request.

### Getting Started
First you need to make sure that body parser is being used by your express app.

```javascript
app.use(bodyParser.json())
```

Then all you have to do is require this package and use it in your routes!

```javascript
var requireFields = require('require-fields')

app.route("login").post(
  requireFields([
    "email",
    "password"
  ]),
  //other middleware / your code
)
```

Notice how I passed an array of string values into the middleware. These strings are the fields that the middleware will check for. If a request comes in that's missing one of those fields, it will send a `400 Bad Request`. The json of the response will look like this:

```json
{
  "message" : "Missing required fields",
  "missingFields" : [
    "missingField1",
    "missingField2"
  ]
}
```
