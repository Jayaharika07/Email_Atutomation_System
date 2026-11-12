# Automated Email Reminder Bot

An Automation Anywhere (Community Edition) bot that reads a Google Sheet and sends reminder emails for pending items.

## What it does
1. Connects to Google Sheets using OAuth2 (Authorization Code), with credentials stored in the Credential Vault
2. Opens the spreadsheet and reads multiple cells into a table
3. Loops through each row and calculates the difference in days between the sheet date and today's date
4. If the difference is more than 2 days and the status is `pending`:
   - Sends an email with the subject "Remainder Email"
   - Writes `Email Sent` back to the sheet

## Sheet layout
| Column | Content |
|--------|---------|
| 1 | Date |
| 3 | Recipient email |
| 5 | Status (`pending`) |

## Setup
1. Create an OAuth client in Google Cloud Console and enable the Google Sheets API
2. Store the Client ID, Client Secret, and username in the Credential Vault
3. Add the redirect URI used by Automation Anywhere to **Authorized redirect URIs**
4. Import the bot and run it

## Known issue
The Connect step currently fails with `Error 400: redirect_uri_mismatch`. The redirect URI sent by the bot must exactly match one listed in the Google Cloud OAuth client.

## Screenshots
Add the screenshots (with sensitive details blurred) from the `/screenshots` folder.
