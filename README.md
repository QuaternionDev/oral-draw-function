# oral-draw-function
 
Backbone of the [Oral Draw](https://github.com/QuaternionDev/oral-draw) system.
 
## What it does
 
This function is the backbone of the Oral Draw system. It runs on a schedule (every 5 minutes by default) and processes sessions whose deadline has passed:
 
- If volunteers signed up → picks one at random, marks the session as `picked`, and saves the winner's name and user ID
- If nobody signed up → marks the session as `failed`
- Sessions that are already `picked`, `failed`, or `locked` are ignored
 
## Environment variables
 
| Variable | Description |
|---|---|
| `APPWRITE_ENDPOINT` | Appwrite API endpoint (e.g. `https://cloud.appwrite.io/v1`) |
| `APPWRITE_PROJECT_ID` | Your Appwrite project ID |
| `DATABASE_ID` | Your Appwrite database ID |
| `APPWRITE_API_KEY` | API key with `databases.read`, `databases.write`, `rows.read`, `rows.write` scopes |
 
## Requirements
 
- Node.js 21 or higher
- Appwrite Cloud (free tier is sufficient)
- A `sessions` and `signups` collection — see the [main repo README](https://github.com/QuaternionDev/oral-draw) for the full schema
 
## Deployment
 
See [Option A, B, or C in the main README](https://github.com/QuaternionDev/oral-draw#step-4--deploy-the-code) for deployment instructions.
 
## Notes

- The function is stateless; all state lives in the Appwrite database
- Safe to run frequently — sessions that have already been processed are skipped
