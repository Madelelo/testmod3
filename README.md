# Module 3 individual assignment #

Submitted by: x500@umn.edu

Heroku URL: heroku_url_to_your_app

## Overview #

Your goal is to understand and extend a skeleton app that connects ReactJS with Express.

## Getting started ##

### Run the app ###

First, we need to install our dependencies. To do this, run

    npm install

Let's confirm that everything is working by starting our server.
To start the development server go to the base directory of your
project and run:

    npm start

This should automatically open a browser window to
`http://localhost:3000`. If it didn't, simply
navigate to it directly.

### Deploy to Heroku ###

Now that we know it is working locally, let's deploy it to Heroku.
You should be able to follow the normal deploy process.

Once you have successfully deployed the app. Go to its url and
confirm that it looks like you would expect.


### Understand the code layout ###

#### Server ####

First, take a look around `/server`. The layout should be familiar.  It is a simple express.js app, not much more than the result of running the express generator. The entry point is `app.js`. The role of the server in single-page applications (SPA) is to provide data for the client.

Restart you local server and try pointing your browser to this URL:

    http://localhost:3000/api/movies

Do you see anything? I don't, give this URL a try:

    http://localhost:3001/api/movies

See something now? Good.

That URL and response is defined in `/server/routes/api.js`.

But what is going on here? Our server is running on port 3000 so what gives? This gets into some of the behind-the-scenes magic of our React development environment. `npm start` actually started two web servers. One runs on port 3000 (react development server) and the other on port 3001 (express). The react server on port 3000 is provided to make react development easy by serving an app directly from the contents of the `client/src` directory, even though that source code is not browser-ready without a build step. The react development server on 3000 is configured to proxy RESTful API requests to the express server on 3001.

As a developer, you will typically interact with the port 3000 app. This setup is very similar to the one described here: <https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/>


#### Client ####

Now, take a look around `/client`. This is a skeleton ReactJS
application, initially created by running
[create-react-app](https://github.com/facebookincubator/create-react-app)
with some minor modifications.


#### client + server = single page application ####

The client handles all of the html, while the server provides data through API endpoints that return JSON. This is the basic architecture of a single-page application (SPA).

### Make changes, see what happens ###

To learn more about what's going on here, make experimental changes to files in the client (e.g., src/MainLayout.js or src/Root.js), and watch the changes affect what's shown in the browser.

If you are using `npm start` your changes should appear as soon as you save your file.

### React-router ###

Go to the main page of our app. There should be a link called "a link to foo". Click this link and watch the terminal running your server carefully. Did you see anything change? You shouldn't have. We went to `localhost:3000/foo`, but the server didn't record any activity. This is because react is doing all the routing client side and doesn't touch the server for the new webpage.

To see how this is done go to `client/src/index.js`, which defines the routes, using [react-router](https://github.com/ReactTraining/react-router).

See the [react-router introduction docs](https://github.com/ReactTraining/react-router/blob/master/docs/Introduction.md) for more information on exactly what's going on here. The main point to understand is that client-side code is swapping html templates in and out as the user clicks links.

Here's another good guide: <https://css-tricks.com/learning-react-router/>

### Making an API call to express ###

See the method `componentDidMount` in `client/src/Root.js` for an example of how to fetch data from an API call to express. (What's that componentDidMount hook? See <https://facebook.github.io/react/docs/react-component.html>)

The code in `Root.js` code also demonstrates passing data between components, as discussed in <https://css-tricks.com/learning-react-container-components/>


## Assignment ##

Your task is to create very tiny movie site by changing code in /client. You should not have to change code in other directories (e.g., /server) to complete this assignment.

### Background ###

The express server has two routes (/api/movies and /api/movies/:movieId) that return JSON to the client with movie information. There are only 12 movies in this dataset. You should be able to see this api by visiting, e.g.,

    http://localhost:3001/api/movies
    http://localhost:3001/api/movies/122904

### Your tasks ###

0. Change the application's header and style.  Get rid of the current style, react icon, and content, and put in a simple header and styling that makes this look like a custom movie site.  No need for fancy style.

1. Convert the home page of the app (`/`) to show a list of movies (i.e., it should render a `MovieList` component that you will write). Your new component should fetch `/api/movies` from the server, then render the results into a list or grid view. Each movie in the display should show at least these items:

    * title
    * releaseYear
    * average rating
    * link to the "movie details page" (see next item)

    Remember, this is very similar to what `Root.js` is currently doing, the main additional step is to iterate over a list, rather than rendering a single object.  See <https://facebook.github.io/react/docs/lists-and-keys.html#rendering-multiple-components>

2. Add a route to the react app (`/movies/:movieId`) that shows a single movie (e.g., a `Movie` component) and its details, including:

    * all of the properties listed above
    * a link to imdb (using imdbMovieId)
    * mpaa
    * genres
    * plotSummary
    * a link back to the home page

    (if you want to add an image for fun, those are hosted at TMDb -- e.g., <http://image.tmdb.org/t/p/original/gpaOYwHCF2O5PM5sqFpfzKWuQvb.jpg>)

3. Push your amazing movie site to heroku, and fill out the README above so that we can give you a checkmark.
