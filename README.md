# Aankhon Se Batana — Cinematic Scroll Reel

A single-page, full-screen **scroll animation** telling a wordless love story set to the song
*"Aankhon Se Batana"*. Eight cinematic scenes, each built from layered illustrations that move
with depth (parallax) as you scroll, with continuous idle motion so the page feels alive even
when still. Built with plain HTML/CSS/JS + GSAP — **no build step, no install.**

---

## What's inside

```
aankhon.html              ← the entire reel (open this)
images/aankhon/scene1..8/ ← the artwork (38 PNGs, layered per scene)
README.md                 ← this file
```

That's it. The whole thing is one HTML file plus its images.

---

## How to run it (the easy way)

1. **Unzip** this folder anywhere.
2. **Double-click `aankhon.html`** — it opens in your default browser and runs immediately.
3. **Scroll** (mouse wheel, trackpad, or arrow keys) to move through the eight scenes.

> It needs an internet connection the first time, because GSAP (the animation library) loads
> from a CDN. After that most browsers cache it. To run 100% offline, see "Offline mode" below.

---

## How to run it (recommended — local server)

Some browsers restrict things when opening a file directly (`file://`). Running a tiny local
server avoids that and is how it's meant to be viewed. Pick whichever you have:

**Python (already on most Macs/Linux):**
```bash
cd aankhon-reel        # the unzipped folder
python3 -m http.server 8000
```
Then open **http://localhost:8000/aankhon.html**

**Node (if you have it):**
```bash
cd aankhon-reel
npx serve .
```
Then open the URL it prints (e.g. http://localhost:3000/aankhon.html).

**VS Code:** install the *Live Server* extension, right-click `aankhon.html` → "Open with Live
Server".

---

## How to record it as a reel (what this is for)

- Open the page, put the browser in **full-screen** (press `F11`, or `⌃⌘F` on Mac).
- For a clean capture, **hide the cursor** and scroll at a slow, steady pace — each scene is
  designed to read in ~3 seconds as it passes through the center of the screen.
- Record the screen (QuickTime / OBS / your phone pointed at the screen).
- Add the song *"Aankhon Se Batana"* in your video editor afterward — the page has **no audio**
  built in.
- Suggested on-screen hook text (added in your editor): **"i made this for her"**.

---

## Customizing

Everything lives in `aankhon.html`. A few easy knobs:

- **Motion speed:** near the top of the `<script>` there's a line:
  ```js
  const SPEED = "lively";   // "calm" | "smooth" | "lively" | "intense"
  ```
  Change that one word to make the idle/scroll motion gentler or stronger.

- **Scene text:** each scene's title and subtitle are plain HTML inside its
  `<section class="panel">…</section>` block — edit the words directly.

- **Swap an image:** replace any PNG in `images/aankhon/sceneN/` with your own (keep the same
  filename, keep it **16:9 landscape**). Backgrounds are the `01-*.png` files (opaque); every
  other file is a transparent-PNG layer.

- **Reduced motion:** if a viewer's system has "reduce motion" enabled, the idle animation
  automatically turns off (snap + reveal still work).

---

## Offline mode (optional)

To run with no internet at all, download the two GSAP files and point the page at local copies:

1. Save these two URLs into a `js/` folder next to `aankhon.html`:
   - https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js
   - https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js
2. In `aankhon.html`, change the two `<script src="https://cdnjs…">` tags near the bottom to
   `<script src="js/gsap.min.js">` and `<script src="js/ScrollTrigger.min.js">`.

Now it runs fully offline.

---

## Tech

- **GSAP 3.12** + **ScrollTrigger** for the parallax and idle timelines.
- Hand-written HTML/CSS — no framework, no bundler, no `npm install`.
- Each scene is a stack of transparent-PNG layers composed on a shared 16:9 canvas; CSS masks
  feather the layer edges so they blend; deeper layers travel more for a 3D feel.

## Notes / license

- The included artwork was generated for this project. If you resell or redistribute, make sure
  you have the rights to the images you ship.
- GSAP is © GreenSock, used via its standard CDN; review GreenSock's license for commercial use.
