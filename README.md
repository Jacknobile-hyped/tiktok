## Explanation of the TikTok Authentication Process.

The TikTok authentication flow follows these steps:

1. **Initialization** - The Flutter app sets up the deep link manager to receive callbacks.

2. **Start Authentication** - The user clicks “Connect TikTok,” the app builds the authorization URL and opens the external browser.

3. **Authentication on TikTok** - The user authenticates on the TikTok site and authorizes the app.

4. **Redirect to web page** - TikTok redirects to the configured URL (`https://viralystsupport.info/`) with an authorization code.

5. **Redirect webpage** - The tiktok-redirect.html page receives the code and attempts to open the app with the deeplink.

6. **App receives code** - If the app opens via deeplink, it receives the authorization code.

7. **Code exchange for token** - The app sends the authorization code to the TikTok API to get access_token and refresh_token.

8. **User info request** - With the access token, the app requests TikTok account information.

9. **Saving account** - The app saves the account information and tokens in the database.

### Critical points:

1. **Redirect URI** - Must match EXACTLY the TikTok configuration.
2. **Content-Type** - Must be `application/x-www-form-urlencoded`.
3. **Code Cleanup** - Code must be cleaned of asterisks and additional characters.
4. **URL Decoding** - Code must be URL-decoded before submission
5. **Parameter Formatting** - Two different methods are used for maximum compatibility.

The redirect web page is essential because:
- It handles various app opening methods for different platforms
- Provides fallback interface if app opening fails
- Cleans up authorization code
- Supports manual copy of code
- Provides debugging information in case of problems


Translated with DeepL.com (free version)
