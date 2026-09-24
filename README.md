# sejulphanord.com

My portfolio, built as a spreadsheet. Sheet tabs are the nav, and the floating comments are notes I left on my own work.

Live at **[sejulphanord.com](https://sejulphanord.com)**. Hosted on GitHub Pages, no build step.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The whole site: layout, styles, content, and scripts |
| `images/` | Headshot, About photo, Work context photos, and the Photos tab |
| `images/sage-face.png` | My illustrated face, used as the avatar on comments |
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
Comments float beside the cell they're about, with a Resolve button like a Figma comment. Resolving one shrinks it to a pin, and clicking the pin opens it again. Resolved comments come back when the visitor opens the site in a new tab.

Most comments live in the HTML. Search `class="comment"` to find each one. Each one goes *inside* the cell it's about:
```html
<aside class="comment" data-c="home"><p>The comment text.</p></aside>
```
`data-c` is a short unique name, used to remember which comments were resolved. Add `data-sm="#someCellId"` to pin it to a different cell on phones. The avatar, pin, and Resolve button are added automatically. Work project comments are the `note` field in `PROJECTS`.

If there's room beside the cell, the comment floats there and starts open. If there isn't (phones, or a cell at the right edge), it shows as a pin with a blue dot and opens as a popover.

### Update my details
Quick facts appear in two places, Home and About. Search `Quick facts` and update both.

### Side projects
Search `Side projects`. Each row is a name, a one-line description (it appears twice: once for desktop, once in `what-m` for phones), and a status chip.

### Change colors
The color tokens are at the top of the `<style>` block. `--accent` sets the blue, and there's a light value and a dark value. Change both. `--canvas` is the gray around the page on big screens, and `--gapfill` shades the narrow spacer columns.

### Layout
The sheet has 8 columns on desktop, 6 on tablets, and 4 on phones. Narrow shaded spacer columns sit between them (`--gap`), so blocks never touch. Past `PAGE_MAX` (in the script) the sheet stops growing and sits centered on a gray canvas, like Excel's Page Layout view.

### Headers and resizing
Click a cell and drag the blue square on its corner to resize it. It follows the pointer smoothly, then glides to the nearest whole cell when you let go. Each cell can grow or shrink by up to 2 columns and 2 rows (`LIMIT` in the script), and double-clicking the square puts it back. Nothing is saved.

Header text sizes itself to its cell: any heading with `class="fit"` gets the largest font size that fits the cell's width and rows, so it grows and shrinks as the cell is resized. `data-max="120"` caps how big it can get (the default is 180px). To make another heading do this, add `class="fit"` to it.

## Contact form
The form sends through [Web3Forms](https://web3forms.com) to contact@sejulphanord.com, which Namecheap forwards to my inbox. The access key is set in `WEB3FORMS_KEY` near the top of the script. It's meant to be public.

If messages stop arriving:
1. Send a test email straight to contact@sejulphanord.com. If that doesn't arrive, the Namecheap forwarder is the problem.
2. If it does arrive, check the key and the Web3Forms dashboard. The free plan allows 250 messages a month.

## Publishing changes
1. Open `index.html` in a browser to check it locally. Everything works except the form.
2. Check it at phone width and in dark mode (the button in the top right).
3. Commit to `main`. Pages redeploys in a minute or two. Hard refresh if you still see the old version.


