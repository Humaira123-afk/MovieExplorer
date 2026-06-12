# 🎬 Movie Explorer

A React Native app to discover trending movies, search by genre, save bookmarks, and watch trailers — all powered by the TMDB API.

**GitHub:** [github.com/Rakhi-Kahtri/Movie_Explorer](https://github.com/Rakhi-Kahtri/Movie_Explorer)

---

## Features

- **Authentication** — Login and Signup with persistent sessions using AsyncStorage
- **Trending Movies** — Fetches the latest trending movies from TMDB across multiple pages
- **Search & Filter** — Search movies by title and filter by genre
- **Bookmarks** — Save and revisit your favourite movies
- **Watch Trailers** — Opens the official trailer directly on YouTube

---

## How `useEffect` Was Used

**`home.js`**
On screen load, `useEffect` fetches movies from 5 pages of the TMDB trending endpoint and combines the results into a single list displayed to the user.

**`detail.js`**
When a movie is selected, `useEffect` triggers three separate TMDB requests — movie details, cast information, and trailer data — so everything is ready when the detail screen opens.

---

## Challenges & Solutions

| Challenge | Solution |
|---|---|
| Duplicate movies appearing in the list | Added a filter to remove entries with repeated IDs before rendering |
| Trailers not loading for some movies | Built a 3-level fallback logic that tries multiple video sources before giving up |
| Terminal errors due to spaces in folder name | Wrapped the folder path in quotes in all terminal commands |

---

## Tech Stack

React Native · TMDB API · AsyncStorage · YouTube (trailer playback)
