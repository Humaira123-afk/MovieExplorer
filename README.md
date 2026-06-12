MovieExplorer
A cross-platform mobile application built with React Native (Expo) that allows users to explore trending movies, search for films, save bookmarks, and watch trailers  all in one place.

App Idea & Features
MovieExplorer was built to solve a simple problem: having one clean, fast mobile app where you can discover movies without jumping between different platforms.
Trending Movies : On launch, the home screen fetches real-time trending movies from the TMDB API and displays them in a scrollable list with posters, titles, and ratings.
Search : Users can search for any movie by name. Debouncing is implemented to avoid unnecessary API calls on every keystroke, keeping the experience smooth and fast.
Bookmarks : Any movie can be bookmarked with a single tap. Bookmarks are saved using AsyncStorage so they persist even after closing the app.
Trailer Viewer : Each movie detail screen includes a Watch Trailer button that plays the official YouTube trailer directly inside the app via expo-web-browser.

How useEffect Was Used
useEffect is the backbone of all data fetching and side effects in this app.
On the Home screen, useEffect triggers an API call to TMDB when the component mounts to load trending movies. On the Search screen, useEffect watches the search query and implements a debounce timer  if the user stops typing for 500ms, the API call fires, and the cleanup function clears the timer on every re-render to prevent redundant calls. On the Bookmarks screen, useEffect loads all saved bookmarks from AsyncStorage whenever the screen comes into focus. On the Movie Detail screen, useEffect re-runs whenever the movie ID changes to fetch full details and the trailer link for that specific film.

Challenges Faced & How They Were Solved
AsyncStorage Persistence : Since AsyncStorage is asynchronous, bookmark saving and loading had timing issues. Fixed by properly using async/await inside useEffect with loading states.
Too Many API Calls on Search : Every keystroke was triggering an API call causing lag. Solved by implementing debouncing inside useEffect using setTimeout and cleanup functions.
Trailer Integration : Playing trailers without leaving the app was tricky. Used expo-web-browser to open YouTube links in an in-app browser session.
Empty States & Error Handling : When the API returned no results or failed, the UI would break. Added proper error handling and empty state screens to give users clear feedback.
Dark Mode Support : Since app.json has userInterfaceStyle set to automatic, the app needed to look good in both light and dark mode. Used React Native's useColorScheme hook with conditional styling throughout.

Tech Stack
React Native with Expo 54, Expo Router for file-based navigation, TMDB API for movie data, AsyncStorage for bookmark persistence, React Navigation for bottom tab navigation, and TypeScript for type safety.
