# 🔐 Account Login Activity Checker

A Streamlit app that reads **your own** sign-in and security-alert emails and shows
where your account was signed in. Powered by Gemini Flash.

Upload `.eml` or `.txt` files (or paste an email's text) and the app lists, for each
alert:

- the service (Google, Facebook, Netflix, ...)
- the event (new sign-in, password changed, failed login, ...)
- time, device, browser/app, location and IP address
- whether it looks suspicious, with a short reason

It also gives a short summary and a few security steps.

> ⚠️ **Limits.** The app shows sign-ins that were *reported by alert emails*. It cannot
> see live sessions. To see or end active sessions, open each service's security
> settings. AI can make mistakes, and alert emails can be fake (phishing).

## Privacy

- Use only your own emails.
- The email text is sent to Google's Gemini API for analysis. Remove one-time codes
  and anything sensitive first.
- The app does not store your files or results.
- The app never asks for your email password and never logs in to your mailbox.

## Run locally

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
pip install -r requirements.txt
```

Create `.streamlit/secrets.toml` (do **not** commit this file):

```toml
GEMINI_API_KEY = "your_gemini_api_key_here"
```

Start the app:

```bash
streamlit run app.py
```

Get a Gemini API key at <https://aistudio.google.com/apikey>.

## How to get a login-alert email as a file

- **Gmail:** open the email, click the three dots, then **Download message** (.eml).
- **Outlook:** open the email, then **File → Save as** (choose .eml or .txt).
- Or simply copy the text of the email and paste it into the text box.

## Deploy on Streamlit Community Cloud

1. Push this repo to GitHub.
2. Go to <https://share.streamlit.io> and click **Create app**.
3. Choose your repo, branch `main`, main file `app.py`.
4. Open **Advanced settings → Secrets** and paste:
   ```toml
   GEMINI_API_KEY = "your_gemini_api_key_here"
   ```
5. Click **Deploy**.

## Changing the AI model

The default is `gemini-3.5-flash`. To use another Gemini Flash model without editing
code, add this to your secrets:

```toml
GEMINI_MODEL = "model-name-from-ai.google.dev"
```

## Files

- `app.py` - the Streamlit app
- `requirements.txt` - Python dependencies
- `README.md` - this file
