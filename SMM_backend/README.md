# Social Media Monitoring Backend (SMM)

This project is a social media scraper and data collector that fetches data from X,Facebook and Instagram. It performs sentiment analysis, and sends alerts via Twilio. The project is structured into multiple Python scripts, each handling different aspects of the functionality.

## Project Structure

- `run.py`: Main entry point for running the Flask server and managing processes.
- `meta.py`: Handles Meta (Facebook and Instagram) scraping and data merging.
- `user_scraper.py`: Contains functions for scraping Twitter and Instagram.
- `twilio_sender.py`: Sends SMS alerts using Twilio.
- `data_collector.py`: Manages data merging, sentiment analysis, and periodic tasks.
- `utils.py`: Contains shared utility functions.

## Setup

### Prerequisites

- Python 3.7+
- pip (Python package installer)
- Virtual environment (optional but recommended)

### Installation

1. **Clone the repository:**

    ```sh
    git clone https://github.com/yourusername/social-media-scraper.git
    cd social-media-scraper
    ```

2. **Create and activate a virtual environment:**

    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install the required packages:**

    ```sh
    pip install -r requirements.txt
    ```

4. **Set up environment variables:**

    Create a `.env` file in the root directory and add the following variables:

    ```env
    APIFY_API_TOKEN=your_apify_api_token
    APIFY_BASE_URL=https://api.apify.com/v2
    TWILIO_ACCOUNT_SID=your_twilio_account_sid
    TWILIO_AUTH_TOKEN=your_twilio_auth_token
    ALERT_TO_NUMBER=your_alert_to_number
    TWILIO_FROM_NUMBER=your_twilio_from_number
    TWITTER_FOLDER_PATH=twitter_data
    TWITTER_OUTPUT_FILE=twitter_output.json
    META_INPUT_FILE=meta_input.json
    META_OUTPUT_FILE=meta_output.json
    FLASK_RUN_PORT=5000
    FLASK_DEBUG=1
    ```

5. **Ensure the necessary directories exist:**

    ```sh
    mkdir -p twitter_data meta_input
    ```

### Twitter Scraper Setup

The Twitter scraping functionality is based on the code from [godkingjay's selenium-twitter-scraper](https://github.com/godkingjay/selenium-twitter-scraper).

1. **Install dependencies:**

    ```sh
    pip install -r requirements.txt
    ```

2. **Set up environment variables for Twitter authentication:**

    Create a `.env` file in the `twitter` directory and add the following variables:

    ```env
    TWITTER_USERNAME=# Your Twitter Handle
    TWITTER_PASSWORD=# Your Twitter Password
    ```

## Usage

### Running the Server

To start the Flask server and the periodic tasks, run:

```sh
python run.py
```

### API Endpoints

- **Start Scrapers:**

    ```http
    GET /start_scrapers
    ```

    Starts the scrapers and runs them continuously.

- **Get Twitter Data:**

    ```http
    GET /twitter_data
    ```

    Returns the merged Twitter data.

- **Get Meta Data:**

    ```http
    GET /meta_data
    ```

    Returns the merged Meta data.

- **Get Status:**

    ```http
    GET /status
    ```

    Returns the status of the scrapers and sentiment analysis.

- **Scrape User:**

    ```http
    POST /scrape
    ```

    Body parameters:
    - `platform`: "twitter" or "instagram"
    - `handle`: The handle of the user to scrape
    - `num_posts`: Number of posts to scrape (default: 10)

    Example:

    ```json
    {
        "platform": "twitter",
        "handle": "example_handle",
        "num_posts": 10
    }
    ```
**Start Identify Script:**

    ```http
    POST /start-identify
    ```

    Starts the `identify.py` script, which is used to detect the origin of posts.
     Currently, it uses dummy data.
     
## Credits

The Twitter scraping functionality is based on the code from [godkingjay's selenium-twitter-scraper](https://github.com/godkingjay/selenium-twitter-scraper).

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes.


### Summary of `README.md`:
1. **Project Structure**: Describes the purpose of each file.
2. **Setup**: Instructions for cloning the repository, setting up a virtual environment, installing dependencies, and configuring environment variables.
3. **Twitter Scraper Setup**: Specific instructions for setting up the Twitter scraper, including environment variables for authentication.
4. **Usage**: Instructions for running the server and using the API endpoints.
5. **Credits**: Acknowledges the use of [godkingjay's selenium-twitter-scraper](https://github.com/godkingjay/selenium-twitter-scraper) for Twitter scraping functionality.
6. **Contributing**: Information on how to contribute to the project.

#
This should provide clear instructions on how to set up and run the project.
````