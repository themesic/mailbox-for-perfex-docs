# 🌐 Translation

Our module is fully translation-ready, allowing you to easily adapt its interface and labels into your preferred language.

Whether you're translating for a multilingual team or just personal convenience, follow the steps below to apply your own translations.

***

### 📁 Location of Language Files

All language strings used by the module are stored in the following path:

`modules/your_module_name/language/english/`

Inside this folder, you'll find one or more `.php` files (usually `mailbox_lang.php`) that contain all the text labels used in the module.

***

### 🈯️ Option 1: Create a New Language Folder

To add a new translation:

1. Navigate to the module's `language` directory.
2. Create a new folder using the **ISO language code** of your preferred language (e.g., `french`, `german`, `greek`, etc.).
3. Copy the existing `english` file(s) into your new folder.
4. Open the copied file and translate the right-hand side of each string:

```php
$lang['mailbox_inbox'] = 'Boîte de réception'; // French example
```

5. Save your file and make sure your language is set in **Perfex CRM > Setup > Settings > Localization**.

Perfex will automatically load the matching language file if it exists.

***

### 🈯️ Option 2: Override from Perfex's Global Language File

Alternatively, if you prefer not to touch the module files, you can override specific strings globally from:

```
application/language/your_language/custom_lang.php
```

This approach is useful for central management or minor edits.

Just define any language keys used in the module with your own custom text. For example:

```php
$lang['mailbox_compose'] = 'Nouveau message';
```

> 💡 This method ensures your custom changes are preserved during module updates.

***

### 📌 Tips & Best Practices

* Always **backup** your language files before making edits.
* Use a **UTF-8 compatible editor** (such as VSCode, Sublime Text, or Notepad++) to prevent encoding issues.
* Avoid editing the `english` file directly if you plan to support multiple languages.

***

### 🧩 Need Help?

If you're unsure about a translation key or your language isn't showing up, feel free to contact our support team. We're happy to help you localize the module properly!
