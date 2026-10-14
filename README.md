# SignBridge

**Helping people who sign and people who speak understand each other.**

SignBridge is a free website that turns hand signs into written words and spoken voice. All you need is a computer with a webcam.

## The problem

Most people never learn sign language. This makes simple moments hard for people who sign, like talking to a shop assistant, a bank teller, a nurse or a new classmate. They often have to ask someone else to speak for them, or write everything down.

## How SignBridge helps

- **Signs become words.** Show a sign to your webcam and the word appears on the screen.
- **Words become speech.** Press one button and the words are read out loud, so the other person can hear them.
- **It learns your signs.** Show it each sign a few times, and it will recognize it next time. You choose the signs, such as letters or everyday words.
- **It guides you.** It tells you what it sees in plain words, like "I see B, and I'm very sure" or "Move a little closer to the camera".
- **It can help by voice or typing.** Say or type a short request like "hello" or "help". It only does a few safe things, and it always asks before opening a website.

## Who it is for

- People who use sign language and want more people to understand them
- Family, friends, teachers and shop or office staff who don't know sign language
- Schools and community groups learning about accessibility

## Your privacy

- Your camera video stays on your own computer. It is never saved or sent anywhere.
- The camera and microphone only turn on when you press Start.
- Your conversation disappears when you close the page.
- Some browsers send your voice to their own service to turn it into text. That is the browser's feature, not ours.

## What it can't do yet

SignBridge is an early version. It only recognizes the signs you teach it, using one hand at a time. It does not understand full sign language, which also uses movement, facial expressions and sentence structure. Please think of it as a helper, not a replacement for a human interpreter.

## How to try it

1. Open SignBridge in Chrome or Edge.
2. Go to **Sign to speech** and press **Start camera**.
3. Open **Teach gestures**, type a name like `A`, and press **Record sign**. Record each sign twice, and teach at least two different signs.
4. Press **Start recognition** and begin signing.
5. Press **Speak text** to hear your words.

## For developers

Everything runs in the browser, so there is no server to manage and no passwords or keys to set up. You need [Node.js](https://nodejs.org) 20 or newer.

```
npm install
npm start
```

Then open http://localhost:8000. Run `npm test` to check everything works.

More details:
- [How it works](docs/how-it-works.md)
- [How to put it online](docs/deploy.md)

## Credits and license

Built with open-source tools: MediaPipe (hand tracking) and Atkinson Hyperlegible (an easy-to-read font by the Braille Institute). See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for details.

Free to use under the MIT license. See [LICENSE](LICENSE).
