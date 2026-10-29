# AI Research Task Agent

An AI-powered research assistant that searches the web for a given topic and uses Google's Gemini API to generate a concise, three-point research brief with source links.

## Features

- **Web Search:** Retrieves relevant search results using DuckDuckGo.
- **AI Summarization:** Uses the Google Gemini API to generate concise research briefs.
- **Source Links:** Displays links to the retrieved search results.
- **Interactive UI:** Built using Streamlit.
- **Logging:** Records request activity, execution duration, and errors.
- **Docker:** Packages the application and its dependencies into a container.
- **CI/CD:** GitHub Actions validates Python syntax and builds the Docker image.
- **Cloud Deployment:** Deployed as a Docker-based web service on Render.

## Technology Stack

- Python
- Streamlit
- Google Gemini API (`google-genai`)
- DuckDuckGo Search (`ddgs`)
- Docker
- Git and GitHub
- GitHub Actions
- Render

## Project Structure

```text
task-automation-agent/
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── main.yml
├── app.py
├── requirements.txt
├── Dockerfile
├── .dockerignore
├── .gitignore
└── README.md
```

## Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/Mayurk906/task-automation-agent.git
cd task-automation-agent
```

### 2. Create and activate a virtual environment

Windows PowerShell:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Gemini API key

Create a `.env` file in the project root:

```text
GEMINI_API_KEY=your_gemini_api_key
```

Obtain an API key from [Google AI Studio](https://aistudio.google.com/). Never commit your actual key to GitHub.

### 5. Start the application

```bash
streamlit run app.py
```

Open `http://localhost:8501` in your browser.

## Docker

Build the image:

```bash
docker build -t task-automation-agent .
```

Run the container:

```bash
docker run --rm -p 8501:8501 --env-file .env task-automation-agent
```

Open `http://localhost:8501`.

## CI/CD Workflow

The GitHub Actions workflow is triggered by pushes and pull requests targeting the `main` branch.

The workflow:

1. Checks out the repository.
2. Sets up Python 3.11.
3. Installs application dependencies.
4. Validates Python syntax.
5. Builds the Docker image.

## Deployment

The application is deployed on Render using Docker. Configure `GEMINI_API_KEY` through the Render environment-variable settings.

The public service URL is available from the Render dashboard.

## Security

- API keys are stored as environment variables.
- `.env` and virtual environment directories are excluded from version control.
- API keys should never be committed to the repository or embedded in the Docker image.

## Future Improvements

- Add automated unit and integration tests.
- Add monitoring for latency, failures, and API usage.
- Implement retries and rate-limit handling.
- Add structured evaluation of summary quality.
- Extend CI/CD to automate deployment after successful validation.

## Author

Mayur Khamamkar