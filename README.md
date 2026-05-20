# NBA New Tab Dashboard

A custom browser new tab page with a clean, minimal dashboard layout inspired by modern start-page extensions, but built as a standalone HTML page that can be hosted anywhere.

Live page:

- https://amarconn.github.io/new-tab/

## Features

- **Google search bar**
  - Search directly from the page.
- **Digital clock**
  - Displays the current local time from the user's computer.
- **Current city and temperature**
  - Uses browser geolocation when permission is granted.
  - Falls back to an approximate location when precise location is unavailable.
- **NBA games for the current day**
  - Shows today's matchups, live status, team logos, and scores.
  - Game times are displayed using the user's local computer time zone.
- **Random wallpaper on every new tab**
  - Loads a new high-resolution background image each time the page opens.
- **Responsive layout**
  - Works on desktop resolutions and adapts to narrower windows.

---

## Browser support

This project is just a static web page, so it works in any modern desktop browser.  
To use it as a **real new tab page**, you need a browser extension that can redirect or replace the default new tab page.

The setup below covers the most common desktop browsers.

---

## Recommended setup

Use this page URL:

```text
https://amarconn.github.io/new-tab/
```

Then configure your browser's custom new tab extension to open that URL.

---

### Firefox setup

For Firefox, the recommended extension is:

- **Custom New Tab Page**

After installing it:

1. Open the extension settings.
2. Paste this URL into the custom new tab field:

   ```text
   https://amarconn.github.io/new-tab/
   ```

3. Save the setting.
4. Open a new tab.

This extension is especially useful because it can keep the address bar ready for typing instead of filling it with the page URL.

---

### Google Chrome setup

Chrome does not provide a built-in setting to replace the new tab page with any URL, so an extension is required.

One compatible option is:

- **Custom New Tab URL**

After installing it:

1. Open the extension options.
2. Set the new tab URL to:

   ```text
   https://amarconn.github.io/new-tab/
   ```

3. Save the setting.
4. Open a new tab.

---

### Microsoft Edge setup

Edge also needs a custom new tab extension.

One available option is:

- **Custom New Tab URL**
- or another Edge extension that supports replacing the new tab page with a custom URL.

Then set:

```text
https://amarconn.github.io/new-tab/
```

as the page to open in new tabs.

---

### Brave setup

Brave supports Chrome Web Store extensions, so the Chrome instructions usually apply.

1. Install a Chrome-compatible custom new tab extension.
2. Set the custom URL to:

   ```text
   https://amarconn.github.io/new-tab/
   ```

3. Open a new tab.

---

### Vivaldi setup

Vivaldi also supports Chrome Web Store extensions.

1. Install a Chrome-compatible custom new tab extension.
2. Set the custom URL to:

   ```text
   https://amarconn.github.io/new-tab/
   ```

3. Open a new tab.

---

## Local hosting or self-hosting

The page can also be self-hosted on:

- GitHub Pages
- Netlify
- Vercel
- Any static website host

For best reliability, use a hosted HTTPS version instead of opening the HTML file directly with `file://`.

---

## How the page works

### Search

The search field sends the query directly to Google.

### Clock

The clock reads the system time from the user's browser.

### Weather and location

The page:

1. Requests browser geolocation when available.
2. Uses reverse geocoding to determine the city name.
3. Loads current temperature data for that location.
4. Caches some recent weather and city data locally in the browser to make reloads faster.

### NBA scoreboard

The page loads the current day's NBA games and displays:

- Team logos
- Team names
- Scores
- Game state
- Local game time
- Live game status when applicable

If the primary score source is unavailable, the page tries a fallback source.

### Wallpaper

Each new tab loads a new random high-resolution background image.  
The user can also manually refresh the wallpaper with the dedicated button on the page.

---

## Customization

### Change the wallpaper source

The wallpaper logic is inside the `loadWallpaper()` function in `index.html`.

### Use a specific collection of Picsum images

Instead of loading a fully random wallpaper every time, you can define a list of image IDs and pick from that list.

Example:

```js
const wallpaperIds = [10, 28, 43, 61, 103, 104, 119, 164, 180, 211];

const randomId =
  wallpaperIds[Math.floor(Math.random() * wallpaperIds.length)];

const url = `https://picsum.photos/id/${randomId}/1920/1080`;
```

### Change the search engine

Inside the HTML form, replace:

```html
action="https://www.google.com/search"
```

with the search URL of another provider.

## Permissions and privacy notes

This page does not require login and does not send data to a custom backend.

However, it does call third-party services in order to provide features:

- Location lookup
- Weather data
- NBA scores
- Wallpaper images

If location permission is granted, your browser may share approximate coordinates with the services used to resolve city name and weather.  
Recent weather and city data may be cached locally in the browser using `localStorage`.

---

## Data and service dependencies

The page relies on external public services for dynamic content:

- Wallpaper images
- Reverse geocoding / city lookup
- Weather data
- NBA scoreboard data

If one of those services changes its API or temporarily becomes unavailable, the related widget may stop working until the page is updated. Such is life on the modern web, where "public endpoint" often means "working until it suddenly does not."

---

## License

Use and modify the project as you like.  
If you publish a modified version, credit is appreciated.
