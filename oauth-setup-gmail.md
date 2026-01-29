# 🔐 Setting Up Gmail OAuth Authentication

This guide will walk you through creating a Google Cloud application for OAuth authentication with Gmail. OAuth provides a more secure way to access your Gmail account compared to traditional password authentication.

## 📋 Prerequisites

- A Google account (personal or Google Workspace)
- Access to [Google Cloud Console](https://console.cloud.google.com/)
- Your Perfex CRM installation URL (for redirect URI configuration)

## 🚀 Step-by-Step Setup

### Step 1: Create a Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Click on the project dropdown at the top of the page
3. Click **"New Project"**
4. Enter a project name (e.g., "Perfex Mailbox OAuth")
5. Click **"Create"**
6. Wait for the project to be created and select it

### Step 2: Enable Gmail API

1. In the Google Cloud Console, navigate to **"APIs & Services"** > **"Library"**
2. Search for **"Gmail API"**
3. Click on **"Gmail API"** from the results
4. Click **"Enable"**
5. Wait for the API to be enabled

### Step 3: Configure OAuth Consent Screen

1. Navigate to **"APIs & Services"** > **"OAuth consent screen"**
2. Select **"External"** user type (unless you have a Google Workspace account, then you can choose "Internal")
3. Click **"Create"**
4. Fill in the required information:
   - **App name**: Enter your application name (e.g., "Perfex CRM Mailbox")
   - **User support email**: Your email address
   - **Developer contact information**: Your email address
5. Click **"Save and Continue"**
6. On the **"Scopes"** page, click **"Add or Remove Scopes"**
7. Add the following scopes:
   - `https://www.googleapis.com/auth/gmail.readonly`
   - `https://www.googleapis.com/auth/gmail.send`
   - `https://www.googleapis.com/auth/gmail.modify`
8. Click **"Update"**, then **"Save and Continue"**
9. On the **"Test users"** page (if using External app type):
   - Add your Gmail address as a test user
   - Click **"Save and Continue"**
10. Review and click **"Back to Dashboard"**

### Step 4: Create OAuth 2.0 Credentials

1. Navigate to **"APIs & Services"** > **"Credentials"**
2. Click **"Create Credentials"** > **"OAuth client ID"**
3. Select **"Web application"** as the application type
4. Enter a name for your OAuth client (e.g., "Perfex Mailbox Client")
5. Under **"Authorized redirect URIs"**, click **"Add URI"**
6. Add your redirect URI in the format:
   ```
   https://your-domain.com/admin/mailbox/oauth/callback?provider=gmail
   ```
   Replace `your-domain.com` with your actual Perfex CRM domain
7. Click **"Create"**
8. **IMPORTANT**: Copy and save both:
   - **Client ID** (you'll need this)
   - **Client Secret** (you'll need this - click "Show" to reveal it)

### Step 5: Configure in Perfex CRM

1. Go to your Perfex CRM admin area
2. Navigate to **Mailbox** > **Configuration**
3. Select **"OAuth2"** as your authentication method
4. Select **"Gmail"** as your provider
5. Enter your **Client ID** in the "Gmail Client ID" field
6. Enter your **Client Secret** in the "Gmail Client Secret" field
7. Click **"Save Configuration"**
8. Click the **"Connect Gmail"** button
9. Authorize the application in the Google popup window
10. You should see a success message confirming the connection

## ⚠️ Important Limitations & Considerations

### Google Test App Limitations

**These limitations are imposed by Google, not by our software:**

1. **Token Expiry (7 Days)**
   - **Unverified apps** (apps in testing mode) have OAuth tokens that expire after **7 days**
   - After 7 days, users must re-authorize the connection
   - This is a **Google security policy** for unverified applications

2. **Test User Restrictions**
   - Only users added to the "Test users" list can use the OAuth app
   - Maximum of **100 test users** allowed
   - This restriction applies until the app is verified and published

3. **App Verification Process**
   - To remove the 7-day token expiry, you must submit your app for **Google verification**
   - Verification can take **several weeks** (typically 4-8 weeks)
   - Google reviews your app for security and compliance
   - **This is a Google requirement**, not a limitation of our module

### App Verification & Publishing

**To remove limitations:**

1. **Submit for Verification**
   - Go to **"OAuth consent screen"** in Google Cloud Console
   - Click **"PUBLISH APP"** button
   - Fill out the verification form with:
     - App purpose and functionality
     - Privacy policy URL
     - Terms of service URL
     - Video demonstration (optional but recommended)
   - Submit for review

2. **Verification Timeline**
   - **Initial review**: 1-2 weeks
   - **Additional information requests**: Variable (if Google needs clarification)
   - **Final approval**: 4-8 weeks total (typical)
   - **This timeline is set by Google**, not our software

3. **After Verification**
   - Tokens no longer expire after 7 days
   - No test user restrictions
   - App can be used by any Gmail user
   - **This is a Google policy**, not controlled by our module

### Production vs Testing

- **Testing Mode**: Quick setup, but tokens expire every 7 days
- **Production Mode**: Requires verification, but tokens don't expire
- **The choice is yours** - our software works with both modes

## 🔄 Token Refresh

Our module automatically handles token refresh when possible. However:

- **Unverified apps**: Tokens expire after 7 days and require manual re-authorization
- **Verified apps**: Tokens refresh automatically without user intervention
- **This behavior is controlled by Google's policies**, not our software

## 📝 Notes

- The redirect URI must match exactly what you configured in Google Cloud Console
- Keep your Client Secret secure - never share it publicly
- If you change your domain, update the redirect URI in Google Cloud Console
- The OAuth flow is handled entirely by Google - our module only initiates and receives the callback

## 🆘 Troubleshooting

**"Redirect URI mismatch" error:**
- Ensure the redirect URI in Google Cloud Console matches exactly: `https://your-domain.com/admin/mailbox/oauth/callback?provider=gmail`
- Check for trailing slashes or HTTP vs HTTPS mismatches

**"Token expired" after 7 days:**
- This is expected for unverified apps (Google's policy)
- Re-authorize by clicking "Connect Gmail" again
- To avoid this, submit your app for Google verification

**"Access blocked" error:**
- Ensure your email is added to the "Test users" list (for unverified apps)
- Check that Gmail API is enabled in your Google Cloud project

**Can't find Gmail API:**
- Make sure you're in the correct Google Cloud project
- Try searching for "Gmail" in the API Library

## 🔗 Additional Resources

- [Google OAuth 2.0 Documentation](https://developers.google.com/identity/protocols/oauth2)
- [Gmail API Documentation](https://developers.google.com/gmail/api)
- [Google Cloud Console](https://console.cloud.google.com/)

---

**Remember**: The 7-day token expiry and test user restrictions are **Google's security policies** for unverified applications. These limitations are not imposed by our software. Once your app is verified by Google, these restrictions are removed.
