# ⏰ Snoozing Emails

Snoozing allows you to temporarily hide emails from your inbox and have them reappear at a specified time. Perfect for emails that need attention later but aren't urgent now.

---

## 🎯 What is Snoozing?

Snoozing is like setting a reminder:
- Email disappears from inbox temporarily
- Email reappears at the time you specify
- Perfect for "deal with this later" emails
- Helps keep inbox focused on current priorities

---

## ✅ Prerequisites

The Snooze feature must be enabled in **Setup → Settings → Mailbox Settings → Enable Snooze Feature**.

---

## ⏰ How to Snooze an Email

### Step 1: Open Snooze Menu

1. Find the email you want to snooze
2. Click the **three-dots menu** (⋯) on the email row
3. Select **Snooze**

### Step 2: Choose Snooze Duration

The snooze modal will open with options:

**Quick Options:**
- **Later Today** (e.g., 3 hours from now)
- **Tomorrow** (9:00 AM)
- **This Weekend** (Saturday 9:00 AM)
- **Next Week** (Monday 9:00 AM)

**Custom Date/Time:**
- Click **Pick a date & time**
- Select the date from calendar
- Choose the time
- Click **Snooze**

### Step 3: Confirm

The email will disappear from your inbox and reappear at the specified time.

---

## 📥 Viewing Snoozed Emails

### Snoozed Folder

1. Navigate to **Mailbox → Emails**
2. In the folder sidebar, click **Snoozed**
3. View all currently snoozed emails with their return times

---

## 🔄 Managing Snoozed Emails

### Remove Snooze (Return to Inbox Now)

1. Navigate to **Snoozed** folder
2. Find the email
3. Click the **three-dots menu** (⋯)
4. Select **Remove Snooze** or **Return to Inbox**
5. Email will immediately return to inbox

### Change Snooze Time

1. Navigate to **Snoozed** folder
2. Find the email
3. Click **Snooze** again
4. Choose a new time
5. Email will be rescheduled

---

## ⏰ When Emails Return

Snoozed emails automatically return to your inbox:
- At the specified date and time
- When the cron job runs (checks every few minutes)
- Email appears in inbox as unread (unless it was already read)

**Note:** Emails return based on your server's timezone and cron job frequency.

---

## 💡 Use Cases

### 1. Follow Up Later

Snooze an email to follow up in a few hours or days:
- "I'll respond to this tomorrow morning"
- "Review this after the meeting"

### 2. Time-Sensitive Tasks

Snooze emails that need attention at specific times:
- "Review this proposal on Friday"
- "Check this before the deadline"

### 3. Inbox Management

Temporarily hide emails to focus on current priorities:
- Clear inbox of non-urgent items
- Focus on what needs attention now

### 4. Reminder System

Use snooze as a reminder system:
- Snooze important emails to specific dates
- Let them reappear when you need to act

---

## 💡 Best Practices

1. **Be Realistic**: Don't snooze too many emails - you'll forget about them
2. **Use Specific Times**: Choose times when you'll actually be available
3. **Review Snoozed Folder**: Periodically check snoozed emails
4. **Combine with Tags**: Tag emails before snoozing for context
5. **Remove When Done**: Remove snooze once you've handled the email

---

## ⚠️ Important Notes

- Snoozed emails are hidden from inbox but not deleted
- Emails return based on cron job frequency (may not be exact minute)
- Snooze feature must be enabled in Settings
- You can snooze multiple emails at once using bulk actions
- Snoozed emails can be searched and accessed from Snoozed folder

---

## 🔗 Related Documentation

- [Organizing Emails](organizing-emails.md) - General organization tips
- [Email Tags (Labels)](email-tags-labels.md) - Tag emails before snoozing
- [Settings Reference](../settings-reference.md) - Enable Snooze feature
