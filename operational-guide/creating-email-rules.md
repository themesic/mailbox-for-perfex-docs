# 📋 Creating and Managing Email Rules

Email Rules allow you to automatically organize, tag, and manage emails based on specific conditions. This powerful feature helps you maintain an organized inbox without manual effort.

---

## 🎯 What Are Email Rules?

Email Rules are automated actions that run when emails match certain conditions. For example:
- Automatically tag emails from specific senders
- Move emails containing certain keywords to specific folders
- Archive emails from mailing lists
- Mark important emails based on subject patterns

---

## 🚀 Accessing Email Rules

1. Navigate to **Mailbox → Rules** in the main menu
2. Or click the **Rules** button in the mailbox interface

> ⚠️ **Note:** Email Rules must be enabled in **Setup → Settings → Mailbox Settings** before you can use this feature.

---

## ➕ Creating a New Rule

### Step 1: Open the Rule Editor

1. Click the **Add Rule** button (usually a "+" icon)
2. The rule editor modal will open

### Step 2: Define Rule Name

Enter a descriptive name for your rule, such as:
- "Tag Support Emails"
- "Archive Newsletters"
- "Mark VIP Emails as Important"

### Step 3: Set Conditions

Conditions determine when the rule should apply. You can add multiple conditions:

**Available Condition Types:**
- **From**: Email sender matches specific address or domain
- **Subject**: Subject line contains specific text
- **Body**: Email body contains specific text
- **To**: Email is sent to specific address
- **Has Attachment**: Email has attachments (yes/no)
- **Tag**: Email has specific tag
- **Read Status**: Email is read/unread

**Condition Logic:**
- **All conditions must match** (AND): Rule applies only if all conditions are true
- **Any condition matches** (OR): Rule applies if any condition is true

**Example Conditions:**
- From contains: `support@example.com`
- Subject contains: `[URGENT]`
- Has Attachment: Yes

### Step 4: Define Actions

Actions specify what happens when conditions are met. You can add multiple actions:

**Available Actions:**
- **Add Tag**: Assign a tag to the email
- **Remove Tag**: Remove a tag from the email
- **Move to Folder**: Move email to specific folder (Archive, Trash, etc.)
- **Mark as Important**: Mark email as important
- **Mark as Read/Unread**: Change read status
- **Star/Unstar**: Add or remove star
- **Delete**: Delete the email (use with caution!)

**Example Actions:**
- Add Tag: "Support"
- Mark as Important: Yes
- Move to Folder: "Support"

### Step 5: Set Rule Order

Rules are processed in order. Set a priority number:
- **Lower numbers** = Higher priority (processed first)
- **Higher numbers** = Lower priority (processed later)

**Best Practice:** Start with order 1, 2, 3, etc. You can reorder rules later.

### Step 6: Enable/Disable Rule

- **Enabled**: Rule is active and will process emails
- **Disabled**: Rule is saved but not active

### Step 7: Save the Rule

Click **Save** to create the rule. The rule will immediately start processing new emails that match the conditions.

---

## 📝 Example Rules

### Example 1: Tag Support Emails

**Name:** Tag Support Emails

**Conditions:**
- From contains: `support@`
- OR Subject contains: `support ticket`

**Actions:**
- Add Tag: "Support"

**Order:** 1

**Result:** All emails from support addresses or with "support ticket" in the subject are automatically tagged as "Support".

---

### Example 2: Archive Newsletters

**Name:** Archive Newsletters

**Conditions:**
- From contains: `newsletter@`
- OR Subject contains: `newsletter`
- OR Subject contains: `unsubscribe`

**Actions:**
- Move to Folder: "Archive"
- Mark as Read: Yes

**Order:** 2

**Result:** Newsletter emails are automatically archived and marked as read, keeping your inbox clean.

---

### Example 3: Mark VIP Emails as Important

**Name:** VIP Emails

**Conditions:**
- From contains: `ceo@company.com`
- OR From contains: `manager@company.com`
- OR Subject contains: `[URGENT]`

**Actions:**
- Mark as Important: Yes
- Add Tag: "VIP"

**Order:** 1

**Result:** Emails from VIP senders or with urgent subjects are automatically marked as important and tagged.

---

## ✏️ Editing Rules

1. Navigate to **Mailbox → Rules**
2. Find the rule you want to edit
3. Click the **Edit** button (pencil icon)
4. Modify conditions, actions, or settings
5. Click **Save**

---

## 🗑️ Deleting Rules

1. Navigate to **Mailbox → Rules**
2. Find the rule you want to delete
3. Click the **Delete** button (trash icon)
4. Confirm the deletion

> ⚠️ **Warning:** Deleting a rule is permanent and cannot be undone.

---

## 🔄 Reordering Rules

Rules are processed in order. To change the order:

1. Navigate to **Mailbox → Rules**
2. Use the drag-and-drop handles (if available) or edit the rule's order number
3. Rules with lower order numbers are processed first

**Important:** The order matters! If multiple rules match the same email, they'll all be applied in order.

---

## ✅ Testing Rules

To test if a rule works:

1. Create or edit the rule
2. Save it
3. Send a test email that matches the rule's conditions
4. Check if the actions were applied correctly
5. Review the Activity Log for rule execution messages

---

## 💡 Best Practices

1. **Start Simple**: Begin with basic rules and add complexity as needed
2. **Test First**: Test rules with a few emails before applying broadly
3. **Use Descriptive Names**: Name rules clearly so you remember their purpose
4. **Order Matters**: Place more specific rules before general ones
5. **Review Regularly**: Periodically review and update rules as needs change
6. **Be Careful with Delete**: Avoid using "Delete" action unless absolutely necessary
7. **Combine Conditions**: Use multiple conditions to make rules more precise

---

## ⚠️ Common Issues

### Rule Not Working

**Possible Causes:**
- Rule is disabled
- Conditions don't match (check spelling, case sensitivity)
- Rule order prevents it from running
- Email Rules feature is disabled in Settings

**Solutions:**
- Verify rule is enabled
- Check condition logic (AND vs OR)
- Review rule order
- Check Settings → Mailbox Settings → Enable Email Rules

### Too Many Rules Applied

**Solution:** Review rule order and conditions. More specific rules should have lower order numbers.

### Rules Processing Slowly

**Solution:** Reduce the number of rules or simplify conditions. Complex rules with many conditions take longer to process.

---

## 🔗 Related Documentation

- [Email Tags (Labels)](email-tags-labels.md) - How to create and use tags
- [Organizing Emails](organizing-emails.md) - General email organization tips
- [Settings Reference](../settings-reference.md) - Enable/disable Email Rules feature
