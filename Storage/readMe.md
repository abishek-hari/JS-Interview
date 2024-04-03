### COOKIES VS LOCAL STORAGE VS SESSION STORAGE

Local Storage, Session Storage, and Cookies are all mechanisms in web development to store data on the client side, but they have some key differences.

# COOKIES

Purpose:Cookies are primarily used for tracking and session management.
Storage Limit: Limited to around 4KB.
Lifetime:Cookies Can be set with an expiration date, or they become session cookies if no expiration is set.

```js
// Setting a cookie
document.cookie =
  "username=John Doe; expires=Thu, 18 Dec 2022 12:00:00 UTC; path=/";

// Retrieving a cookie
let username = document.cookie
  .split(";")
  .find((cookie) => cookie.includes("username"))
  .split("=")[1];
```

# SESSION STORAGE

Purpose: Similar to cookies, but with a larger storage capacity and a shorter lifecycle. Data stored in session storage is only available for the duration of the page session (as long as the browser is open).
Storage Limit: Usually around 5MB.
Lifetime: Cleared when the page session ends (when the browser tab is closed).

```js
// Setting data in session storage
sessionStorage.setItem("key", "value");

// Retrieving data from session storage
let value = sessionStorage.getItem("key");
```

# LOCAL STORAGE

Purpose: Similar to session storage, but with a longer lifecycle. Data stored in local storage persists even after the browser is closed and reopened.
Storage Limit: Usually around 5MB.
Lifetime: Persistent until explicitly cleared by the user or through JavaScript.

```js
// Setting data in local storage
localStorage.setItem("key", "value");

// Retrieving data from local storage
let value = localStorage.getItem("key");
```
