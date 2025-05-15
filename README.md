## Explanation of the TikTok authentication process.

The authentication flow of TikTok follows the following steps:

1. **Initialization** - The Flutter application sets up the deep link manager to receive callbacks.

2. **The user clicks “Connect TikTok,” the application creates the authorization URL and opens the external browser.

3. **Authentication on TikTok** - User authenticates on the TikTok site and authorizes the app.

4. **Redirect to web page** - TikTok redirects to the configured URL (`https://viralystsupport.info/`) with an authorization code.

5. **Redirect webpage** - The tiktok-redirect.html page receives the code and attempts to open the app with the deeplink.

6. **App receives code** - If the app opens via deeplink, it receives the authorization code.

7. **Code exchange for token** - The app sends the authorization code to the TikTok API to get access_token and refresh_token.

8. **Request for user information** - With the access token, the app requests TikTok account information.

9. **The app saves the account information and tokens in the database.

### Critical points:

1. **URI of redirection** - Must match EXACTLY the configuration of TikTok.
2. **Content-Type** - Must be `application/x-www-form-urlencoded`.
3. **Code Cleanup** - Code must be cleaned of asterisks and additional characters.
4. **URL decoding** - Code must be decoded according to the URL before submission.
5. **Parameter formatting** - Two different methods are used to ensure maximum compatibility.

The redirection web page is essential because:
- It handles the various methods of opening apps for different platforms.
- Provides a fallback interface if app opening fails
- Cleans up the authorization code
- Supports manual copying of code
- Provides debugging information in case of problems
