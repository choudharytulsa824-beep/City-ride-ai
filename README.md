# City AI — real AI starter

This project is a working web-app starter. It uses a small Node.js server to call Google's Gemini API. The API key stays on the server and is never sent to the browser.

## Important
- The app will not answer with real AI until you add your own Gemini API key and run the server.
- Google AI Studio may offer a free tier for supported models, with quotas and eligibility limits. Check current pricing/limits before using it with other people.
- Do not publish your API key, share screenshots showing it, or put it into `public/index.html`.
- This is a starter, not yet a Play Store Android app. Public launch needs hosting, privacy policy, abuse controls/rate limits, testing, and possibly costs.

## Run on a laptop
1. Install Node.js 20 or newer from the official Node.js website.
2. Extract this ZIP into a folder.
3. Open a terminal/command prompt inside the extracted `city-ai-real` folder.
4. Create a file named `.env` by copying `.env.example`; put your API key after `GEMINI_API_KEY=`.
5. Start the server:
   - `npm start` (the script loads `.env` using Node's `--env-file` support)
6. Open `http://localhost:3000` in a browser on that same laptop.

For phone testing on the same Wi-Fi, use your laptop's local IP and port 3000, for example `http://192.168.1.5:3000` (replace with the laptop's actual local IP). Firewall/network settings may need adjustment.

## Get an API key
Open Google AI Studio: https://aistudio.google.com/app/apikey
Create an API key and keep it private. Check the official Gemini API docs and pricing:
- https://ai.google.dev/gemini-api/docs/get-started
- https://ai.google.dev/gemini-api/docs/pricing

## Hosting
To make it work from anywhere, deploy the Node.js project to a trusted Node hosting service and add `GEMINI_API_KEY` and `GEMINI_MODEL` as private environment variables in the host dashboard. Do not put your API key in the frontend. Add request limits and monitoring before inviting public users.

## Troubleshooting
- `AI API error (400/403/429)`: key/model/permission/quota may be wrong or the free quota may be exhausted. Check Google AI Studio.
- `GEMINI_API_KEY set nahi hai`: set the environment variable or `.env` loading in your hosting environment. This minimal project deliberately does not read `.env` itself; see local setup below.

### Local `.env` note
Node.js does not automatically load `.env` in every version/setup. Easiest: use a recent Node version that supports `--env-file`, then run:
`node --env-file=.env server.js`
Or use a shell environment variable. On Windows PowerShell:
`$env:GEMINI_API_KEY="YOUR_KEY"; node server.js`
On macOS/Linux:
`GEMINI_API_KEY="YOUR_KEY" node server.js`

The included `npm start` script uses Node's `--env-file` option. If that option is unsupported, update Node.js or set the environment variable directly as shown above.
