# AI Football Scout: Streamlined Player Analysis with Gemini

## 1. Project Overview

**AI Football Scout** is a Python-based tool designed to automate and enhance the football player scouting process. Leveraging the power of Google's Gemini AI model, this project allows users to quickly generate insightful scouting reports from readily available online data.  Instead of complex pipelines, we focus on Gemini's robust capabilities to process information efficiently, making player analysis faster and more accessible.

This project prioritizes simplicity and ease of use, enabling football enthusiasts, scouts, and analysts to gain valuable insights into players by simply providing URLs to player statistics or uploading their own scouting data files.

## 2. Problem Statement

Traditional football scouting is often:

* **Time-Consuming:** Manually analyzing player statistics, reading reports, and watching videos takes significant time.
* **Data Overload:**  The sheer volume of available football data can be overwhelming to process effectively.
* **Subjective and Inconsistent:** Human scouting reports can be influenced by personal biases and vary in quality.
* **Difficult to Scale:** Expanding scouting operations to cover more players and leagues requires significant resources.

**AI Football Scout** aims to address these problems by providing a streamlined AI-powered solution for faster, more consistent, and data-driven player analysis.

## 3. Proposed Solution: Gemini-Powered Scouting

This project utilizes Gemini's strengths – its large context window, multimodal processing, and natural language understanding – to create a simple yet powerful scouting tool.  Here's how it works:

* **Flexible Data Input:** Users can provide player data in two primary ways:
    * **URL Input:** Paste URLs to web pages containing player statistics (e.g., from football statistics websites like FBref). The tool will scrape the relevant data.
    * **File Upload:** Upload local files containing scouting data. This can be:
        * **Statistical Data (CSV, TXT):** Structured numerical data.
        * **Text-Based Scouting Reports (TXT, Markdown):** Unstructured qualitative reports.
* **Gemini AI Analysis:**  The provided data (whether from URL or file) is fed to the Gemini AI model along with a well-crafted prompt. Gemini then performs the following:
    * **Data Interpretation:** Understands and processes both structured statistical data and unstructured text reports.
    * **Scouting Report Generation:** Generates a structured scouting report summarizing player strengths, weaknesses, potential, and overall evaluation.
    * **Contextual Understanding:**  Leverages its vast knowledge base to provide context and insights relevant to football.
* **Markdown Report Output:** The AI-generated scouting report is delivered in a clear and readable Markdown format, easily viewable and shareable.

**Key Simplifications Compared to Complex Designs:**

* **Direct Gemini Integration:** We bypass complex RAG (Retrieval Augmented Generation) pipelines and vector databases. Gemini's large context window allows us to feed the relevant data directly within the prompt.
* **Focus on Core Functionality:**  We prioritize essential features (data input, report generation) over advanced functionalities like complex video analysis or user interfaces in the initial phase.
* **Simplified Architecture:**  The system architecture is kept minimal, relying heavily on Gemini for processing and analysis.

## 4. System Architecture (Simplified)

```
User Input (URL or File) --> Data Ingestion --> Gemini AI Model --> Scouting Report (Markdown)
```

**Components:**

1.  **Data Input:** Handles URL input and file uploads.
2.  **Data Ingestion:**
    *   **Web Scraper (for URLs):**  Uses libraries like `BeautifulSoup` and `requests` to extract data from web pages.
    *   **File Reader (for Files):** Reads data from uploaded files (CSV, TXT, Markdown).
3.  **Gemini AI Model:**  The core processing engine, using the `google-generativeai` library to interact with the Gemini API.
4.  **Scouting Report Output:** Generates the final scouting report in Markdown format.

## 5. Technology Stack

*   **Programming Language:** Python
*   **Web Scraping Libraries:** `requests`, `BeautifulSoup4` (for URL input)
*   **Data Manipulation:** `pandas` (for handling statistical data - optional but recommended)
*   **AI Model Integration:** `google-generativeai` (for Gemini API access)
*   **Markdown Formatting:** Standard Python Markdown libraries (or simple string formatting for basic Markdown).

## 6. Features and Functionality

**Core Features (Initially Implemented):**

*   **URL-Based Data Input:**
    *   Accepts URLs to player statistics pages (e.g., FBref player pages).
    *   Scrapes relevant statistical tables from the webpage.
*   **File-Based Data Input:**
    *   Supports uploading local files:
        *   **CSV/TXT Statistical Data:** For structured numerical player stats.
        *   **TXT/Markdown Scouting Reports:** For existing text-based scouting reports.
*   **Gemini-Powered Scouting Report Generation:**
    *   Generates a structured Markdown scouting report based on the input data.
    *   Report includes sections for:
        *   Player Summary (Name, Position, etc.)
        *   Strengths (based on data)
        *   Weaknesses (based on data)
        *   Potential/Summary
        *   (Customizable sections in future iterations)
*   **Markdown Report Output:**
    *   Outputs the scouting report in a well-formatted Markdown file (`.md`).

**Future Enhancements (Feasible and Incremental):**

*   **Video URL Input:**
    *   Accept video URLs (e.g., YouTube, Vimeo links).
    *   Use Gemini's multimodal capabilities to *briefly* analyze video descriptions or transcripts (initially, not deep video analysis).  This could be used to add context from video content to the report.
*   **Football Manager Data Integration:**
    *   Allow input of Football Manager player data (if users can export or provide it in a compatible format).
    *   Incorporate FM attributes into the scouting report generation process.
*   **Improved Data Handling:**
    *   More robust error handling for web scraping and file parsing.
    *   Support for more data sources and website structures.
*   **Basic Command-Line Interface (CLI):**
    *   Develop a simple CLI for easier script execution and parameter input.
*   **Customizable Report Prompts:**
    *   Allow users to adjust the prompts sent to Gemini to customize the focus or style of the generated reports.
*   **Very Basic Web Interface (Optional, later stage):**
    *   If desired, create a *very simple* web interface using Flask or Streamlit for easier file uploads and URL input (keep it minimal).

**Features Explicitly Avoided (for Simplicity - Initially):**

*   Complex User Interface (Full web application with databases, user accounts, etc.)
*   Deep Video Analysis using AI (Beyond basic text from video descriptions)
*   Real-time Data Streaming
*   Advanced Machine Learning Models beyond Gemini
*   Highly Customizable Report Templates (Start with a standard template)

## 7. Getting Started

### Prerequisites

1.  **Python 3.7+** installed on your system.
2.  **Google Generative AI API Key:** You need to obtain an API key from Google AI Studio to use the Gemini API. [Link to Google AI Studio](https://makersuite.google.com/app/apikey)

### Installation

1.  **Clone the Repository (Once the project is on GitHub):**
    ```bash
    git clone [repository-url]
    cd AI-Football-Scout
    ```

2.  **Install Required Python Libraries:**
    ```bash
    pip install requests beautifulsoup4 pandas google-generativeai
    ```

### Usage

1.  **Set your Gemini API Key:**
    *   You will need to set your API key as an environment variable or directly in the script (less secure, but simpler for initial testing).  *Example approach will be provided in the code.*

2.  **Run the Script:**

    ```bash
    python scout_script.py --data_type [url|file] --data_source [URL or File Path]
    ```

    *   **`--data_type`**:  Specify `url` if you are providing a website URL or `file` if you are uploading a local file.
    *   **`--data_source`**:
        *   If `--data_type url`, provide the full URL to the player statistics page.
        *   If `--data_type file`, provide the path to your local data file.

    **Example Usage (URL Input):**

    ```bash
    python scout_script.py --data_type url --data_source https://fbref.com/en/players/82ec26c1/Lamine-Yamal
    ```

    **Example Usage (File Input - Statistical CSV):**

    ```bash
    python scout_script.py --data_type file --data_source player_stats.csv
    ```

    **Example Usage (File Input - Scouting Report TXT):**

    ```bash
    python scout_script.py --data_type file --data_source existing_report.txt
    ```

3.  **Output:**
    *   A Markdown file named `player_scouting_report.md` will be generated in the same directory as the script. This file will contain the AI-generated scouting report.

### Example Data Files and URLs

*   **Example FBref URL:**  `https://fbref.com/en/players/82ec26c1/Lamine-Yamal` (Replace with other player URLs from FBref or similar sites)
*   **Example CSV Statistical Data ( `player_stats.csv` ):**

    ```csv
    Statistic,Per 90,Percentile
    Non-Penalty Goals,0.15,24.0
    npxG: Non-Penalty xG,0.24,58.0
    Shots Total,2.61,71.0
    Assists,0.22,63.0
    ```

*   **Example Text Scouting Report ( `existing_report.txt` ):**

    ```text
    This player is technically gifted with excellent dribbling skills.
    However, his decision-making in the final third needs improvement.
    ... (rest of the report) ...
    ```

## 8. Benefits of AI Football Scout

*   **Speed and Efficiency:** Generate scouting reports much faster than manual analysis.
*   **Data-Driven Insights:** Provides objective analysis based on available data.
*   **Accessibility:** Easy to use, requiring minimal technical expertise.
*   **Improved Consistency:** AI-generated reports offer a more consistent evaluation framework.
*   **Focus on Gemini's Strengths:**  Leverages the power of a cutting-edge AI model for intelligent analysis.
*   **Simpler and More Feasible:**  Prioritizes a practical and achievable design for rapid development and usability.

## 9. Contributing

Contributions to **AI Football Scout** are welcome!  Please feel free to:

*   **Report Issues:** If you find bugs or have suggestions for improvements, please open an issue on GitHub.
*   **Submit Pull Requests:** If you want to contribute code, please fork the repository, create a new branch for your feature, and submit a pull request.

## 10. License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.

---

**AI Football Scout** is a project aimed at making football scouting more efficient and data-driven. By leveraging the power of Gemini AI in a simple and accessible way, we hope to empower football enthusiasts and analysts with valuable insights into player performance and potential.
