# WhatsApp AI Website Generator 🚀

An automated AI-powered website generation system that accepts requests via WhatsApp and delivers fully deployed websites within minutes. Built for the ElevateBox Internship Screening Task.

## 📖 Overview
The goal is to build a zero-friction website builder. A user sends a simple message on WhatsApp (e.g., "Build me a restaurant website"), and the system automatically extracts requirements using AI, generates a professional website using React + Tailwind CSS, and deploys it to a live Netlify URL.

## 🛠️ Tech Stack
- **Backend:** FastAPI (Python)
- **AI Brain:** Google Gemini 1.5 Flash
- **WhatsApp Integration:** Twilio WhatsApp Sandbox
- **Site Engine:** Jinja2 + Tailwind CSS (Static HTML/React components)
- **Deployment:** Netlify API
- **Tunneling:** ngrok (to expose local server to Twilio)

## 🚀 Setup Instructions

### 1. Prerequisites
- Python 3.10+
- [ngrok](https://ngrok.com/) (Included in the root folder as `ngrok.exe`)
- A [Twilio Account](https://www.twilio.com/) (Free trial works)
- A [Netlify Account](https://www.netlify.com/)

### 2. Installation
```bash
# Clone the repository
git clone <your-repo-url>
cd "whatsapp ai"

# Install Python dependencies
pip install -r requirements.txt
```

### 3. Environment Variables
Create a `.env` file in the root directory and add your credentials:
```env
GEMINI_API_KEY=your_gemini_api_key
NETLIFY_AUTH_TOKEN=your_netlify_token
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
PORT=8001
```

### 4. Running the Project (Two Terminals Required)

**Terminal 1: Start the Backend**
```bash
python main.py
```

**Terminal 2: Start the Tunnel**
```bash
./ngrok.exe http 8001
```
*Note: Copy the `https://...` Forwarding URL provided by ngrok.*

### 5. Connecting to WhatsApp
1. **Twilio Sandbox:** In the Twilio Console, go to **Messaging > Try it Out > Send a WhatsApp Message**. Follow the steps to join the sandbox.
2. **Webhook Setup:** Go to **Messaging > Settings > WhatsApp Sandbox Settings**.
3. **Configure URL:** In the "When a message comes in" field, paste your ngrok URL and append `/whatsapp`.
   *Example:* `https://a1b2-c3d4.ngrok-free.app/whatsapp`
4. **Save:** Click Save at the bottom.

## 🧪 How to Test
1. Open WhatsApp and send a message to your Twilio Sandbox number.
2. **Request:** `"Create a modern dark-themed portfolio for a creative developer named Alex."`
3. **Response:** You will receive an immediate acknowledgment, followed by a live Netlify URL once the site is deployed.

## 🛠 Troubleshooting
- **Authentication Error:** Ensure your `TWILIO_ACCOUNT_SID` starts with `AC`. Avoid using API Key SIDs starting with `SK` or `US`.
- **URL not sent to WhatsApp:** Check your terminal logs for any errors from the Twilio API. Ensure your `TWILIO_AUTH_TOKEN` is revealed using the "Show" button in the console.
- **ngrok issues:** If you restart ngrok, you **must** update the Webhook URL in the Twilio Console with the new address.

---
**Developer:** Allegapally Manaswini
