# ⚙️ Settings Reference

This page provides a comprehensive guide to all settings available in the Mailbox module. Access these settings by navigating to **Setup → Settings → Mailbox Settings** (admin only).

---

## 📧 Email Threading

**Setting:** `Enable Email Threading`

**Description:** Groups related emails (replies, forwards) into conversations, similar to Gmail's threading feature.

**Options:**
- **Yes**: Emails are grouped into conversation threads. When you click on an email, you'll see all related messages in a collapsible thread.
- **No**: Emails are displayed in a flat list without grouping.

**When to Use:**
- Enable if you want to see email conversations in a threaded view
- Disable if you prefer a simple chronological list of all emails

**Default:** Enabled

---

## ⏱️ Check Every (Minutes)

**Setting:** `Check Every`

**Description:** How frequently the cron job should check for new emails from your IMAP server.

**Options:** Number of minutes (minimum: 3)

**Recommendations:**
- **3-5 minutes**: For active email accounts that need quick updates
- **10-15 minutes**: For normal business use
- **30+ minutes**: For less critical accounts or to reduce server load

**Important:** This setting requires your Perfex CRM cron job to be properly configured. See the Cron Job section below.

**Default:** 5 minutes

---

## 🎯 Feature Settings

### Archive Feature

**Setting:** `Enable Archive Feature`

**Description:** Allows users to archive emails to keep the inbox clean while preserving important messages. Archived emails are moved to a separate Archive folder but remain accessible.

**Options:**
- **Yes**: Archive feature is available. Users can archive emails using the actions menu.
- **No**: Archive feature is disabled.

**When to Use:**
- Enable if you want to help users keep their inbox organized
- Disable if you prefer a simpler interface

**Default:** Enabled

**How to Use:** See the [Archiving Emails](operational-guide/archiving-emails.md) guide.

---

### Snooze Feature

**Setting:** `Enable Snooze Feature`

**Description:** Allows users to temporarily hide emails and have them reappear at a specified time. Perfect for emails that need attention later.

**Options:**
- **Yes**: Snooze feature is available. Users can snooze emails for later.
- **No**: Snooze feature is disabled.

**When to Use:**
- Enable if you want users to be able to defer emails for later review
- Disable if you prefer a simpler workflow

**Default:** Enabled

**How to Use:** See the [Snoozing Emails](operational-guide/snoozing-emails.md) guide.

---

### Keyboard Shortcuts

**Setting:** `Enable Keyboard Shortcuts`

**Description:** Enables keyboard shortcuts for quick email actions, improving productivity for power users.

**Options:**
- **Yes**: Keyboard shortcuts are enabled
- **No**: Keyboard shortcuts are disabled

**Available Shortcuts:**
- **Ctrl+A**: Select All
- **Delete**: Delete selected emails
- **R**: Reply to email
- **A**: Archive email
- **S**: Star/Unstar email
- **I**: Mark as Important
- **C**: Compose new email

**Default:** Enabled

---

### Auto-mark as Read on Preview

**Setting:** `Auto-mark as Read on Preview`

**Description:** Automatically marks emails as read when viewed in the preview pane or single email view.

**Options:**
- **Yes**: Emails are automatically marked as read when previewed
- **No**: Emails remain unread until manually marked

**Note:** This is a global setting. Individual staff members can override this in their personal Mailbox Config settings.

**Default:** Enabled

---

## 🔄 Sync Settings

### Maximum Emails per Sync

**Setting:** `Maximum Emails per Sync`

**Description:** Limits the number of emails processed per cron run to prevent server overload and timeouts.

**Options:** 
- **0**: Unlimited (process all emails)
- **Any positive number**: Maximum emails to process per sync

**Recommendations:**
- **50-100**: For normal servers
- **200-500**: For powerful servers
- **0**: Only if you have a very powerful server and want to process all emails at once

**When to Adjust:**
- Increase if sync is completing too quickly and you want to process more emails
- Decrease if you're experiencing timeouts or server overload

**Default:** 0 (unlimited)

---

### Sync Timeout (seconds)

**Setting:** `Sync Timeout`

**Description:** Maximum time allowed for email synchronization before the process times out.

**Options:** 30 to 3600 seconds (1 hour)

**Recommendations:**
- **300 seconds (5 minutes)**: Standard for most installations
- **600 seconds (10 minutes)**: For large mailboxes or slow connections
- **1800+ seconds (30+ minutes)**: Only for very large initial syncs

**When to Adjust:**
- Increase if syncs are timing out before completion
- Decrease if you want to prevent long-running processes

**Default:** 300 seconds (5 minutes)

---

## 🎨 UI Settings

### Auto-refresh Interval (seconds)

**Setting:** `Auto-refresh Interval`

**Description:** Automatically refreshes the inbox at the specified interval to show new emails without manual refresh.

**Options:**
- **0**: Disabled (no auto-refresh)
- **30-3600**: Refresh interval in seconds

**Recommendations:**
- **60 seconds (1 minute)**: For active email accounts
- **300 seconds (5 minutes)**: For normal use
- **0**: If you prefer manual refresh or want to reduce server load

**Note:** Auto-refresh only works when the mailbox page is open in your browser.

**Default:** 0 (disabled)

---

### Show Sender Avatars

**Setting:** `Show Sender Avatars`

**Description:** Displays sender avatar images in the email list (if available). Avatars are sourced from:
1. Staff member profile photos (if sender is a staff member)
2. Contact photos (if sender is a contact)
3. Gravatar (based on email address)
4. Generic avatar icon (fallback)

**Options:**
- **Yes**: Avatars are displayed next to sender names
- **No**: No avatars are shown

**Default:** Enabled

---

## 🚀 Advanced Features

### Enable Email Rules

**Setting:** `Enable Email Rules`

**Description:** Allows users to create custom email filtering rules for automatic email organization. Rules can automatically tag, move, archive, or perform other actions on emails based on conditions.

**Options:**
- **Yes**: Rules feature is available. Users can create and manage rules.
- **No**: Rules feature is disabled.

**When to Use:**
- Enable if you want users to automate email organization
- Disable if you prefer manual email management

**Default:** Enabled

**How to Use:** See the [Creating and Managing Email Rules](operational-guide/creating-email-rules.md) guide.

---

### Enable Multiple Tags per Email

**Setting:** `Enable Multiple Tags per Email`

**Description:** Allows assigning multiple tags/labels to a single email for better organization and categorization.

**Options:**
- **Yes**: Users can assign multiple tags to each email
- **No**: Only one tag can be assigned per email

**When to Use:**
- Enable if you want flexible email categorization (e.g., tag an email as both "Important" and "Support")
- Disable if you prefer a simpler single-tag system

**Default:** Enabled

**Note:** Requires the `mail_email_tags` database table to be present.

---

### Enable Advanced Search

**Setting:** `Enable Advanced Search`

**Description:** Shows advanced search options with filters for From, Subject, Body, Tags, Date, Read Status, and more.

**Options:**
- **Yes**: Advanced search interface is available
- **No**: Only basic search is available

**When to Use:**
- Enable if you want powerful search capabilities
- Disable if you prefer a simpler search interface

**Default:** Enabled

**How to Use:** See the [Advanced Search](operational-guide/advanced-search.md) guide.

---

### Enable Enhanced Bulk Actions

**Setting:** `Enable Enhanced Bulk Actions`

**Description:** Enables advanced bulk actions like select all, mass archive, mass delete, mass tag, etc.

**Options:**
- **Yes**: Enhanced bulk actions are available
- **No**: Only basic bulk actions are available

**When to Use:**
- Enable if you want to manage multiple emails at once efficiently
- Disable if you prefer individual email management

**Default:** Enabled

---

## ⏰ Cron Job Configuration

### Important: Cron Job Required

The Mailbox module **requires** a properly configured cron job to fetch emails from your IMAP server. Without a cron job, emails will not be synced automatically.

**Cron Command:**
```
*/5 * * * * php /path/to/perfex/index.php cron/index
```

**Configuration Steps:**
1. Access your server's cron configuration (via cPanel, SSH, or hosting control panel)
2. Add the cron command above, adjusting:
   - The frequency (`*/5` = every 5 minutes)
   - The path to your Perfex installation
3. Save the cron job

**Verification:**
- Check **Utilities → Activity Log** for email sync activity
- Use the **Manual Sync** button in Settings to test immediately
- Navigate to **Setup → Settings → Cron Job** for Perfex's cron settings

**Troubleshooting:**
- If emails aren't syncing, verify the cron job is running
- Check Activity Log for error messages
- Ensure the cron user has proper permissions
- Verify the path to `index.php` is correct

---

## 📝 Notes

- **Admin Only**: All settings on this page are admin-only. Regular staff members cannot modify these settings.
- **Per-Staff Overrides**: Some settings (like "Import Only Unread Emails" and "HTML Rendering") can be overridden by individual staff members in their Mailbox Config.
- **Default Values**: Most features are enabled by default for the best user experience.
- **Performance**: Adjust sync settings based on your server capacity and email volume.
- **Compatibility**: Settings are backward compatible. Disabling a feature won't affect existing data.

---

## 🔗 Related Documentation

- [Configuration Steps](configuration-steps.md) - How to set up your email connection
- [Troubleshooting](troubleshooting.md) - Common issues and solutions
- [Operational Guide](operational-guide/README.md) - How to use mailbox features
