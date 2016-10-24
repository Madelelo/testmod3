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

(make sure you're in this directory, not client).

This will start two development servers, one for react (port 3000) and one
for express (port 3001). The react server will proxy requests to express.
As a developer, you should interact with the port 3000 app.

### push the app to heroku

Create a heroku app to host this code, make sure you can see the app.

### understand the code layout

First, look around `/server`. This should be familiar.  It is a simple express.js app, not much more than the result of running the express generator.  `app.js` is the main process; it is started by running `bin/www`, which contains some configuration.

Now, look around `/client`. This is a skeleton ReactJS application, not much more than the result of running [create-react-app](https://github.com/facebookincubator/create-react-app).

Client and server are wired together in a way similar to this: <https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/>

Try changing to the client directory and running `npm run build`.  Look at the /build directory to see the "single page application" that results.

### make changes, view the output

To learn more about what's going on here, make changes to files (e.g., MainLayout.js or Root.js), and watch the changes affect what's shown in the browser.

### understand that the app uses react-router

See index.js, which defines the routes, using [react-router](https://github.com/ReactTraining/react-router).

See <https://github.com/ReactTraining/react-router/blob/master/docs/Introduction.md> for more docs on exactly what's going on here. The key to understand is that it's client-side code that is swapping html templates in and out as the user changes from / to /foo and back again.

Here's another good guide: <https://css-tricks.com/learning-react-router/>

### understand that the app makes an API call to express

See the method `componentDidMount` in `Root.js` for an example of how to fetch data from an API call to express.

This code also demonstrates passing data between components, as discussed in <https://css-tricks.com/learning-react-container-components/>


* push the app to heroku, make sure you can see the app

## tasks

Your task is to create very tiny movie site by changing code in /client. You should not have to change code in other directories (e.g., /server) to accomplish the tasks.

Background: The express server has two routes (/api/movies and /api/movies/:movieId) that return JSON to the client with movie information. There are only 12 movies in this dataset. In development mode, you should be able to test this api by visiting, e.g.,

    http://localhost:3001/api/movies
    http://localhost:3001/api/movies/122904

Your tasks:

0. Change the application's header and style. It currently has a spinning icon and other stuff.  Get rid of this stuff and put in a simple header and styling that makes this look like your own movie site.  You can add a CSS framework if you want, but that's completely optional.

1. Convert the home page of the app (`/`) to show a list of movies (i.e., it should render a `MovieList` component that you will write). Your new component should fetch `/api/movies` from the server, then render the results into a list or grid view. Each movie in the display should show at least these items:

    * title
    * releaseYear
    * average rating
    * link to the "movie details page" (see next item)

Remember, this is very similar to what `Root.js` is currently doing, the main additional step is to iterate over a list, rather than rendering a single object.  See <https://facebook.github.io/react/docs/lists-and-keys.html#rendering-multiple-components>

2. Add a route to the react app (`/movies/:movieId`) that shows a single movie and its details, including:

    * all of the properties from the home page
    * a link to imdb (using imdbMovieId)
    * mpaa
    * genres
    * plotSummary

(if you want to add an image, those are hosted at TMDb -- e.g., <http://image.tmdb.org/t/p/original/gpaOYwHCF2O5PM5sqFpfzKWuQvb.jpg>)

3. Push your amazing movie site to heroku, fill out the README above so that we can give you a checkmark.
