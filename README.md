# Interview Prep — Golang Q&A

A single-file, mobile-friendly static web page with 82 curated Golang interview
questions and answers (including REST, gRPC, and networking topics). Built to read
comfortably on both phone and laptop.

## Features
- Medium-sized, comfortable reading typography (Fraunces + Newsreader + JetBrains Mono)
- Tap any question to expand / collapse the answer
- Live search across all questions and answers
- Syntax-highlighted Go code blocks with a one-tap **Copy** button
- "Expand all / Collapse all" toggle
- Category selector with **Golang** active; **Kafka** and **Kubernetes** are shown
  as "Soon" — ready for you to extend later (see below)
- No external build step, no frameworks, no dependencies — just one HTML file

## How to host on GitHub Pages
1. Create a new repository on GitHub (e.g. `interview-prep`).
2. Upload `index.html` to the root of the repo (commit it).
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Pick branch `main` and folder `/ (root)`, then **Save**.
6. After ~1 minute your page is live at:
   `https://<your-username>.github.io/<repo-name>/`

## How to add Kafka / Kubernetes later
Open `index.html` and find the `const DATA = [...]` line near the bottom.
Each question is an object like:

```js
{
  "num": 1,                       // or null for an "extra" question
  "q": "Your question text?",
  "parts": [
    ["p",  "A paragraph of explanation."],
    ["ul", ["bullet one", "bullet two"]],
    ["code", "package main\n\nfunc main() {}"],
    ["h",  "A small sub-heading"]
  ]
}
```

To add new topics, you can give each question a `"cat"` field ("go" / "kafka" / "k8s"),
fill in Kafka/Kubernetes questions the same way, remove the `soon`/`disabled` from those
category buttons in the HTML, and filter `DATA` by the active category in the
`currentList()` function. The structure is already laid out for this.
