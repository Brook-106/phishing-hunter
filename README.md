# Phishing Hunter

A fast, browser-based game that trains your eye for phishing emails. Read each message, check the sender and the link, and decide: **Safe** or **Phish**? Beat the timer, keep your streak, and learn the clue you missed after every answer.

![Phishing Hunter cover](assets/cover.png)

## Play it

- **itch.io:** https://brook-106.itch.io/phishing-hunter
- **GitHub Pages:** https://brook-106.github.io/phishing-hunter/

No install, no account, no tracking. It runs entirely in your browser on desktop and mobile.

## How to play

1. Press **Start hunting**.
2. Read the email: look at the **sender name**, the **sender address**, the message text, and the **"Link goes to"** line that shows where the link really points.
3. Tap **Safe** or **Phish** before the timer bar runs out.
4. Read the explanation that appears after each answer, then continue to the next message.
5. You have **3 lives**. A wrong answer or a timeout costs one. When they are gone, the game ends and your score is shown.

### Controls

| Action | Keyboard | Touch / mouse |
| --- | --- | --- |
| Mark as Safe | Left arrow or `S` | Safe button |
| Mark as Phish | Right arrow or `P` | Phish button |
| Next message | `Enter` | Next message button |

### Scoring

- A correct answer gives **10 points**, plus **2 points per streak step** (up to a streak of 5), plus **bonus points equal to the seconds left** on the timer.
- The timer starts at **12 seconds** and gets **1 second shorter every 3 messages**, down to a minimum of **5 seconds**.
- Your best score is saved in your browser's local storage on your device.

## What you will learn

Every explanation points at a real warning sign. The messages in the game cover the most common ones:

- **Lookalike domains**, such as `paypa1` (digit one instead of the letter l), `micros0ft` (zero instead of o) or a capital `I` in place of `l`.
- **Fake urgency**, like "your account will be blocked today" or "confirm within 24 hours".
- **Mismatched or shortened links** that hide the real destination.
- **Requests for money, gift cards or bank details** through an email link.
- **Impersonation from free mail addresses**, for example a "CEO" writing from a Gmail account.
- **What safe mail looks like**: exact official domains, links that stay on the same domain, nothing urgent, and no request for your password or card.

## Run it locally

The game is a single static file with no dependencies and no build step.

```bash
git clone https://github.com/Brook-106/phishing-hunter.git
cd phishing-hunter
```

Then either open `index.html` in your browser, or serve it locally:

```bash
python3 -m http.server 8000
```

and visit `http://localhost:8000`.

## Project structure

```text
phishing-hunter/
├── index.html      # the whole game: markup, styles and logic
├── assets/
│   └── cover.png   # cover image used in this README and on itch.io
├── LICENSE
└── README.md
```

## Add your own messages

All messages live in the `M` array near the top of the script in `index.html`. Each message is one object:

```js
{
  f: "PayPal Support",              // sender display name
  a: "service@paypa1-secure.com",   // sender address
  s: "Your account has been limited", // subject
  b: "Message body text...",        // body
  l: "Restore my account",          // link text ("" for no link)
  u: "http://paypa1-secure.com/verify", // where the link really goes ("" for no link)
  p: true,                          // true = phishing, false = safe
  w: "Why this is phishing or safe" // explanation shown after the answer
}
```

The game currently ships with 16 messages, 8 phishing and 8 safe, shuffled each run. Add more objects to the array to extend it.

## Built with

- HTML, CSS and vanilla JavaScript, with no frameworks and no external libraries
- IBM Plex Sans and IBM Plex Mono, loaded from Google Fonts, with system font fallbacks
- Light and dark mode that follows your device setting

All sender names, addresses and links in the game are fictional examples made for training. Brand names are used only to illustrate common scams, and no real emails are sent or collected.

## AI disclosure

The code, the email scenarios and the cover image were created with the help of an AI assistant (Claude by Anthropic) and reviewed and published by the author.

## License

Released under the [MIT License](LICENSE).

## Author

Made by **Adithyan** ([@Brook-106](https://github.com/Brook-106)), a cybersecurity student.
