# Project Rules

- Never add a subtitle under `Ross Family Chores`.
- `index.html` must remain compatible with the old Samsung TV Internet browser.
- Do not use CSS Grid.
- Do not use Flexbox (`display: flex`, `inline-flex`, `flex-*`, `justify-content`, `align-items`).
- Prefer old-browser-safe layout patterns (`display: block`, `inline-block`, `table`, `table-cell`, and floats when needed).
- When using modern visual CSS (gradients, shadows, etc.), include simple fallback values first (for example `background-color` before `background` gradients).
- Always make sure all kids have chores every week: Ellie, Brooklyn, Hazel, Maverick, Hinckley, Adaline and Raleigh.
- It is okay to commit directly to `main` in this repo — no feature branch or PR is required.
- Phone photos (especially from Samsung phones) often carry an EXIF `Orientation` tag instead of storing pixels upright. Modern browsers/Mac Preview auto-rotate using that tag, but the old Samsung TV browser does not, so sideways/upside-down photos only show up on the TV. Before adding any photo to the site, bake the rotation into the pixel data and strip the orientation tag so every browser renders it the same way:
  ```
  python3 -c "
  from PIL import Image, ImageOps
  img = Image.open('photo.jpg')
  ImageOps.exif_transpose(img).save('photo.jpg', quality=90)
  "
  ```
  Verify with `python3 -c "from PIL import Image; img = Image.open('photo.jpg'); print(img.size, img.getexif().get(274))"` — orientation should print `None`. Do this for every photo added to the repo, not just ones that look sideways in a normal browser preview.
- When the user gives you text to put on the page (chore names, notes, lyrics, labels, etc.), spell check it first and point out anything that looks misspelled before adding it. Don't silently auto-correct — flag it and let the user confirm the fix or say it's intentional.
