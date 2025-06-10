# YetiChat Setup Guide

This guide provides comprehensive instructions for setting up and deploying YetiChat, a full-stack AI research assistant.

## 1. Getting a Free Google Gemini API Key

YetiChat uses the Google Gemini API to power its research and conversational AI capabilities. You'll need a free API key to run the backend.

### Step-by-Step Instructions

1.  **Go to Google AI Studio:** Open your web browser and navigate to [https://aistudio.google.com/](https://aistudio.google.com/).

2.  **Create a New Project or Use an Existing One:**
    *   If you're new to Google AI Studio, you'll be prompted to create a new project.
    *   If you have existing projects, you can select one from the list.

3.  **Get Your API Key:**
    *   Once you're in a project, click on the "**Get API key**" button in the upper right corner of the screen.
    *   A dialog box will appear with your API key. Copy the key and store it in a safe place.

### Important Notes

*   **Free Tier Limitations:** The free tier of the Gemini API has usage limitations. Be sure to check the [Google AI Platform pricing page](https://cloud.google.com/vertex-ai/pricing) for the latest information on free tier limits.
*   **Usage Monitoring:** You can monitor your API usage in the Google AI Studio dashboard.

## 2. YetiChat Setup Instructions

Follow these steps to set up and run YetiChat locally for development.

### Prerequisites

*   Node.js and npm (or yarn/pnpm)
*   Python 3.8+
*   A Google Gemini API Key (see section 1)

### Step-by-Step Instructions

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/yetichat.git
    cd yetichat
    ```

2.  **Install Dependencies:**

    *   **Backend:**
        ```bash
        cd backend
        pip install .
        ```

    *   **Frontend:**
        ```bash
        cd frontend
        npm install
        ```

3.  **Configure Environment Variables:**

    *   Navigate to the `backend/` directory.
    *   Create a file named `.env` by copying the `backend/.env.example` file.
    *   Open the `.env` file and add your Gemini API key:
        ```
        GEMINI_API_KEY="YOUR_ACTUAL_API_KEY"
        ```

4.  **Run Locally for Development:**

    *   From the project root directory, run the following command:
        ```bash
        make dev
        ```
    *   This will start both the backend and frontend development servers.
    *   Open your browser and navigate to `http://localhost:5173` to view the application.

5.  **Build for Production:**

    *   To build the application for production, run the following command from the project root directory:
        ```bash
        make build
        ```
    *   This will create an optimized build of the frontend in the `frontend/dist` directory.

## 3. Netlify Deployment Guide

This section explains how to deploy the YetiChat frontend to Netlify.

### Step-by-Step Instructions

1.  **Prepare the Project for Netlify:**
    *   No special preparation is needed. The `netlify.toml` file in the project root already configures the build settings for Netlify.

2.  **Deploy Frontend to Netlify:**
    *   Create a new site on Netlify and connect it to your GitHub repository.
    *   Netlify will automatically detect the `netlify.toml` file and configure the build settings.
    *   Click the "Deploy site" button to start the deployment.

3.  **Set Up Environment Variables in Netlify:**
    *   In your Netlify site dashboard, go to **Site settings > Build & deploy > Environment**.
    *   Add a new environment variable:
        *   **Key:** `VITE_API_URL`
        *   **Value:** The URL of your deployed backend service.

4.  **Connect to a Backend Service:**
    *   The YetiChat frontend needs a backend to function. You can use a local development server or deploy the backend to a cloud platform (see section 4).
    *   Once your backend is deployed, set the `VITE_API_URL` environment variable in Netlify to the URL of your backend service.

## 4. Backend Deployment Options

Here are some options for deploying the YetiChat backend:

*   **Local Development Server:** For testing and development, you can run the backend server locally using `make dev`.
*   **Cloud Platforms:** You can deploy the backend to cloud platforms like:
    *   **Railway:** A platform that makes it easy to deploy web applications.
    *   **Heroku:** A popular platform for deploying and scaling applications.
*   **Docker Deployment:** The project includes a `Dockerfile` and `docker-compose.yml` for deploying the backend with Docker.

## 5. Troubleshooting

Here are some common issues and their solutions:

*   **`GEMINI_API_KEY` not found:** Make sure you have created a `.env` file in the `backend/` directory and added your Gemini API key to it.
*   **Frontend not connecting to backend:**
    *   Check that the backend server is running.
    *   Verify that the `VITE_API_URL` environment variable is set correctly in your frontend environment (or in Netlify).
*   **"Cannot find module" errors during installation:** Make sure you have installed the dependencies for both the frontend and backend.


## 4. Backend Deployment Options

Here are some options for deploying the YetiChat backend:

*   **Local Development Server:** For testing and development, you can run the backend server locally using `make dev`.
*   **Cloud Platforms:** You can deploy the backend to cloud platforms like:
    *   **Railway:** A platform that makes it easy to deploy web applications.
    *   **Heroku:** A popular platform for deploying and scaling applications.
*   **Docker Deployment:** The project includes a `Dockerfile` and `docker-compose.yml` for deploying the backend with Docker. To run the production server with Docker, you will need to provide both your `GEMINI_API_KEY` and a `LANGSMITH_API_KEY`.

    ```bash
    GEMINI_API_KEY=<your_gemini_api_key> LANGSMITH_API_KEY=<your_langsmith_api_key> docker-compose up
    ```

## 5. Troubleshooting

Here are some common issues and their solutions:

*   **`GEMINI_API_KEY` not found:** Make sure you have created a `.env` file in the `backend/` directory and added your Gemini API key to it.
*   **Frontend not connecting to backend:**
    *   Check that the backend server is running.
    *   Verify that the `VITE_API_URL` environment variable is set correctly in your frontend environment (or in Netlify).
    *   For local development, you may need to edit the `apiUrl` in `frontend/src/App.tsx` to point to your local backend server, which is `http://localhost:2024` for development or `http://localhost:8123` for docker-compose.
*   **"Cannot find module" errors during installation:** Make sure you have installed the dependencies for both the frontend and backend.
