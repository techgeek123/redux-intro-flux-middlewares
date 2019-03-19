# Route Middleware and Testing

## Learning Competencies
- Cleaning API Routing using Middleware
- Testing API Routes

## Overview

### Route Middleware to Protect API Routes

At this point, we have 3 routes defined on our API routes (/api/authenticate, /api, and /api/users). Let's create route middleware to protect the last 2 routes. We won't want to protect the /api/authenticate route so what we'll do is place our middleware beneath that route. Order is important here.

Let's take a look at the code:

```js
// API ROUTES -------------------

// get an instance of the router for api routes
var apiRoutes = express.Router(); 

// route to authenticate a user (POST http://localhost:8080/api/authenticate)
...

// route middleware to verify a token
apiRoutes.use(function(req, res, next) {

  // check header or url parameters or post parameters for token
  var token = req.body.token || req.query.token || req.headers['x-access-token'];

  // decode token
  if (token) {

    // verifies secret and checks exp
    jwt.verify(token, app.get('superSecret'), function(err, decoded) {      
      if (err) {
        return res.json({ success: false, message: 'Failed to authenticate token.' });    
      } else {
        // if everything is good, save to request for use in other routes
        req.decoded = decoded;    
        next();
      }
    });

  } else {

    // if there is no token
    // return an error
    return res.status(403).send({ 
        success: false, 
        message: 'No token provided.' 
    });

  }
});

// route to show a random message (GET http://localhost:8080/api/)
...

// route to return all users (GET http://localhost:8080/api/users)
...

// apply the routes to our application with the prefix /api
app.use('/api', apiRoutes);
```

We are using the jsonwebtoken package again, but this time we are going to verify the token that was passed in. It is important that our secret used here matches the secret that was used to create the token. We are also making sure to send the right HTTP response code as 403 forbidden and our user was not authenticated to view any data.

If everything looks good the token was able to be verified, we'll take the information that came out of the token and pass it to the other routes in the req object.

### Testing Our Middleware

We have built our middleware that our Node application will run through before it gets to the routes that we want authenticated.

Let's go into POSTman again and try to access both routes without passing a token.

This is our route without the token just accessing the base api route of http://localhost:8080/api

Now let's pass in the token that was created before in our ``HTTP`` header as ``x-access-token`` accessing the users list at http://localhost:8080/api/users

We can also pass it in as a URL parameter by going to: 

    http://localhost:8080/api/users?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NDY1MDViMDFmYTAzYmUwMTUxMDYwOWIiLCJuYW1lIjoiTmljayBDZXJtaW5hcmEiLCJwYXNzd29yZCI6InBhc3N3b3JkIiwiYWRtaW4iOnRydWUsIl9fdiI6MH0.ah-NFQ1967WVeN6lYNAahT7hZtshG6kw6AW3ncuJOYw


## Exploration
- [Keeping API Routing Clean with Express Routers](https://scotch.io/tutorials/keeping-api-routing-clean-using-express-routers)
