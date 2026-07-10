# CSS Clamp Calculator

Compute a CSS `clamp()` for fluid typography and spacing from a min and max viewport and size, with correct `vw`-based linear interpolation and the math explained. No server, no tracking, no third-party scripts.

**Live demo:** https://0xelitesystem.github.io/css-clamp-calculator/

## Use

Open `index.html` in any modern browser, or visit the GitHub Pages link in the repo description.

Enter four numbers:

- Min viewport width (px)
- Max viewport width (px)
- Min size at that min viewport (px)
- Max size at that max viewport (px)

The tool outputs a `clamp(min, preferred, max)` string where the preferred value scales linearly with the viewport. You can output the fixed parts in `rem` (with a configurable root font size) or in `px`. Copy the result with one click.

It also shows a live preview that resizes with your browser window, and a step-by-step breakdown of the slope, the `vw` coefficient, and the intercept so you can check the numbers yourself.

## Why this exists

Fluid type is just linear interpolation, but the arithmetic (slope, intercept, converting to `vw` and `rem`) is fiddly to do by hand and easy to get subtly wrong. This does it in one HTML file and shows its work, so you can trust the output instead of copying a number you cannot verify.

## The math

For a size that goes from `minSize` at `minVw` to `maxSize` at `maxVw`:

- `slope = (maxSize - minSize) / (maxVw - minVw)` (px per px, unitless)
- The `vw` coefficient is `slope * 100`
- `intercept = minSize - slope * minVw` (the size at a viewport of 0)
- `preferred = intercept + slope * viewport`, written as `intercept + (slope * 100)vw`
- `clamp()` holds the result between the smaller and larger of the two sizes

## Privacy

Everything runs in your browser. Nothing is uploaded. Verify by viewing the page source or by opening DevTools and watching the network tab. No requests are made.

## Run locally

```bash
git clone https://github.com/0xelitesystem/css-clamp-calculator
cd css-clamp-calculator
# Open index.html in your browser, or:
python -m http.server 8000
```

## Build

There is no build. It is a single HTML file with inline CSS and JavaScript.

## License

MIT.

## Related

- [cubic-bezier-editor](https://github.com/0xelitesystem/cubic-bezier-editor)
- [gradient-generator](https://github.com/0xelitesystem/gradient-generator)
- [box-shadow-generator](https://github.com/0xelitesystem/box-shadow-generator)
