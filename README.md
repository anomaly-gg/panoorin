# Panoorin show list

The grandparents' TV app (Panoorin v6+) reads `shows.json` from
https://anomaly-gg.github.io/panoorin/shows.json whenever it opens
(at most every 10 minutes; GitHub Pages itself caches ~10 minutes).

Each entry is one tile, matched by `id`:
- edit an entry -> the tile updates in place on the TV
- delete an entry -> the tile disappears from the TV
- add an entry -> a new tile appears at the end
Tiles added on the TV itself are never touched.

Easier: add shows on the TV itself - the editor's "MAGDAGDAG NG PALABAS" list
shows every show the Worker (../worker) has seen a full episode of in the last
two weeks, one OK to add. This file is for tiles you want pushed from the PC.

A show tile needs `show`:
- `search`  - what to type into YouTube search ("Coco Martin's Sigabo Episode")
- `match`   - the show's name as the Worker lists it ("Coco Martin's Sigabo");
              an exact match wins, otherwise any show whose name contains it
- `channel` - the uploading channel ID:
              ABS-CBN Entertainment UCstEtN0pgOmCf02EdXsGChw   GMA Network   UCKL5hAuzgFQsyrsQKgU0Qng
              GMA Public Affairs    UCj5RwDivLksanrNvkW0FB4w   GMA News      UCqYw-CTd1dU2yGI71sEyqNw
              ABS-CBN News          UCE2606prvXQc_noEqKxVJXA   News5         UCGEbMwiX774cseKvJqF9R2g
              PTV                   UCJCUbMaY593_4SN1QPG7NFQ

Only uploads titled "... Episode N ..." from that channel count, so clips,
highlights and recaps are ignored. "Episode N (1/3)" parts are grouped.

Optional: `subtitle`, `mark` (2-3 letters), `color` ("#RRGGBB"),
`section` ("DRAMA" or "NEWS"). Without `show`, a tile is a plain link and needs `url`.

Publish: run `publish.bat` in this folder.
