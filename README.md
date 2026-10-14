# SignBridge

SignBridge helps people who use sign language and people who don't understand it talk to each other. It runs in a web browser, so all you need is a webcam.

## The problem

Most people never learn sign language. That makes everyday moments hard for people who sign: talking to a shop assistant, a bank teller, a nurse or a new classmate. They often have to rely on someone else to speak for them, or write things down.

## What SignBridge does

- **Turns signs into words.** Hold a sign up to your webcam and it appears as text on the screen.
- **Reads the words aloud.** Press one button and the text is spoken, so the other person can hear it.
- **Learns the signs you use.** You show it each sign a few times. It then recognizes those signs, such as the alphabet or everyday words.
- **Tells you what it sees, in plain words.** It says things like "I see B, and I'm very sure" or "Your hand looks small, move a little closer", so you always know what to do next.
- **Helps by voice or typing.** Say or type short requests like "hello", "help" or "read this text aloud". It only does a small list of safe things, and it asks before it opens any website.
- **Keeps a conversation list.** Signed words, spoken words and replies all appear in one place.

## Who it can help

- People who use sign language and want to be understood by more people
- Family, friends, teachers and staff who don't know sign language
- Schools and community groups who want a simple way to explore accessibility

## Your privacy

- Your camera video stays on your own device. It is never saved and never sent anywhere.
- The camera and microphone turn on only when you press Start.
- The website loads everything from its own address. It does not call other companies' servers while you use it.
- Your conversation disappears when you close the page. Your taught signs can be kept on your device, but only if you tick a box.
- Some browsers send your voice to their own service to turn it into text. That is a browser feature, not something SignBridge does.

## What it can't do yet

SignBridge is an early version. It recognizes only the signs you teach it, with one hand at a time. It does not understand full sign language, which also uses hand movement, facial expressions and sentence structure. It should be treated as a helper, not a replacement for a human interpreter.

## Try it on your computer

You need [Node.js](https://nodejs.org) 20 or newer and an internet connection for the first build. Use Chrome or Edge.

```
npm install
npm start
```

Then open http://localhost:8000.

1. Open **Sign to speech** and press **Start camera**.
2. Open **Teach gestures**, type a name such as `A`, and press **Record sign**. Do this at least twice for each sign, moving your hand a little closer and farther each time. Teach at least two different signs.
3. Press **Start recognition** and begin signing.
4. Press **Speak text** to hear your words.

Tip: name a sign `SPACE` to add a space, or `DEL` to delete a letter.

## Put it on the internet

SignBridge is a static website. It has no server of its own to run, so any static host works. Step-by-step guides for GitHub Pages, Netlify, Vercel and Cloudflare Pages are in [docs/deploy.md](docs/deploy.md).

## For developers

**How it is built.** Plain HTML, CSS and JavaScript modules. No framework and no bundler. Hand tracking is [MediaPipe](https://github.com/google-ai-edge/mediapipe) running in the browser. Sign matching is a small nearest-neighbours classifier in `public/js/core.js`. See [docs/how-it-works.md](docs/how-it-works.md).

```
public/            the website (index.html, css/, js/)
  js/core.js         matching, steadying, plain-language messages, voice commands
  js/tracker.js      loads and runs hand tracking
  js/app.js          buttons, camera, conversation list
config/security.mjs  the security rules, written once
scripts/build.mjs    builds dist/ and copies in the open-source pieces
scripts/serve.mjs    local server that sends the same security headers as production
tests/               logic, page and security tests
```

**Commands**

| Command | What it does |
|---|---|
| `npm run build` | Builds the site into `dist/`. Downloads the hand model on the first run. |
| `npm start` | Builds, then serves `dist/` at http://localhost:8000 with production headers. |
| `npm test` | Runs all tests. |

**Settings** (environment variables, all optional)

| Name | Purpose |
|---|---|
| `MODEL_URL` | Where to download the hand model from, if you want to use your own copy. |
| `MODEL_SHA256` | If set, the build refuses a model file whose checksum does not match. |
| `ALLOW_MISSING_MODEL=1` | Lets the build finish without the model. Only used by the tests. |
| `PORT` | Port for the local server. Default 8000. |

No API keys or secrets are needed anywhere.

**Security.** A strict Content Security Policy allows scripts, styles, fonts and requests only from the site itself. There is no inline script or style, and no `eval`. Camera and microphone are allowed only for the site's own pages. Voice commands can only run items from a fixed list, and the one external link needs a click to confirm. Gesture files are size-limited and checked before use. The rules live in `config/security.mjs`, and the tests check that `vercel.json`, the generated `_headers` file and the page itself all match.

**Tests.** 38 logic tests, 31 page checks (run in a simulated browser) and 14 security and build checks. The simulated browser has no camera, hand tracking or speech, so those parts must be tried by hand in a real browser.

## Credits

Built on open-source work: MediaPipe (Apache 2.0), Atkinson Hyperlegible by the Braille Institute (SIL Open Font License), jsdom and esbuild for tests. Details are in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## License

MIT. See [LICENSE](LICENSE).
