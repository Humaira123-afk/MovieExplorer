MovieExplorer
A cross-platform mobile app built with React Native (Expo) for exploring trending movies, searching films, saving bookmarks, and watching trailers.

Features

Trending Movies: Home screen fetches real-time trending movies from TMDB API on launch
Search: Debounced search (500ms) to avoid excessive API calls
Bookmarks: Save movies with AsyncStorage for persistence across app restarts
Trailer Viewer: Watch YouTube trailers in-app via expo-web-browser

How useEffect Was Used

Home Screen: Fetches trending movies on component mount
Search Screen: Debounce timer with cleanup function to prevent redundant API calls
Bookmarks Screen: Reloads saved bookmarks whenever screen comes into focus
Movie Detail Screen: Re-fetches movie details/trailer when movie ID changes

Challenges & Solutions

AsyncStorage timing issues: Fixed using async/await with loading states
Excessive API calls on search: Solved via debouncing with setTimeout + cleanup
In-app trailer playback: Used expo-web-browser for YouTube links
Empty/error states: Added proper error handling and empty state UI
Dark mode: Used useColorScheme hook with conditional styling

Tech Stack

React Native (Expo 54), Expo Router (file-based navigation)
TMDB API, AsyncStorage
React Navigation (bottom tabs), TypeScript
