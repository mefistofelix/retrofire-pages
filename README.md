# retrofire-pages

Static pages for the RetroFire app on Fire TV, served by GitHub Pages:

- `addrepo/`: opened on a phone from the QR code the TV shows ("Aggiungi repository"). It keeps
  the user's repositories (link + password) in the browser's localStorage and sends the chosen
  ones to the TV with pkarr (the signed DNS records iroh uses for discovery): the QR carries an
  Ed25519 key seed and an AES key; the page signs a DNS packet with a TXT record `_rf` holding
  the repositories (deflate-raw, then AES-256-GCM with the QR key, additional data = the public
  key in z-base-32) and PUTs it to several pkarr relays, where the TV reads it.
