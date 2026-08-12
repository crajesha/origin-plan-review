# Plan Review Assistant

A small, self-contained chat tool for reviewing **your own** Origin drywall
experimental plan before your interview. It's a single `index.html` file —
no build step, no server.

## What it does

- Embeds the full text of your submitted plan directly in the page.
- Every answer is generated with a system prompt that restricts the model
  to that text only — it will tell you "that's not covered in your document"
  rather than inventing anything.
- This is a **study aid**, not something to present as part of your
  assessment submission. It exists so you can quiz yourself and rehearse
  explaining your own reasoning out loud.

## Running it locally

Just open `index.html` in a browser. That's it.

Note: the page calls `https://api.anthropic.com/v1/messages` directly from
the browser. If you're just using it inside Claude.ai as an artifact, that
call is already routed and works out of the box. If you deploy this
standalone (e.g. GitHub Pages) and it needs its own API key, you'll need to
add a small backend proxy — never put a real Anthropic API key in
client-side JS in a public repo.

## Pushing to GitHub yourself

Don't paste API keys or tokens into a chat with any AI assistant, including
this one — treat them like passwords. To push this folder yourself:

```bash
cd plan-review-assistant
git init
git add .
git commit -m "Add plan review assistant"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

If you want it live on the web (e.g. to open on your phone before the
interview), enable **GitHub Pages** in the repo settings pointing at the
`main` branch root — no extra config needed since it's a static file.

## Files

- `index.html` — the whole app (UI + embedded document text + chat logic)
- `plan.txt` — plain-text extract of your Word doc, kept for reference
