# Fintab PKR — Personal Finance Dashboard

A full-featured personal finance app in Pakistani Rupees with:
- 📊 Dashboard with spending charts
- 📈 Net worth timeline (6M / 12M / 24M)
- 🧾 Expense tracking & categorisation
- ⚙️ Budget management with custom alerts
- 💹 Investment portfolio tracker
- ✨ **AI Financial Advisor** (powered by Claude — works via secure serverless function)
- ⬇️ CSV export for all data

---

## 🚀 Deploy to Vercel in 5 minutes

### Step 1 — Get your Anthropic API key
1. Go to https://console.anthropic.com/
2. Sign up / log in
3. Click **API Keys** → **Create Key**
4. Copy the key (starts with `sk-ant-...`)

### Step 2 — Push to GitHub
```bash
cd fintab
git init
git add .
git commit -m "Initial commit"
# Create a repo on github.com, then:
git remote add origin https://github.com/YOUR_USERNAME/fintab.git
git push -u origin main
```

### Step 3 — Deploy on Vercel
1. Go to https://vercel.com and sign in with GitHub
2. Click **Add New → Project**
3. Import your `fintab` GitHub repo
4. Click **Environment Variables** and add:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** your key from Step 1
5. Click **Deploy**

That's it! Vercel gives you a live URL like `https://fintab-xyz.vercel.app`

---

## 💻 Run locally

```bash
cd fintab
npm install
cp .env.example .env.local
# Edit .env.local and paste your ANTHROPIC_API_KEY
npm run dev
# Open http://localhost:3000
```

---

## 🔐 How the AI security works

Your API key is stored **only** in Vercel's environment variables — never in the browser.

When you chat with the AI advisor:
1. Browser sends your message to `/api/chat` (your own serverless function)
2. The serverless function adds your secret API key and calls Anthropic
3. Only the reply comes back to the browser

Your key is never exposed to users.

---

## 📁 Project structure

```
fintab/
├── pages/
│   ├── index.js        ← Main app (all views)
│   └── api/
│       └── chat.js     ← Secure AI proxy (serverless)
├── styles/
│   └── globals.css     ← Theme & base styles
├── .env.example        ← Copy to .env.local with your key
├── vercel.json         ← Vercel deployment config
└── package.json
```
