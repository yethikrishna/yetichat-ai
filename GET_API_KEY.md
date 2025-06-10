# 🔑 Get Your Free Google Gemini API Key

YetiChat requires a Google Gemini API key to power its AI research capabilities. Here's how to get one for free:

## Step-by-Step Instructions

### 1. Visit Google AI Studio
Go to **[Google AI Studio](https://aistudio.google.com/)** in your web browser.

### 2. Sign In
- Sign in with your Google account
- If you don't have one, create a free Google account first

### 3. Create or Select a Project
- If this is your first time, click "Create new project"
- If you have existing projects, select one from the dropdown

### 4. Get Your API Key
- Look for the **"Get API key"** button (usually in the top-right corner)
- Click it to open the API key dialog
- Your API key will be displayed - **copy it immediately**
- Store it safely (you'll need it for setup)

### 5. Verify Your Key
Your API key should look like this: `AI39a1bC2dE3fG4hI5jK6lM7nO8pQ9rS0tU1vW2xY3z`

## 🔒 Security Important Notes

- **Keep your API key secret** - never share it publicly
- **Don't commit it to Git** - use environment variables
- **Monitor your usage** in Google AI Studio dashboard

## 💰 Free Tier Information

The Google Gemini API offers a generous free tier:
- ✅ Free requests per month
- ✅ No credit card required to start
- ✅ Perfect for personal projects and testing

Monitor your usage in the Google AI Studio dashboard to stay within limits.

## 🚀 Next Steps

Once you have your API key:

1. **For Local Development:**
   ```bash
   cd backend
   cp .env.example .env
   # Edit .env and add: GEMINI_API_KEY="your_api_key_here"
   ```

2. **For Deployment:**
   - Add the API key to your deployment platform's environment variables
   - Never include it directly in your code

## ❓ Troubleshooting

**Can't find the "Get API key" button?**
- Make sure you're signed in to Google AI Studio
- Try refreshing the page
- Check if you're in a valid project

**API key not working?**
- Verify you copied the complete key
- Check for extra spaces or characters
- Make sure the API key is active in Google AI Studio

**Usage limits exceeded?**
- Check your usage in Google AI Studio
- Consider upgrading to a paid plan if needed
- Wait for the limit to reset (usually monthly)

Need more help? Check our [Complete Setup Guide](./docs/yetichat-setup-guide.md)!
