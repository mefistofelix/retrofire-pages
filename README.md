# retrofire-pages

Static pages for the RetroFire app on Fire TV, served by GitHub Pages:

- `addrepo/`: opened on a phone from the QR code the TV shows ("Aggiungi repository"). It keeps
  the user's repositories (link + password) in the browser's localStorage and sends the chosen
  ones to the TV through Nostr: an event of kind 30078 tagged `d=<topic from the QR>`, its content
  encrypted with AES-256-GCM under the key from the QR (additional data: the topic), so only that
  TV can read it. The event expires after one hour (NIP-40).
