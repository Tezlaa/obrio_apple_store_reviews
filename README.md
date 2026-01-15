# Apple Store Review Analysis API

This project provides a REST API to collect, process, and analyze reviews from the Apple Store for a specific app. It generates metrics and actionable insights using Natural Language Processing (NLP).

## Features

1.  **Data Collection**: Fetches 100 random reviews for a specified app using `app-store-scraper`.
2.  **Data Processing**: Cleans and preprocesses review text.
3.  **Metrics**: Calculates average rating and rating distribution.
4.  **Insights**: Performs sentiment analysis and extracts common keywords from negative reviews.
5.  **API**: Key endpoints to fetch analysis and download raw data.

## Setup Instructions

### Prerequisites

-   Python 3.8+
-   pip

### Installation

1.  Clone the repository (if applicable) or navigate to the project folder.
2.  Create a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```
3.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
4.  (Optional) Download NLTK data manually if the auto-download fails:
    ```bash
    python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords')"
    ```

## Running the API

Start the server using `uvicorn`:

```bash
uvicorn app.main:app --reload
```

The API will be available at `http://localhost:8000`.
API Documentation (Swagger UI) is available at `http://localhost:8000/docs`.

### Docker

You can also run the application using Docker.

1.  **Build the Docker image:**

    ```bash
    docker build -t app-store-reviews .
    ```

2.  **Run the container:**
    ```bash
    docker run -p 8000:8000 app-store-reviews
    ```

### Endpoint: Analyze Reviews

**POST** `/api/analyze`

Body:

```json
{
    "app_name": "minecraft",
    "app_id": "479516143",
    "country": "us",
    "count": 100
}
```

Response includes metrics (average rating, distribution) and insights (sentiment, negative keywords).

### Endpoint: Download Reviews

**POST** `/api/reviews/download`

Same body as above. Returns a CSV file with the reviews.

## Design Decisions

-   **FastAPI**: Chosen for its speed, automatic documentation, and ease of use.
-   **app-store-scraper**: Used to interface with the Apple App Store.
-   **TextBlob**: Used for simple and effective sentiment analysis.
-   **NLTK**: Used for tokenization and stopword removal to find meaningful keywords.
-   **Pandas**: Used for data manipulation and analysis.

## Sample Report

See `sample_report.json` for an example of the analysis output.
# orbio_test_task
# orbio_test_task
# orbio_test_task
