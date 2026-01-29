# 🚧 Configuration Steps

Follow these steps to set up your personal inbox connection to the Mailbox module in Perfex CRM. \
**Each staff member can only configure their own inbox connection, which will be tied to the email address used for signing into the admin area.** For security and isolation purposes, ensure each staff member sets up their own email account.<br>

### 1️⃣ Enter Your Email Account's Information

Navigate to the **Mailbox Configuration Settings** section by selecting "Emails" under "Mailbox" menu on the left:&#x20;

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Enter the **IMAP account username** and **password** associated with your email address (e.g., if you are logged in as **john@gmail.com**, set up **john@gmail.com** as your inbox) and optionally add your signature there.

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

For security purposes, **john@gmail.com** cannot set up a connection for **george@gmail.com** in their own CRM account. To set up **george@gmail.com**, create a **George** staff account in Perfex CRM, and then configure George’s email inbox from within his user profile. This ensures that each staff member’s email communications are properly isolated and securely linked to their own user account.

After entering your email account credentials and (optionally) your signature, press **Save** to finalize the connection.



### 2️⃣ Set Up Your IMAP Server Details

Click on Perfex's **Setup** Menu and locate **Settings** section:

![](<.gitbook/assets/image (6).png>)      <img src=".gitbook/assets/image (8).png" alt="" data-size="original">

\
\
Then head to the bottom and find **Mailbox Settings**:\
\
![](<.gitbook/assets/image (9).png>)

\
\
Click it and fill in the needed details, based on your email provider's settings.

**Mandatory Details needed**:

* **IMAP Server** (e.g., `imap.gmail.com`)
* **Encryption Method** (Usually SSL)
* **Folder** (folder used for monitoring - usually “Inbox”)
* **Check Every** (the frequency of emails fetching task, in minutes)

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

You can optionally change a few straightforward options used for module's operation, at the same screen. Be sure to use the correct settings for your provider - incorrect details will prevent a successful connection.<br>

### 3️⃣ You’re All Set!

After saving your settings, the Mailbox module will attempt to connect to your inbox, as long as **Perfex CRM's cron jobs are running properly**.

> ✅ **Tip:** You can verify that cron is working by checking scheduled task execution or module sync activity.



### ⚠️ Important Notes

* On first connection, if your inbox contains a large number of **unread emails**, all of them will be imported into the module and stored in your Perfex database.
* This is completely normal - but the initial sync might take a few minutes.
* If your server has limited resources, this could lead to temporary timeouts during the sync process. Simply wait and refresh after a while.

