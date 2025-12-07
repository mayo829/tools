# Weather Fetcher Tool

This n8n workflow fetches current weather for multiple cities (configured in the **Set Configuration** node), logs the data to Supabase, and sends email summaries and alerts.

---

## Setup

### 1. Project Folder
Create a project folder and navigate into it:

```bash
mkdir weather_fetcher
cd weather_fetcher
```
- Make sure you have Node.js and n8n installed. You can get them using this command:
```text
npm install n8n node
```
- Run this to install dotenv
```text
npm install -g dotenv
```

### API setup & key config
- Create a .env file and add all of your api keys/environment to it. If you need help with this step, google how to get the specific key. You will need this environment:
```text
SUPABASE_API_KEY=your_supabase_api_key
SUPABASE_URL=your_supabase_url
OPENWEATHER_API_KEY=your_openweather_api_key
OPENAI_API_KEY=your_openai_api_key
GOOGLE_APP_PASS=your_google_app_password
```
- Make a script file (I named mine run_n8n.js) as follows to automatically set up your environment and run n8n
```text
require('dotenv').config({ path: 'path/to/.env' });
require('child_process').execSync('n8n', { stdio: 'inherit' });
```
- Run the script
```text
node run_n8n.js
```
- If this is your first time running n8n, create an account and follow the setup instructions.
- On the n8n home page, click Create Workflow.
- Click the three dots (...) in the top-right corner and select Import from File.
- Choose the service_assessment.json file (your workflow).
- Run the workflow manually using the Run Workflow button on the first node, or let it trigger automatically via the Schedule Trigger at 8 AM.