# 🚧 Configuration Steps

Follow these steps to set up your personal inbox connection to the Mailbox module in Perfex CRM. \
**Each staff member can only configure their own inbox connection, which will be tied to the email address used for signing into the admin area.** For security and isolation purposes, ensure each staff member sets up their own email account.<br>

## 🔐 Authentication Methods

The Mailbox module supports two authentication methods:

1. **OAuth2 Authentication** (Recommended for Gmail and Outlook) - Password-free, secure connection
2. **Password Authentication** - Traditional IMAP password-based connection

### Option A: OAuth2 Authentication (Gmail/Outlook)

OAuth2 is the recommended method for Gmail and Outlook/Microsoft 365 accounts. It provides secure, password-free authentication and is required by many modern email providers.

#### For Gmail Users:

1. **Admin Setup** (One-time, done by administrator):
   - Go to **Setup → Settings → Mailbox Settings**
   - Scroll to **OAuth Settings** section
   - Enter your **Gmail OAuth Client ID** and **Client Secret**
   - Click **Save**

2. **Staff Setup** (Each staff member):
   - Navigate to **Mailbox → Emails** (or **Profile → Mailbox Config**)
   - Select **OAuth** as authentication method
   - Click **Connect Gmail** button
   - Authorize the application in the popup window
   - Your Gmail account will be connected automatically

#### For Outlook/Microsoft 365 Users:

1. **Admin Setup** (One-time, done by administrator):
   - Go to **Setup → Settings → Mailbox Settings**
   - Scroll to **OAuth Settings** section
   - Enter your **Outlook OAuth Client ID**, **Client Secret**, and **Tenant ID**
   - Click **Save**

2. **Staff Setup** (Each staff member):
   - Navigate to **Mailbox → Emails** (or **Profile → Mailbox Config**)
   - Select **OAuth** as authentication method
   - Click **Connect Outlook** button
   - Authorize the application in the popup window
   - Your Outlook account will be connected automatically

> 💡 **Note:** OAuth tokens are automatically refreshed before expiration. You only need to authorize once.

### Option B: Password Authentication

For email providers that don't support OAuth2, or if you prefer password-based authentication:

### 1️⃣ Enter Your Email Account's Information

Navigate to the **Mailbox Configuration Settings** section by selecting "Emails" under "Mailbox" menu on the left:&#x20;

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Enter the **IMAP account username** and **password** associated with your email address (e.g., if you are logged in as **john@gmail.com**, set up **john@gmail.com** as your inbox) and optionally add your signature there.

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

For security purposes, **john@gmail.com** cannot set up a connection for **george@gmail.com** in their own CRM account. To set up **george@gmail.com**, create a **George** staff account in Perfex CRM, and then configure George's email inbox from within his user profile. This ensures that each staff member's email communications are properly isolated and securely linked to their own user account.

After entering your email account credentials and (optionally) your signature, press **Save** to finalize the connection.

### 2️⃣ Set Up Your IMAP Server Details

You can configure IMAP settings in two ways:

#### Method 1: Per-Staff IMAP Configuration (Recommended)

Each staff member can configure their own IMAP server settings:

1. Navigate to **Mailbox → Emails** (or **Profile → Mailbox Config**)
2. Scroll to **IMAP Server Configuration** section
3. Enter your **IMAP Server** (e.g., `imap.gmail.com`)
4. Select **Encryption Method** (SSL, TLS, or None)
5. **IMAP Port** will auto-update based on encryption (993 for SSL, 143 for TLS)
6. Configure **Folder Mappings**:
   - **Folder to Scan** (usually "INBOX")
   - **Sent Folder** (e.g., "Sent", "Sent Items")
   - **Drafts Folder** (e.g., "Drafts")
   - **Trash Folder** (e.g., "Trash", "Deleted Items")
   - **Spam Folder** (e.g., "Spam", "Junk")
   - **Archive Folder** (e.g., "Archive")
7. Click **Save**

> 💡 **Tip:** If you leave folder mappings empty, the module will attempt to auto-detect them.

#### Method 2: Global IMAP Settings (Fallback)

If per-staff settings are not configured, the module will use global settings:

1. Click on Perfex's **Setup** Menu and locate **Settings** section
2. Then head to the bottom and find **Mailbox Settings**
3. Click it and fill in the needed details, based on your email provider's settings.

**Mandatory Details needed**:

* **IMAP Server** (e.g., `imap.gmail.com`)
* **Encryption Method** (Usually SSL)
* **Folder** (folder used for monitoring - usually "Inbox")
* **Check Every** (the frequency of emails fetching task, in minutes)

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

You can optionally change a few straightforward options used for module's operation, at the same screen. Be sure to use the correct settings for your provider - incorrect details will prevent a successful connection.<br>

### 3️⃣ Configure Personal Preferences

In your **Mailbox Config** page, you can also configure:

* **Import Only Unread Emails**: Enable to fetch only unread emails (faster sync)
* **Enable HTML Rendering**: Enable to display HTML emails with formatting
* **Auto-mark as Read on Preview**: Automatically mark emails as read when viewing in preview pane or single view
* **Sync Read Status to Email Server**: Sync read status back to your IMAP server (keeps Gmail/Outlook in sync, but slower)

> 💡 **Note:** "Sync Read Status to Email Server" is useful if you want your Gmail/Outlook inbox to stay synchronized with Perfex. When enabled, reading an email in Perfex will mark it as read on your email server.

### 4️⃣ You're All Set!

After saving your settings, the Mailbox module will attempt to connect to your inbox, as long as **Perfex CRM's cron jobs are running properly**.

> ✅ **Tip:** You can verify that cron is working by checking scheduled task execution or module sync activity. You can also use the **Manual Sync** button in Settings → Mailbox Settings to test the connection immediately.

### ⚠️ Important Notes

* On first connection, if your inbox contains a large number of **unread emails**, all of them will be imported into the module and stored in your Perfex database.
* This is completely normal - but the initial sync might take a few minutes.
* If your server has limited resources, this could lead to temporary timeouts during the sync process. Simply wait and refresh after a while.
* **OAuth users**: Your OAuth tokens are automatically refreshed before expiration. If you see connection errors, try disconnecting and reconnecting your OAuth account.
* **Password users**: For Gmail and Outlook, you may need to use an **App Password** instead of your regular password if 2FA is enabled. See the Troubleshooting section for details.
