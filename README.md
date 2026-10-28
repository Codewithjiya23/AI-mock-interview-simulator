# 🎤 AI Mock Interview Simulator

Practice job interviews with an AI interviewer. Built with **Python**, **Streamlit**, and the **Google Gemini API**.

## Features

- Enter a job role and (optionally) paste a job description
- Choose a difficulty level: Beginner, Intermediate, or Advanced
- Get 5 AI-generated interview questions, asked one at a time
- Receive a score, strengths, improvement tips, and a sample answer after each response
- Get a final performance summary with an improvement plan
- Start a new interview at any time

## Project files

| File | Purpose |
|------|---------|
| `app.py` | The Streamlit app |
| `requirements.txt` | Python packages Streamlit Cloud installs |
| `README.md` | This guide |
| `.gitignore` | Keeps secret files out of GitHub |

## Step 1: Get a free Gemini API key

1. Go to https://aistudio.google.com and sign in with a Google account.
2. Click **Get API key**, then **Create API key**.
3. Copy the key and keep it private. Never paste it into `app.py`, GitHub, or a chat.

## Step 2: Upload the project to GitHub

1. Sign in at https://github.com (create a free account if needed).
2. Click the **+** icon at the top right, then **New repository**.
3. Name it `mock-interview-simulator`, choose **Public**, and click **Create repository**.
4. Click **uploading an existing file**.
5. Drag in `app.py`, `requirements.txt`, `README.md`, and `.gitignore`.
6. Click **Commit changes**.

Do **not** upload any file that contains your API key.

## Step 3: Deploy on Streamlit Community Cloud

1. Go to https://share.streamlit.io and click **Continue with GitHub**.
2. Click **Create app** (or **New app**), then choose **Deploy a public app from GitHub**.
3. Select your repository `mock-interview-simulator`, branch `main`, and main file path `app.py`.
4. Click **Advanced settings**.
5. In the **Secrets** box, paste this (use your real key):

   ```toml
   GEMINI_API_KEY = "paste-your-key-here"
   ```

6. Click **Save**, then **Deploy**. Wait a few minutes for the app to start.

### Changing the secret later

Open your app on Streamlit Cloud, click **Manage app** (bottom right), then **Settings**, then **Secrets**, edit, and click **Save**.

## Run on your own computer (optional)

1. Install Python 3.10 or newer.
2. In a terminal inside the project folder, run:

   ```bash
   pip install -r requirements.txt
   ```

3. Create a folder named `.streamlit` and inside it a file named `secrets.toml` containing:

   ```toml
   GEMINI_API_KEY = "paste-your-key-here"
   ```

4. Start the app:

   ```bash
   streamlit run app.py
   ```

The `.gitignore` file stops `secrets.toml` from being uploaded to GitHub.

## Troubleshooting

| Problem | Fix |
|---------|-----|
| "The Gemini API key is missing" | Add `GEMINI_API_KEY` in Streamlit Cloud: **Manage app** > **Settings** > **Secrets** |
| "Gemini request failed" with a 429 message | You hit the free rate limit. Wait a minute and try again |
| "API key not valid" | Create a new key in Google AI Studio and update the secret |
| Model not found | Add `GEMINI_MODEL = "model-name"` to Secrets, using a current name from the Gemini API docs |

## Security

The API key lives only in Streamlit Secrets. The code reads it with `st.secrets["GEMINI_API_KEY"]`, so it is never stored in GitHub.
