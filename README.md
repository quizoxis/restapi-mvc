# REST API using Node and MVC

# Requirements

- nodejs
- express
- mongodb

# Dependencies
`express mongoose body-parser`

## Development

`babel-cli babel-loader babel-preset-es2015 nodemon webpack webpack-cli`

- Express.js:  is a node.js frameworks to develop the application.
- Mongoose: is a MongoDB ORM which provides easy to use syntax to query the data from the database.
- body-parser: is used parse all the request coming in the application.
- babel-cli: is used to make our application ES6 code to the backward-compatible version of the javascript.
- webpack: is used to bundle the javascript files for the production.
- nodemon: is used to start our server every time when there is any change in the code. It is only for the development purpose that’s why we install it into the devDependencies.

# Running

- Start a MongoDB container:

`docker run -d -p 27017-27019:27017-27019 --name mongodb mongo:latest`

- Start API Server

`npm start`

# Test

You can use any API client like postman, for the sake of simplicity i'm using curl here.

## Create a New user

Following makes a POST request:

`curl -d '{"name":"ruser","email":"ruser@r.ne"}' -X POST -H 'Content-Type: application/json' http://localhost:3000/api/v1/users`

Response:

`{"message":"user created successfully","data":{"_id":"5e68f3b660973a08b12ca8c9","name":"ruser","email":"ruser@r.ne","createdAt":"2020-03-11T14:20:38.226Z","updatedAt":"2020-03-11T14:20:38.226Z","__v":0}}`


## Fetch list of users

`curl -H 'Content-Type: application/json' -X GET http://localhost:3000/api/v1/users`

Response:

`{"message":"users fetched successfully","data":[{"_id":"5e68f3b660973a08b12ca8c9","name":"ruser","email":"ruser@r.ne","createdAt":"2020-03-11T14:20:38.226Z","updatedAt":"2020-03-11T14:20:38.226Z","__v":0}]}`

## Get details of specific user

`curl -H 'Content-Type: application/json' -X GET http://localhost:3000/api/v1/users/5e68f3b660973a08b12ca8c9`

Response:

`{"message":"user with id 5e68f3b660973a08b12ca8c9 fetched successfully","data":{"_id":"5e68f3b660973a08b12ca8c9","name":"ruser","email":"ruser@r.ne","createdAt":"2020-03-11T14:20:38.226Z","updatedAt":"2020-03-11T14:20:38.226Z","__v":0}}`


## Update User Info

`curl -d '{"name":"ruser","email":"ruser@r.nero"}' -X PUT -H 'Content-Type: application/json' http://localhost:3000/api/v1/users/5e68f3b660973a08b12ca8c9`

Response:

`{"message":"user updated successfully","data":{"_id":"5e68f3b660973a08b12ca8c9","name":"ruser","email":"ruser@r.nero","createdAt":"2020-03-11T14:20:38.226Z","updatedAt":"2020-03-11T14:31:31.735Z","__v":0}}`

## Delete user

`curl -H 'Content-Type: application/json' -X DELETE http://localhost:3000/api/v1/users/5e68f3b660973a08b12ca8c9`
