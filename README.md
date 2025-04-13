git add README.md
git commit -m "Add README with setup and deployment instructions"
git push origin main
// === Nomadia MVP Backend Setup ===
// Project: Nomadia (Flight Search Aggregator with Anonymous Browsing)
// Environment: Node.js + Playwright + MongoDB

// STEP 1: Install Dependencies
// Run in terminal:
// npm init -y
// npm install express cors dotenv mongoose puppeteer-extra puppeteer-extra-plugin-stealth

// STEP 2: Set Up Express Server (index.js)
const express = require('express');
const cors = require('cors');
const dotenv = require('dotenv');
dotenv.config();

const app = express();
app.use(cors());
app.use(express.json());

// Test Route
app.get('/', (req, res) => {
  res.send('Nomadia API Running');
});

// Placeholder for search route
const searchRoute = require('./routes/search');
app.use('/api/search', searchRoute);

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));

// === README.md ===
/*
# ✈️ Nomadia – Anonymous Flight Search API

Nomadia is a privacy-first backend service that scans multiple online platforms for the cheapest airline tickets. It uses stealth browsing to avoid dynamic pricing manipulation triggered by cookies and repeat searches.

## 🚀 Features

- 🔍 Aggregates flight deals from:
  - Kayak
  - WayAway
  - Kiwi.com
- 🛡️ Stealthy and anonymous web scraping using Puppeteer + Stealth plugin
- 📦 RESTful API with Express
- 📤 Ready for deployment on Railway or other cloud platforms

## 📦 Installation

```bash
git clone https://github.com/your-username/nomadia-backend.git
cd nomadia-backend
npm install
```

## ⚙️ Environment Variables

Create a `.env` file in the root directory:

```env
PORT=5000
NODE_ENV=production
```

## 🧪 Usage

### Start the server locally:

```bash
node index.js --no-sandbox
```

### API Endpoint:

```
POST /api/search
```

#### Body parameters (JSON):

```json
{
  "from": "NYC",
  "to": "LAX",
  "date": "2025-04-28"
}
```

#### Response format:

```json
[
  {
    "source": "Kayak",
    "airline": "Delta",
    "price": "$220",
    "depart": "6:00 AM",
    "arrive": "9:00 AM",
    "link": "https://..."
  }
]
```

## 🛠 Deployment (Railway Recommended)

1. Push this repo to GitHub
2. Go to [https://railway.app](https://railway.app)
3. Start a new project → **Deploy from GitHub**
4. Add Environment Variables:
   - `PORT=5000`
   - `NODE_ENV=production`
5. Set Start Command:
   ```bash
   node index.js --no-sandbox
   ```

## 📄 License

MIT License © 2025 [Your Name]
*/
