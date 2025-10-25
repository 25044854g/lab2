# Project Writeup: Note-Taking App with Translation & Cloud Integration 

## Aims 

 - Develop a note-taking application with translation functionality using Google Cloud Translate API 

- Integrate cloud database storage using Supabase

 - Deploy the application to Vercel for public access 

- Implement proper environment management for API keys and sensitive configurations 

## Process Overview 

### 1. Environment Setup First, I configured the Python environment and installed required dependencies. 

The project required a mix of web framework, database, and API integration packages: ```json {  "packageList": [                                        "blinker==1.9.0",                                                    "click==8.2.1",                                                  "Flask==3.1.1",                                                     "flask-cors==6.0.0",                                                    "Flask-SQLAlchemy==3.1.1",                                    "gunicorn==21.2.0",                                          "itsdangerous==2.2.0",                                           "Jinja2==3.1.6",                                             "MarkupSafe==3.0.2",                                          "SQLAlchemy==2.0.41",                                      "typing_extensions==4.14.0",                                   "Werkzeug==3.1.3",                                                     "google-cloud-translate==3.11.1",                                  "supabase==2.22.1",                                                   "psycopg2-binary==2.9.9",                                              "python-dotenv==1.0.0",                                         "openai==1.3.0"  ] } ```
Installation command: 
```bash pip install -r requirements.txt ``` 

### 2. API Configuration 

#### Google Cloud Translate Setup 
I chose Google Cloud Translate API for the translation functionality. This required: 
- Creating a project in Google Cloud Console 

- Enabling the Translate API 

- Generating service account credentials 

  ![](C:\Users\Jennifer\Desktop\sem1\COMP5241\Lab2\fbe16e2d4df3cd4462228012b21e56e7.png)

  ![](C:\Users\Jennifer\Desktop\sem1\COMP5241\Lab2\44af9e6ce443c67b0f44a1edd5ff3ded.png)

 #### Supabase Integration

For cloud database storage, I set up Supabase: 
- Created a new Supabase project 
- Configured the PostgreSQL database - Generated API keys for authentication

![](C:\Users\Jennifer\Desktop\sem1\COMP5241\Lab2\3b621395d78ea7607f49081a25e80e79.png)

![](C:\Users\Jennifer\Desktop\sem1\COMP5241\Lab2\0456ce3a2d645bfc2e1b6b646f36cc09.png)

### 3. Environment Variables Configuration 
To securely manage sensitive information, I set up environment variables: 
```powershell # Supabase configuration $env:SUPABASE_URL="https://eefdegomerhkcifhkvyu.supabase.co" $env:SUPABASE_KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImVlZmRlZ29tZXJoa2NpZmhrdnl1Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjExODQ0NTYsImV4cCI6MjA3Njc2MDQ1Nn0.x8yY_5ZGaWk0LkywxpJ9Td2rcq6ceiZkv7GAgS9L2ek" $env:SUPABASE_DB_URL="postgresql://postgres:zyh1314520@db.eefdegomerhkcifhkvyu.supabase.co:5432/postgres" # Google Cloud configuration $env:GOOGLE_APPLICATION_CREDENTIALS="C:\Users\Jennifer\Desktop\note-taking-app-updated-LianaZeng0827\note-translator-key.json" $env:GOOGLE_CLOUD_PROJECT="even-dragon-475911-d8" ```
### 4. Application Testing & Deployment 
After configuration, I tested the application locally: 
```bash python src/main.py ```
Verified the server was running correctly:
```powershell Invoke-WebRequest -Uri "http://localhost:3000/api/health" -Method GET ``` 
Once local testing was complete, I deployed the application to Vercel. 
## Challenges & Lessons Learned 
The most significant challenge encountered was persistent failures when testing the translation and note generation features. After extensive troubleshooting of configuration settings, API keys, and network requests, I discovered the issue was due to the computer's firewall settings blocking outgoing API calls. This highlights the importance of checking system-level configurations alongside application-level settings when debugging connectivity issues. 
This experience wasted several hours of development time but taught me to consider environmental factors beyond the application code itself when troubleshooting integration issues with external services. 
## Insights 
- Proper environment variable management is crucial for both security and maintainability
- Screenshots of configuration steps are valuable for future reference and team collaboration 
- Testing connectivity to external APIs should be done early in the development process 
- Firewall and network security settings can impact application functionality in unexpected ways 
## Tips for Future Projects 
- Implement incremental testing, verifying each integration step before moving to the next 
-  Create a dedicated testing script for API connectivity verification 
-  Document all configuration steps immediately as they're implemented 
-  Use `.env` files with `python-dotenv` for local development to maintain consistency 
-  Regularly commit working versions to version control to enable rollbacks when issues arise