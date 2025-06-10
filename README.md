# YetiChat - AI Research Assistant

YetiChat is a powerful fullstack AI research assistant built with React frontend and LangGraph-powered backend. YetiChat performs comprehensive research on your queries by dynamically generating search terms, querying the web, and providing well-supported answers with citations. Experience intelligent conversational AI powered by Google's Gemini models and LangGraph.

![YetiChat AI Research Assistant](./app.png)

## 📋 Quick Links

- 🔑 **[Get Free API Key](./GET_API_KEY.md)** - Get your Google Gemini API key in 5 minutes
- 🚀 **[Deploy to Netlify](./NETLIFY_DEPLOY.md)** - Deploy YetiChat frontend for free
- 📚 **[Complete Setup Guide](./docs/yetichat-setup-guide.md)** - Detailed instructions for full setup
- 🛠️ **[Local Development](#-quick-start)** - Get started developing locally

## ✨ Features

- 🤖 **AI-Powered Research**: Advanced conversational AI that researches any topic
- 🔍 **Smart Query Generation**: Dynamically creates optimal search queries
- 🌐 **Web Research Integration**: Searches and analyzes web sources automatically  
- 🧠 **Intelligent Reflection**: Identifies knowledge gaps and refines searches
- 📚 **Cited Answers**: Provides well-sourced responses with citations
- ⚡ **Real-time Streaming**: Watch YetiChat research and think in real-time
- 🎨 **Modern UI**: Clean, responsive interface built with React and Tailwind
- 🚀 **Easy Deployment**: One-click deploy to Netlify

## Project Structure

The project is divided into two main directories:

-   `frontend/`: Contains the React application built with Vite.
-   `backend/`: Contains the LangGraph/FastAPI application, including the research agent logic.

## 🚀 Quick Start

### Get Your Free Google API Key
1. Visit [Google AI Studio](https://aistudio.google.com/)
2. Create a project and get your free API key
3. Copy the API key for the next steps

### Local Development Setup

**Prerequisites:**
- Node.js 18+ and npm
- Python 3.8+
- Google Gemini API key (free)

**Setup:**
```bash
# Clone and navigate
git clone https://github.com/your-username/yetichat.git
cd yetichat

# Backend setup
cd backend
cp .env.example .env
# Edit .env and add: GEMINI_API_KEY="your_api_key_here"
pip install .

# Frontend setup  
cd ../frontend
npm install

# Run development servers
cd ..
make dev
```

Open your browser to `http://localhost:5173` to start using YetiChat!

### Netlify Deployment (Frontend Only)

**Quick Deploy:**
1. Fork this repository to your GitHub account
2. Connect your GitHub repo to Netlify
3. Netlify will automatically deploy the frontend
4. For the backend, see our [Complete Setup Guide](./docs/yetichat-setup-guide.md)

**📚 Need help?** Check our [Complete Setup Guide](./docs/yetichat-setup-guide.md) for detailed instructions, backend deployment options, and troubleshooting.

## How the Backend Agent Works (High-Level)

The core of the backend is a LangGraph agent defined in `backend/src/agent/graph.py`. It follows these steps:

![Agent Flow](./agent.png)

1.  **Generate Initial Queries:** Based on your input, it generates a set of initial search queries using a Gemini model.
2.  **Web Research:** For each query, it uses the Gemini model with the Google Search API to find relevant web pages.
3.  **Reflection & Knowledge Gap Analysis:** The agent analyzes the search results to determine if the information is sufficient or if there are knowledge gaps. It uses a Gemini model for this reflection process.
4.  **Iterative Refinement:** If gaps are found or the information is insufficient, it generates follow-up queries and repeats the web research and reflection steps (up to a configured maximum number of loops).
5.  **Finalize Answer:** Once the research is deemed sufficient, the agent synthesizes the gathered information into a coherent answer, including citations from the web sources, using a Gemini model.

## Deployment

In production, the backend server serves the optimized static frontend build. LangGraph requires a Redis instance and a Postgres database. Redis is used as a pub-sub broker to enable streaming real time output from background runs. Postgres is used to store assistants, threads, runs, persist thread state and long term memory, and to manage the state of the background task queue with 'exactly once' semantics. For more details on how to deploy the backend server, take a look at the [LangGraph Documentation](https://langchain-ai.github.io/langgraph/concepts/deployment_options/). Below is an example of how to build a Docker image that includes the optimized frontend build and the backend server and run it via `docker-compose`.

_Note: For the docker-compose.yml example you need a LangSmith API key, you can get one from [LangSmith](https://smith.langchain.com/settings)._

_Note: If you are not running the docker-compose.yml example or exposing the backend server to the public internet, you update the `apiUrl` in the `frontend/src/App.tsx` file your host. Currently the `apiUrl` is set to `http://localhost:8123` for docker-compose or `http://localhost:2024` for development._

**1. Build the Docker Image:**

   Run the following command from the **project root directory**:
   ```bash
   docker build -t gemini-fullstack-langgraph -f Dockerfile .
   ```
**2. Run the Production Server:**

   ```bash
   GEMINI_API_KEY=<your_gemini_api_key> LANGSMITH_API_KEY=<your_langsmith_api_key> docker-compose up
   ```

Open your browser and navigate to `http://localhost:8123/app/` to see the application. The API will be available at `http://localhost:8123`.

## Technologies Used

- [React](https://reactjs.org/) (with [Vite](https://vitejs.dev/)) - For the frontend user interface.
- [Tailwind CSS](https://tailwindcss.com/) - For styling.
- [Shadcn UI](https://ui.shadcn.com/) - For components.
- [LangGraph](https://github.com/langchain-ai/langgraph) - For building the backend research agent.
- [Google Gemini](https://ai.google.dev/models/gemini) - LLM for query generation, reflection, and answer synthesis.

## 🚀 Deployment Options

### Frontend (Static Site)
- **Netlify** (Recommended): [Deploy Guide](./NETLIFY_DEPLOY.md)
- **Vercel**: Similar to Netlify, upload `frontend/dist` folder
- **GitHub Pages**: Upload built files to gh-pages branch

### Backend (API Server)
- **Railway**: Easy one-click deployment
- **Heroku**: Classic platform with free tier
- **Railway**: Modern platform with generous free tier
- **Docker**: Use included Dockerfile for any platform

## ⚠️ Important Notes

1. **API Key Required**: You need a free Google Gemini API key - [Get it here](./GET_API_KEY.md)
2. **Frontend Only**: Netlify deployment only hosts the frontend - backend needed separately
3. **Free Tiers**: Both Google Gemini and deployment platforms offer generous free tiers

## 🆘 Need Help?

- 📖 **Setup Issues**: Check our [Complete Setup Guide](./docs/yetichat-setup-guide.md)
- 🔑 **API Key Help**: See [API Key Guide](./GET_API_KEY.md)
- 🚀 **Deployment Help**: See [Netlify Deploy Guide](./NETLIFY_DEPLOY.md)
- 🐛 **Found a Bug**: Open an issue on GitHub

## 🎯 What's Next?

1. **Get your API key** from Google AI Studio
2. **Deploy the frontend** to Netlify for free
3. **Set up the backend** using our deployment guide
4. **Customize YetiChat** for your needs

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

## Quick Start Instructions

Follow these steps to get your project running:

1.  **Set up your Gemini API Key:**
    *   Open the `backend/.env` file.
    *   Replace `YOUR_API_KEY_HERE` with your actual Google Gemini API key. You can get your free API key from [Google AI Studio](https://aistudio.google.com/).

2.  **Install Dependencies and Compile:**
    Open your terminal and run the following command from the root of the project:
    ```bash
    pip install -e ./backend && npm install --prefix frontend
    ```

3.  **Run the Development Server:**
    After the installation is complete, run the following command:
    ```bash
    make dev
    ```
    This will start both the backend and frontend development servers. You should then be able to access your agent in your browser.

*(These instructions are based on the setup guide provided in the issue.)*

## Deploying Yetichat to Netlify

You can deploy the frontend of your Yetichat agent to Netlify for a live, shareable version.

### Prerequisites:

1.  **Push to GitHub:** Ensure your project, with your latest changes, is pushed to a GitHub repository.
2.  **Gemini API Key:** You must have your Gemini API key set in `backend/.env` for local testing, but for Netlify, the backend needs to be accessible via a public URL, and the frontend needs to know this URL.
3.  **Deployed Backend (Optional but Recommended):**
    *   For the Netlify-deployed frontend to fully function, it needs to connect to a running backend. You can deploy the backend (the `backend` folder contents) to a cloud service (e.g., Railway, Render, Google Cloud Run, etc.).
    *   If you don't deploy the backend, your Netlify frontend will only work if it can connect to your local backend running on `http://127.0.0.1:2024` (this is the default proxy target if `VITE_API_URL` is not set during build). This is usually only feasible for testing.

### Netlify Setup Steps:

1.  **Go to Netlify:** Sign up or log in at [Netlify.com](https://netlify.com).
2.  **New Site from Git:**
    *   Click "Add new site" (or "New site from Git").
    *   Choose "Import an existing project" and connect to your GitHub account.
    *   Select your Yetichat GitHub repository.
3.  **Build Settings:**
    *   Netlify should automatically detect the settings from `netlify.toml` if it's in your repository's root.
    *   **Build command:** `cd frontend && npm ci && npm run build`
    *   **Publish directory:** `frontend/dist`
    *   Ensure the Node version matches (e.g., Node 18, as specified in `netlify.toml`).
4.  **Environment Variables (Crucial!):**
    *   In your Netlify site's settings, navigate to "Site configuration" > "Environment variables".
    *   Add a variable:
        *   **Key:** `VITE_API_URL`
        *   **Value:** The URL of your deployed backend (e.g., `https://your-yetichat-backend.onrender.com/api`).
        *   *Note:* The `/api` suffix might be needed depending on how your backend routes are structured and how the frontend makes calls. The default setup proxies requests starting with `/api` to your backend. If your backend is already serving under an `/api` path, you might not need it in `VITE_API_URL`. Test this carefully. If you are using the default Vite proxy target for local dev (`http://127.0.0.1:2024`), your deployed backend should also expect API calls at a similar base path.
5.  **Deploy:** Click "Deploy site" (or the equivalent).

Netlify will then build and deploy your frontend.

For more detailed steps, you can also refer to the `NETLIFY_DEPLOY.MD` file in this repository.