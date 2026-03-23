# Ayen — South Sudan Education Bot

Ayen is a free AI education assistant delivered through Facebook Messenger. Students in South Sudan can chat with Ayen using Facebook's free mode — no data required. Ayen helps with Math, Science, Social Studies, English, essay writing, and general knowledge — for all levels from Grade 1 to university.

---

## How to deploy Ayen in 4 steps

---

### Step 1 — Get your Groq API key (free)

1. Go to **https://console.groq.com**
2. Sign up for a free account
3. Click **API Keys** → **Create API Key**
4. Copy the key — you will need it in Step 4

Free tier: **14,400 requests/day** (~1,440 users at 10 messages each)

---

### Step 2 — Create your Facebook App

1. Go to **https://developers.facebook.com**
2. Click **My Apps** → **Create App** → choose **Business**
3. Add the **Messenger** product
4. Create or connect a **Facebook Page** (name it "Ayen" or "Ayen South Sudan")
5. Generate a **Page Access Token** — copy it

---

### Step 3 — Deploy to Render.com (free)

1. Push this project to a GitHub repository
2. Go to **https://render.com** → **New** → **Web Service**
3. Connect your GitHub repo
4. Set:
   - **Build Command:** `npm install`
   - **Start Command:** `node index.js`
5. Add these **Environment Variables** (from your `.env.example`):
   - `PAGE_ACCESS_TOKEN` — from Step 2
   - `VERIFY_TOKEN` — any secret word you choose (e.g. `ayen2024`)
   - `GROQ_API_KEY` — from Step 1
6. Click **Deploy** — Render gives you a URL like `https://ayen-bot.onrender.com`

---

### Step 4 — Connect webhook to Facebook

1. In your Facebook Developer App → **Messenger** → **Settings**
2. Click **Add Callback URL**
3. Enter: `https://ayen-bot.onrender.com/webhook`
4. Enter your **Verify Token** (same word you used in Step 3)
5. Click **Verify and Save**
6. Under **Webhooks**, subscribe to: `messages`

---

## Test Ayen

Go to your Facebook Page → click **Send Message** and try:

- `Hello`
- `I am in grade 7. Can you help me understand fractions?`
- `Write me an essay about the importance of education in South Sudan`
- `What is photosynthesis? Explain simply`
- `Solve for x: 2x + 4 = 14, show your working`
- `Give me feedback on my essay: [paste essay here]`

---

## Project structure

```
ayen-bot/
├── index.js          ← All bot logic (webhook + Groq + memory)
├── package.json      ← Node.js dependencies
├── .env.example      ← Environment variables template
├── .env              ← Your secrets (NEVER share or commit this)
└── README.md         ← This file
```

---

## Costs

| Stage | Cost |
|-------|------|
| Launch (Groq free tier) | $0/month |
| Growing (Groq paid) | ~$20/month for ~15,000 users/month |
| Scale (self-hosted Llama 3) | ~$20–50/month, unlimited users |

---

## What Ayen can do

- Answer questions in Math, Science, Social Studies, English, General Knowledge
- Write structured essays on any topic at the right grade level
- Give feedback on a student's own writing
- Explain concepts using South Sudanese examples (Nile, Juba, cattle, sorghum)
- Remember the conversation context (last 10 exchanges)
- Adapt language to Grade 1 through University level
- Motivate and encourage students who are struggling

---

*Education is a right, not a privilege. Built for the students of South Sudan.*
