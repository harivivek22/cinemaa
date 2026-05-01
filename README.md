# సినిమా క్రమం — Deploy Guide

## What's in this folder

```
cinemaa/
├── public/
│   ├── index.html   ← the whole game UI
│   ├── style.css    ← all styling
│   ├── app.js       ← game logic, timer, drag & drop
│   └── puzzles.js   ← your puzzle database (edit this!)
└── vercel.json      ← Vercel deployment config
```

---

## Deploy to Vercel (FREE — takes 5 minutes)

### Step 1 — Create a GitHub account
Go to https://github.com and sign up if you don't have one.

### Step 2 — Create a new GitHub repository
1. Click the **+** button → **New repository**
2. Name it: `cinemaa`
3. Set it to **Public**
4. Click **Create repository**

### Step 3 — Upload these files
1. Click **uploading an existing file**
2. Drag and drop ALL the files from this folder:
   - `public/index.html`
   - `public/style.css`
   - `public/app.js`
   - `public/puzzles.js`
   - `vercel.json`
3. Click **Commit changes**

### Step 4 — Deploy on Vercel
1. Go to https://vercel.com and sign up with your GitHub account
2. Click **Add New Project**
3. Select your `cinemaa` repository
4. Click **Deploy** — that's it!

Your game will be live at: `https://cinemaa.vercel.app` (or similar)

---

## Adding new puzzles

Open `public/puzzles.js` and add a new entry to the `PUZZLES` array:

```js
// Puzzle 31
[
  { name: "Movie Name 1", director: "Director Name", year: 1999 },
  { name: "Movie Name 2", director: "Director Name", year: 2010 },
  { name: "Movie Name 3", director: "Director Name", year: 2018 },
],
```

Rules:
- All three movies must have **different years**
- Order doesn't matter — the game sorts them automatically
- After editing, commit the file to GitHub — Vercel auto-redeploys in ~30 seconds

---

## Connecting puzzle submissions (optional upgrade)

Right now submissions are logged to the browser console.
To collect them for real, either:

### Option A — Google Forms (easiest, free)
1. Create a Google Form with fields: Name, Email, Movie 1 title/director/year, Movie 2, Movie 3, Note
2. In `app.js`, replace the `console.log('Submission:' ...)` line with:
   ```js
   window.open('YOUR_GOOGLE_FORM_URL', '_blank');
   ```

### Option B — Supabase (real database, free tier)
1. Create a free account at https://supabase.com
2. Create a table called `submissions`
3. Replace the console.log with a `fetch()` POST to your Supabase REST API

---

## Custom domain (optional)

In Vercel dashboard → your project → Settings → Domains → Add your domain.
If you buy `cinemaa.game` or `sinemakramam.com`, point it here.

---

## Leaderboard (real friends, optional upgrade)

The leaderboard currently shows demo data.
To make it real with actual friends:
1. Add Firebase or Supabase
2. On game completion, POST `{ puzzleIdx, correct, timeMs, playerName }` to your DB
3. Fetch today's results and render them in `renderLeaderboard()`

---

## That's it!

Total cost to run: **₹0** (Vercel free tier handles up to 100GB bandwidth/month)
