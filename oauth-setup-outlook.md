# 🔐 Setting Up Outlook/Microsoft 365 OAuth Authentication

This guide will walk you through creating a Microsoft Azure application for OAuth authentication with Outlook/Microsoft 365. OAuth provides a more secure way to access your Outlook account compared to traditional password authentication.

## 📋 Prerequisites

- A Microsoft account (personal or Microsoft 365/Office 365)
- Access to [Azure Portal](https://portal.azure.com/)
- Your Perfex CRM installation URL (for redirect URI configuration)
- **Note**: For Microsoft 365 organizations, you may need admin approval

## 🚀 Step-by-Step Setup

### Step 1: Register an Application in Azure Portal

1. Go to [Azure Portal](https://portal.azure.com/)
2. Sign in with your Microsoft account
3. Navigate to **"Azure Active Directory"** (or search for it)
4. Click on **"App registrations"** in the left menu
5. Click **"+ New registration"**
6. Fill in the application details:
   - **Name**: Enter a name (e.g., "Perfex CRM Mailbox")
   - **Supported account types**: 
     - Choose **"Accounts in any organizational directory and personal Microsoft accounts"** for maximum compatibility
     - Or choose based on your needs (see limitations below)
   - **Redirect URI**: 
     - Platform: **Web**
     - URI: `https://your-domain.com/admin/mailbox/oauth/callback?provider=outlook`
     - Replace `your-domain.com` with your actual Perfex CRM domain
7. Click **"Register"**

### Step 2: Configure API Permissions

1. In your app registration, click **"API permissions"** in the left menu
2. Click **"+ Add a permission"**
3. Select **"Microsoft Graph"**
4. Select **"Delegated permissions"**
5. Add the following permissions:
   - `Mail.Read` - Read mail in all mailboxes
   - `Mail.ReadWrite` - Read and write mail in all mailboxes
   - `Mail.Send` - Send mail as the user
   - `offline_access` - Maintain access to data you have given it access to (for token refresh)
6. Click **"Add permissions"**
7. **IMPORTANT**: Click **"Grant admin consent for [Your Organization]"** if you see this button
   - This is required for organization accounts
   - **Note**: This requires admin privileges - see limitations below

### Step 3: Create Client Secret

1. In your app registration, click **"Certificates & secrets"** in the left menu
2. Click **"+ New client secret"**
3. Enter a description (e.g., "Perfex Mailbox Secret")
4. Choose an expiration period:
   - **24 months** (recommended for production)
   - Or shorter if preferred
5. Click **"Add"**
6. **IMPORTANT**: Copy the **Value** immediately (you won't be able to see it again)
   - This is your **Client Secret**
   - Save it securely

### Step 4: Get Application (Client) ID

1. In your app registration, go to **"Overview"**
2. Copy the **Application (client) ID**
   - This is your **Client ID**
   - Save it securely

### Step 5: Configure Redirect URI (Verify)

1. In your app registration, click **"Authentication"** in the left menu
2. Under **"Redirect URIs"**, verify your redirect URI is listed:
   ```
   https://your-domain.com/admin/mailbox/oauth/callback?provider=outlook
   ```
3. If not present, click **"+ Add a platform"** > **"Web"** and add it
4. Under **"Implicit grant and hybrid flows"**, ensure **"Access tokens"** is checked (if available)
5. Click **"Save"**

### Step 6: Configure in Perfex CRM

1. Go to your Perfex CRM admin area
2. Navigate to **Mailbox** > **Configuration**
3. Select **"OAuth2"** as your authentication method
4. Select **"Outlook"** as your provider
5. Enter your **Client ID** (Application ID from Azure)
6. Enter your **Client Secret** (the secret value you copied)
7. **For Microsoft 365 organizations**: Enter your **Tenant ID** (found in Azure AD > Overview)
   - Leave blank for personal Microsoft accounts
8. Click **"Save Configuration"**
9. Click the **"Connect Outlook"** button
10. Authorize the application in the Microsoft popup window
11. You should see a success message confirming the connection

## ⚠️ Important Limitations & Considerations

### Microsoft Azure App Restrictions

**These limitations are imposed by Microsoft, not by our software:**

1. **Admin Consent Requirements**
   - **Organization accounts** (Microsoft 365/Office 365) require **admin consent** for certain permissions
   - Admin must approve the app before users can use it
   - **This is a Microsoft security policy**, not a limitation of our module
   - Personal Microsoft accounts don't require admin consent

2. **Account Type Restrictions**
   - **"Accounts in this organizational directory only"**: Only users in your organization can use the app
   - **"Accounts in any organizational directory"**: Users from any Microsoft 365 organization can use it
   - **"Accounts in any organizational directory and personal Microsoft accounts"**: Maximum compatibility
   - **"Personal Microsoft accounts only"**: Only personal @outlook.com, @hotmail.com accounts
   - **This is controlled by Microsoft**, not our software

3. **Tenant ID Requirements**
   - **Organization accounts**: Tenant ID is required for proper authentication
   - **Personal accounts**: Tenant ID can be left blank
   - **This is a Microsoft requirement**, not our software limitation

### App Verification & Publishing

**Microsoft App Verification:**

1. **Unverified Apps**
   - Can be used immediately for personal accounts
   - May show warning messages to users (Microsoft's security feature)
   - **This is Microsoft's policy**, not our software

2. **Verified Apps**
   - Requires submission to Microsoft App Store (optional)
   - Provides better user experience (no warnings)
   - **Verification is optional** - not required for functionality
   - **This is a Microsoft process**, not controlled by our module

3. **Admin Consent Workflow**
   - For organization accounts, admin must grant consent
   - Admin sees what permissions the app requests
   - **This is Microsoft's security model**, not our software

### Token Refresh

Our module automatically handles token refresh:

- **Refresh tokens**: Automatically obtained with `offline_access` permission
- **Token expiry**: Typically 1 hour for access tokens, 90 days for refresh tokens
- **Automatic refresh**: Our module refreshes tokens automatically before expiry
- **This behavior follows Microsoft's OAuth standards**, not our custom implementation

### Multi-Tenant vs Single-Tenant

- **Multi-Tenant**: App can be used by any Microsoft account (requires admin consent per organization)
- **Single-Tenant**: App can only be used within your organization
- **The choice affects who can use your app** - this is a Microsoft configuration, not our software

## 🔄 Token Management

- **Access tokens**: Short-lived (typically 1 hour)
- **Refresh tokens**: Long-lived (typically 90 days)
- **Automatic refresh**: Our module handles this automatically
- **Token storage**: Securely encrypted in your database
- **This follows Microsoft's OAuth 2.0 implementation**, not our custom system

## 📝 Notes

- The redirect URI must match exactly what you configured in Azure Portal
- Keep your Client Secret secure - never share it publicly
- If you change your domain, update the redirect URI in Azure Portal
- For organization accounts, ensure admin consent is granted
- Tenant ID is only needed for Microsoft 365/Office 365 accounts
- The OAuth flow is handled entirely by Microsoft - our module only initiates and receives the callback

## 🆘 Troubleshooting

**"AADSTS50011: Redirect URI mismatch" error:**
- Ensure the redirect URI in Azure Portal matches exactly: `https://your-domain.com/admin/mailbox/oauth/callback?provider=outlook`
- Check for trailing slashes or HTTP vs HTTPS mismatches
- Verify the URI is listed under "Web" platform type

**"Admin consent required" error:**
- This is expected for organization accounts (Microsoft's policy)
- Contact your Microsoft 365 administrator to grant consent
- Admin can grant consent in Azure Portal > Enterprise applications
- **This is a Microsoft requirement**, not our software limitation

**"Invalid client secret" error:**
- Client secrets expire - create a new one in Azure Portal
- Ensure you copied the "Value" (not the Secret ID)
- Check that the secret hasn't expired

**"AADSTS700016: Application not found" error:**
- Verify the Client ID is correct
- Ensure you're using the Application (client) ID, not the Object ID
- Check that the app registration exists in the correct Azure AD tenant

**"Token refresh failed" error:**
- Ensure `offline_access` permission is granted
- Verify admin consent was granted (for organization accounts)
- Check that the client secret hasn't expired
- **This follows Microsoft's token refresh policies**, not our software

**Can't find API permissions:**
- Ensure you're in the correct app registration
- Try refreshing the Azure Portal page
- Check that you have proper permissions in Azure AD

## 🔗 Additional Resources

- [Microsoft Identity Platform Documentation](https://docs.microsoft.com/en-us/azure/active-directory/develop/)
- [Microsoft Graph API Documentation](https://docs.microsoft.com/en-us/graph/overview)
- [Azure Portal](https://portal.azure.com/)
- [Microsoft OAuth 2.0 Flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

---

**Remember**: Admin consent requirements, account type restrictions, and token policies are **Microsoft's security policies** for Azure applications. These limitations are not imposed by our software. Our module follows Microsoft's OAuth 2.0 standards and works within Microsoft's security framework.
