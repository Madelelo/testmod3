# module 3 individual assignment

Submitted by: TODO

Heroku URL: TODO

## overview

Your goal is to understand and extend a skeleton app that connects ReactJS with Express.

## getting started

### run the app

First, start the app. To do this, run

    npm install

To run a development server, run:

    npm start

(npm start must be run from the root directory of the project, *not* in /client).

npm start will automatically open a browser window to

    http://localhost:3000

### push the app to heroku

Create a heroku app to host this code, make sure you can see the app.

### understand the code layout

**server**

First, look around `/server`. This should be familiar.  It is a simple express.js app, not much more than the result of running the express generator.  `app.js` is the main process; it is started by running `bin/www`, which contains some configuration.

Try putting this in your browser:

    http://localhost:3001/api/movies

That URL and response is defined in `/server/routes/api.js`

**client**

Now, look around `/client`. This is a skeleton ReactJS application, not much more than the result of running [create-react-app](https://github.com/facebookincubator/create-react-app).

**client + server = single page application**

Client is the html, server has API endpoints that return JSON. This is the basic architecture of a single-page application (SPA).

Behind the scenes, npm start will start two development servers, one for react (port 3000) and one for express (port 3001). The react server will proxy requests to express. As a developer, you will typically interact with the port 3000 app. This setup is very similar to the one described here: <https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/>

### make changes, view the output

To learn more about what's going on here, make experimental changes to files (e.g., MainLayout.js or Root.js), and watch the changes affect what's shown in the browser.

### understand that the app uses react-router

See index.js, which defines the routes, using [react-router](https://github.com/ReactTraining/react-router).

See <https://github.com/ReactTraining/react-router/blob/master/docs/Introduction.md> for more docs on exactly what's going on here. The main point to understand is that client-side code is swapping html templates in and out as the user clicks links.

Here's another good guide: <https://css-tricks.com/learning-react-router/>

### understand that the app makes an API call to express

See the method `componentDidMount` in `Root.js` for an example of how to fetch data from an API call to express. (What's that componentDidMount hook? See <https://facebook.github.io/react/docs/react-component.html>)

The code in Root.js code also demonstrates passing data between components, as discussed in <https://css-tricks.com/learning-react-container-components/>


## assignment tasks

Your task is to create very tiny movie site by changing code in /client. You should not have to change code in other directories (e.g., /server) to complete this assignment.

Background: The express server has two routes (/api/movies and /api/movies/:movieId) that return JSON to the client with movie information. There are only 12 movies in this dataset. You should be able to see this api by visiting, e.g.,

    http://localhost:3001/api/movies
    http://localhost:3001/api/movies/122904

Your tasks:

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
