# react-sandbox

A React app (in `client`) backed by an Express server (in `server`).

## development

To get started, run

    npm install

To run a development server, run:

    npm start

(make sure you're in this directory, not client).

This will start two development servers, one for react (port 3000) and one
for express (port 3001). The react server will proxy requests to express.
As a developer, you should interact with the port 3000 app.


## heroku

This app is ready for heroku.  When you deploy to heroku, it will:

* build the react app
* start express
* all URLs that don't start with `/api` will simply return the react app

You can simulate this mode by running `heroku local`


## setup notes

client:

<https://github.com/facebookincubator/create-react-app>

    npm install -g create-react-app
    create-react-app client

server:

<http://expressjs.com/en/starter/generator.html>

    npm install express-generator -g
    express server
    cd server
    npm install

combining client + server:

<https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/>

react routing:

<https://github.com/ReactTraining/react-router>

good guides:

<https://css-tricks.com/learning-react-router/> and <https://css-tricks.com/learning-react-container-components/>

<https://medium.com/@learnreact/container-components-c0e67432e005#.9i7s9rn2l>
