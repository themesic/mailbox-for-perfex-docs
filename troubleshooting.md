---
description: >-
  If you’re facing issues with connecting to your email account or syncing
  emails, follow this checklist to investigate and resolve:
---

# 🧑‍💻 Troubleshooting

### 🔍 1. Check the Activity Log

Go to **Utilities → Activity Log** inside Perfex CRM to view any error messages related to IMAP connection or syncing failures.

***

### 🧾 2. Enable Debug Mode

To get more detailed error output:

* Open `index.php` in the root of your Perfex CRM installation.
*   Locate the line:

    ```php
    define('ENVIRONMENT', 'production');
    ```
*   Change it to:

    ```php
    define('ENVIRONMENT', 'development');
    ```
* Save the file and reload the page to see raw error messages.\
  &#xNAN;_(Don’t forget to change it back to `production` after testing!)_

***

### 🧠 3. Inspect Your Hosting Error Logs

If the screen goes blank or no errors appear in Perfex:

* Access your **web hosting control panel** (e.g., cPanel or Plesk).
* Look for **“Error Log”**, usually under the “Metrics” or “Logs” section.
* Scan for recent errors like “memory exhausted”, “timeout”, or IMAP-related issues.

***

### 🔁 4. Double-Check Cron Setup

Ensure your cron jobs are running. Without them, the Mailbox module cannot sync emails.

Refer to Perfex CRM’s documentation or your server admin for cron troubleshooting.

***

### 🔐 5. OAuth vs Password Authentication

The Mailbox module supports two authentication methods:

#### OAuth2 Authentication (Recommended)

**For Gmail and Outlook users**, OAuth2 is the recommended method. It's more secure and doesn't require storing passwords.

**Common OAuth Issues:**

* **"OAuth connection failed"**: 
  - Verify that OAuth credentials are correctly set in **Setup → Settings → Mailbox Settings**
  - Check that redirect URI is correctly configured in your OAuth app
  - Ensure your OAuth app has the required scopes (IMAP access, Send email)

* **"Token expired"**: 
  - OAuth tokens are automatically refreshed. If you see this error, try disconnecting and reconnecting your OAuth account
  - For Gmail: Tokens expire after 7 days of inactivity. Reconnect if needed.
  - For Outlook: Tokens are long-lived but may need reconnection if revoked.

* **"OAuth not available"**: 
  - OAuth is only available for Gmail and Outlook
  - For other providers, use password authentication

#### Password Authentication

For email providers that don't support OAuth2, use password authentication.

**Check if your Email provider needs an App Password**

Some email providers, such as **Gmail**, **Yahoo**, and **Outlook**, require you to use an **App Password** instead of your actual email account password — especially if **2FA (Two-Factor Authentication)** is enabled.

If you encounter repeated authentication errors during IMAP setup, check whether your provider requires an app-specific password.

**Example: Gmail Users**

1. Go to [https://myaccount.google.com/security](https://myaccount.google.com/security)
2. Enable **2-Step Verification**, if not already enabled.
3. Under "Signing in to Google", locate **App Passwords**.
4. Generate a new app password for "Mail".
5. Use that password in **Mailbox Config** of the module instead of your normal Gmail password.

> ⚠️ Failure to use an App Password when required will result in authentication errors or blocked login attempts.

**Note:** For Gmail and Outlook, we strongly recommend using OAuth2 instead of App Passwords for better security and ease of use.

Always consult your provider's documentation if unsure.

### 🔄 6. Per-Staff vs Global Settings

The module supports both per-staff and global IMAP settings:

* **Per-Staff Settings**: Each staff member can configure their own IMAP server, port, encryption, and folder mappings
* **Global Settings**: Fallback settings used when per-staff settings are not configured

**If emails aren't syncing:**

1. Check your **Mailbox Config** page for per-staff settings
2. Verify that IMAP server, port, and encryption are correct
3. Check folder mappings (especially if using non-standard folder names)
4. Review Activity Log for specific error messages

### 📊 7. Read Status Sync Issues

If you've enabled "Sync Read Status to Email Server" but changes aren't reflecting in Gmail/Outlook:

* **Old emails**: Emails imported before version 2.1.7 may not have UID stored. Only new emails will sync read status.
* **UID missing**: Check Activity Log for "Email ID XXX has no UID stored" messages (this is normal for old emails)
* **OAuth required**: Read status sync works best with OAuth authentication
* **Manual sync**: Use the Manual Sync button in Settings to test the connection

***

### 🆘 Still Need Help?

If you’re stuck or unable to resolve an issue, our support team is here to help.\
Please open a ticket through the **Support Ticketing Area**, and we’ll assist you as soon as possible.
