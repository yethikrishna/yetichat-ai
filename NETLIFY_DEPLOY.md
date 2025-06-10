# 🚀 Deploy YetiChat to Netlify

This guide shows you how to deploy YetiChat frontend to Netlify for free.

## Method 1: GitHub + Netlify (Recommended)

1. **Fork this repository** to your GitHub account
2. **Go to [Netlify](https://netlify.com)** and sign up/login
3. **Click "New site from Git"**
4. **Connect your GitHub** and select your forked YetiChat repository
5. **Configure build settings:**
   - Build command: `cd frontend && npm ci && npm run build`
   - Publish directory: `frontend/dist`
6. **Click "Deploy site"**

Your YetiChat frontend will be live in minutes! 🎉

## Method 2: Manual Deploy

1. **Build the project locally:**
   ```bash
   cd frontend
   npm install
   npm run build
   ```

2. **Go to [Netlify](https://netlify.com)** and drag the `frontend/dist` folder to the deploy area

## Adding Backend API URL

⚠️ **Important:** The frontend needs a backend API to function.

### Option A: Deploy Backend Separately
1. Deploy the backend to a service like Railway, Heroku, or similar
2. In Netlify, go to Site Settings → Environment Variables
3. Add: `VITE_API_URL` = `https://your-backend-url.com`

### Option B: Use Local Backend for Testing
- The deployed frontend will try to connect to `http://localhost:8123` by default
- Run the backend locally when testing the deployed frontend

## 🔧 Environment Variables in Netlify

1. Go to your site in Netlify dashboard
2. Navigate to Site Settings → Environment Variables
3. Add any needed variables:
   - `VITE_API_URL`: Your backend URL

## 🎯 Next Steps

- Set up the backend using our [Complete Setup Guide](./docs/yetichat-setup-guide.md)
- Customize YetiChat branding and features
- Monitor usage in Netlify dashboard

**Need help?** Check the [Complete Setup Guide](./docs/yetichat-setup-guide.md) for detailed instructions.
