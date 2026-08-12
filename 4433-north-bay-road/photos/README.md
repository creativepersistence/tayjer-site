# Photos — 4433 North Bay Road

71 listing photographs of the property, watermarked `A11886801 © Miami MLS® 2025`.

```
photos/
├── photo-1.jpg … photo-71.jpg    full size, 1600px wide — used by the lightbox
└── thumbs/                        900px, q78 — used by the gallery grid
```

The gallery loads `thumbs/`, and the lightbox loads the full-size original of the
same filename. Any thumb that's missing renders a "photo pending" tile instead,
so the page never breaks on a gap.

## Changing what's shown

The gallery is driven by the `SHOTS` array in `../index.html` (search for
`const SHOTS`). Each entry is:

```js
{ f:"photo-3.jpg", cap:"Front elevation", alt:"…", cls:"shot--wide" }
```

`cls` is optional: omit it for a third-width tile, `shot--wide` for half width,
`shot--hero` for full width. To add a photo that isn't in the current selection,
add an entry and generate its thumbnail:

```bash
python3 -c "
from PIL import Image
im = Image.open('photo-NN.jpg').convert('RGB')
im.thumbnail((900, 900), Image.LANCZOS)
im.save('thumbs/photo-NN.jpg', 'JPEG', quality=78, optimize=True, progressive=True)"
```

## What's in the set

26 of the 71 are currently selected for the gallery. Also used outside it:

| File | Where |
|---|---|
| `photo-1.jpg` | full-bleed band beneath the hero |
| `photo-71.jpg` | floor plan, in The Residence |
| `photo-70.jpg` | second floor-plan variant, unused |
| `photo-68.jpg` | overhead aerial — the roof is masked in the original, so unused |

The remaining ~40 are alternate angles of rooms already represented.

## Two notes on accuracy

**The property is not waterfront.** The overhead aerial (`photo-68.jpg`) and the
site plan (`photo-71.jpg`) both show an interior lot fronting North Bay Road,
hedged on all sides, with a pool and a lap pool — no bay frontage and no dock.
Earlier copy on the page described it as bayfront; that has been corrected.
Don't reintroduce it.

**No photograph of "The Vintner's Wall."** The 150-bottle wine gallery described
in the owner's press release doesn't appear anywhere in this set. The feature is
still listed on the page because it's sourced from the release, but it's worth
confirming before the page goes live.
