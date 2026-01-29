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

### 🔐 5. Check if your Email provider needs an App Password

Some email providers, such as **Gmail**, **Yahoo**, and **Outlook**, require you to use an **App Password** instead of your actual email account password — especially if **2FA (Two-Factor Authentication)** is enabled.

If you encounter repeated authentication errors during IMAP setup, check whether your provider requires an app-specific password.

**Example: Gmail Users**

1. Go to [https://myaccount.google.com/security](https://myaccount.google.com/security)
2. Enable **2-Step Verification**, if not already enabled.
3. Under "Signing in to Google", locate **App Passwords**.
4. Generate a new app password for "Mail".
5. Use that password in **Mailbox Settings** of the module instead of your normal Gmail password.

> ⚠️ Failure to use an App Password when required will result in authentication errors or blocked login attempts.

Always consult your provider's documentation if unsure.

***

### 🆘 Still Need Help?

If you’re stuck or unable to resolve an issue, our support team is here to help.\
Please open a ticket through the **Support Ticketing Area**, and we’ll assist you as soon as possible.
