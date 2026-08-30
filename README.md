# Welcome Home

A private, personal website made as a gift. Runs entirely locally — no server, no internet connection required for the core experience.

## How to open it

Double-click `index.html`, or drag it into any web browser. That's it.

If you want the "Add to Home Screen" / installable app behaviour to work, you'll eventually need to serve it over `http://` or `https://` rather than opening the file directly (browsers restrict service workers on `file://`). For everyday use, just opening `index.html` is fine — everything except the installable-app part works straight away.

## Folder structure

```
welcome-home/
    index.html        ← the whole site (structure, style, and behaviour)
    manifest.json      ← makes the site installable as an app
    sw.js               ← lets the site work offline once visited
    README.md           ← this file
    icons/               ← app icons (already included)
    media/
        videos/           ← put your "Open When" videos here
        audio/             ← put your "Hear Me" voice recordings here
            music/           ← put your "Music" section songs here
        images/            ← optional photo(s) for the Love section
```

## Adding your media

### Open When videos (required for that section to work)

Drop your video files into `media/videos/` using **exactly** these filenames:

```
media/videos/bad-day.mp4
media/videos/stressed.mp4
media/videos/miss-me.mp4
media/videos/cant-sleep.mp4
media/videos/motivation.mp4
media/videos/happy.mp4
media/videos/hug.mp4
```

If a file is missing, that card will simply show "Video coming soon." instead of breaking the page — so you can add them one at a time.

Videos should be `.mp4` format for the widest browser support.

### Hear Me voice recordings

Add audio files to `media/audio/`:

```
media/audio/good-morning.mp3
media/audio/good-night.mp3
media/audio/just-because.mp3
```

Want more or different recordings? Open `index.html`, find the `hearMeTracks` list near the top of the `<script>` section, and add or edit entries like this:

```js
{id:'good-morning', title:'Good morning', file:'media/audio/good-morning.mp3'},
```

### Music

Add song files to `media/audio/music/`:

```
media/audio/music/song-1.mp3
media/audio/music/song-2.mp3
media/audio/music/song-3.mp3
```

Edit the `musicTracks` list in `index.html` the same way as above to rename tracks or add more.

### Love section extras (optional)

- **Hear It** looks for `media/audio/love-note.mp3`
- **See It** looks for `media/images/love.jpg`

If either file is missing, the button will simply say "coming soon" instead of breaking anything.

## Editing the words

Everything you'd want to personalise lives inside `index.html`:

- **Love messages** — search for `const loveMessages` and edit the list of lines.
- **Love Note** (the longer note) — search for `loveNoteBox` in the HTML section and edit the text inside it.
- **Secret** — search for `secret-text` in the HTML section and replace the message with your real secret.
- **Section titles/subtitles** — each screen's text sits right in the HTML, in plain readable sentences.

You don't need to know how to code to change these — just find the sentence in quotes and replace it with your own words, keeping the quote marks in place.

## What's already working

- Opening screen → Enter → Home
- All seven home cards navigate correctly, each with a way back to Home
- Open When: 7 cards, each showing a title and its video only (play, mute, fullscreen)
- Hear Me & Music: custom audio players (play/pause, progress bar, tap to seek)
- Take a Break: adjustable countdown timer with Start/Pause/Reset
- Brain Dump: free writing area, auto-saved to this browser only (localStorage), with Clear
- Love: random message on tap, plus Love Note / Hear It / See It / One More
- Secret: tap-to-reveal hidden message
- Extra → Send a Little Love: a real, working drawing canvas (mouse + touch), with colour choices, Undo, Clear, and Send

## Testing checklist

1. Open `index.html` — the opening screen should appear.
2. Tap **Enter** — you should land on Home.
3. Tap each of the 7 home cards — each should open its section.
4. On every section, tap **← Back** — you should return to Home.
5. Open "Open When," tap each of the 7 cards — correct title should show each time.
6. If you've added video files, they should play, mute, and go fullscreen; if not, you should see "Video coming soon." instead of an error.
7. In Love, tap **Press for Love** and **One More** several times — the message should change each time.
8. In "Send a Little Love," draw with your mouse (and, on a phone/tablet, with your finger) — a line should appear. Try **Undo** and **Clear**.
9. Resize your browser window (or open on your phone) — everything should stack cleanly with no overflow.
10. Open your browser's developer console (optional, for the technically curious) — there should be no red error messages.

## A note on privacy

Brain Dump content is saved only in your own browser's local storage — it never leaves the device, and there's no server involved anywhere on this site.
