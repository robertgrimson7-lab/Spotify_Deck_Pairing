# Spotify Deck wireless sign-in return page

This small static site returns a short-lived Spotify authorization code to an ESP32 Spotify Deck during phone-based setup. It has no token service, analytics, external scripts, or database. Spotify passwords remain on Spotify's sign-in page; the deck exchanges its code directly with Spotify using PKCE and retains its tokens locally.

Open setup on the deck first. Join its temporary Wi-Fi, configure home Wi-Fi, then connect your phone to that same home network. Open the deck's home-network address, unlock with the key on its display, and start Spotify sign-in. This page offers a return link and a copy/paste handoff if a browser blocks navigation to the local deck.

Register this exact URI in your own Spotify developer app:

`https://robertgrimson7-lab.github.io/Spotify_Deck_Pairing/callback.html`

The local destination is restricted to private IPv4 addresses. The device validates the random, expiring state and keeps the PKCE proof; this page cannot independently complete sign-in. The return page clears the code from the visible browser URL and sends no subsequent network requests. As the HTTPS host, GitHub receives the initial callback request and its query parameters; the authorization code is short-lived and cannot be exchanged without the deck's proof. Do not share handoff text.

The page is published from the `main` branch using GitHub Pages. No Wi-Fi credentials, Spotify tokens, owner Client ID, firmware binaries or project-local notes belong in this repository. This is an independent project, not an official Spotify product.

References: [Spotify PKCE flow](https://developer.spotify.com/documentation/web-api/tutorials/code-pkce-flow), [redirect URI requirements](https://developer.spotify.com/documentation/web-api/concepts/redirect_uri).
