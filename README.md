# sejulphanord.com

My portfolio, built as a spreadsheet. Sheet tabs are the nav, and the sticky notes are comments I left on my own work.

Live at **[sejulphanord.com](https://sejulphanord.com)**. Hosted on GitHub Pages, no build step.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The whole site: layout, styles, content, and scripts |
| `images/` | Headshot, About photo, Work context photos, and the Photos tab |
| `images/photos/thumbs/` | Square thumbnails for the Photos tab |
| `Sejul-Phanord-CV.docx` | The CV linked from Work and Contact |
| `CNAME` | Tells GitHub Pages to serve this at sejulphanord.com. Don't delete it. |

## Common updates

Everything below happens in `index.html`. Search for the text in `code` to jump to the right spot.

### Add or remove a photo
1. Export the photo at about 1800px on the long edge and save it to `images/photos/`, e.g. `beach-portrait.jpg`.
2. Make a square 360×360 crop of it with the same filename in `images/photos/thumbs/`.
3. Find `const PHOTOS` and add a line:
   ```js
   ['beach-portrait','Beach portrait','Portrait','2026',CAM,LENS],
   ```
   The order is filename (without `.jpg`), title, type, year, camera, lens. Use `PHONE,''` for phone shots.
4. Type must be one of: Portrait, Event, Sports, Nature, Travel, Ships. For a new type, also add it to the dropdown at `id="typeFilter"`.

Rows show in the order they're listed, so put your strongest photo first.

### Add or edit a work project
Find `const PROJECTS`. Each project has:
- `name`, `role`, `year`, `area`: the columns in the table
- `img` and `cap`: the context photo (landscape, saved in `images/work/`) and its caption. Leave `img:''` for no photo.
- `sections`: pairs of heading and paragraph, as many as you need
- `tags`: the small line at the bottom
- `note`: the comment that shows beside it

The "Recent work" table on Home fills in from this list automatically.

### Edit a comment
Most comments live in the HTML. Search `class="note"` to find each one. Work project comments are the `note` field in `PROJECTS`.

### Update my details
Quick facts appear in two places, Home and About. Search `Quick facts` and update both.

### Side projects
Search `Side projects`. Each row is a name, a one-line description (it appears twice: once for desktop, once in `what-m` for phones), and a status chip.

### Change colors
The color tokens are at the top of the `<style>` block. `--accent` sets the blue, and there's a light value and a dark value. Change both.

## Contact form
The form sends through [Web3Forms](https://web3forms.com) to contact@sejulphanord.com, which Namecheap forwards to my inbox. The access key is set in `WEB3FORMS_KEY` near the top of the script. It's meant to be public.

If messages stop arriving:
1. Send a test email straight to contact@sejulphanord.com. If that doesn't arrive, the Namecheap forwarder is the problem.
2. If it does arrive, check the key and the Web3Forms dashboard. The free plan allows 250 messages a month.

## Publishing changes
1. Open `index.html` in a browser to check it locally. Everything works except the form.
2. Check it at phone width and in dark mode (the button in the top right).
3. Commit to `main`. Pages redeploys in a minute or two. Hard refresh if you still see the old version.


