# Panoorin show list

The grandparents' TV app (Panoorin v6+) reads `shows.json` from
https://anomaly-gg.github.io/panoorin/shows.json whenever it opens
(at most every 10 minutes; GitHub Pages itself caches ~10 minutes).

Each entry is one tile, matched by `id`:
- edit an entry -> the tile updates in place on the TV
- delete an entry -> the tile disappears from the TV
- add an entry -> a new tile appears at the end
Tiles added on the TV itself are never touched.

A show tile needs `show`:
- `search`  - what to type into YouTube search ("Coco Martin's Sigabo Episode")
- `match`   - a word every episode title contains ("Sigabo")
- `channel` - the uploading channel ID (ABS-CBN Entertainment = UCstEtN0pgOmCf02EdXsGChw,
              GMA Network = UCKL5hAuzgFQsyrsQKgU0Qng)

Only uploads titled "... Episode N ..." from that channel count, so clips,
highlights and recaps are ignored. "Episode N (1/3)" parts are grouped.

Optional: `subtitle`, `mark` (2-3 letters), `color` ("#RRGGBB"),
`section` ("DRAMA" or "NEWS"). Without `show`, a tile is a plain link and needs `url`.

Publish: run `publish.bat` in this folder.
