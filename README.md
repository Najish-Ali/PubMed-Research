# PubMed Research Paper Fetcher 💻✨

## Overview

The PubMed Research Paper Fetcher is a Python program that interacts with the PubMed API to retrieve and process research papers based on a given search query. The program is designed to filter papers authored by individuals affiliated with pharmaceutical or biotech companies and save the results in a CSV file for further analysis.

### Key Features

- Fetch research papers from PubMed using a search query.
- Identify non-academic authors based on their affiliations.
- Save filtered results to a CSV file for easy analysis.
- Modular design for flexibility and reusability.

---

## How It Works

### Core Components

#### 1. **PubMedFetcher Class**

The `PubMedFetcher` class handles the main functionality of the program:

- **`fetch_papers(query: str)`**: Fetches and processes papers matching the search query.
- **`_search_papers(query: str)`**: Retrieves PubMed IDs for papers matching the query.
- **`_fetch_details(ids: List[str])`**: Fetches detailed metadata for each paper using their PubMed IDs.
- **`_filter_papers(papers: List[Dict])`**: Filters papers to identify authors affiliated with companies.
- **`_is_academic_author(affiliation: str)`**: Determines if an author is academic based on keywords in their affiliation.

#### 2. **CSV Export**

The program saves the filtered results to a CSV file, including fields like:

- PubMed ID
- Title
- Publication Date
- Non-academic Author(s)
- Company Affiliation(s)

### Filtering Logic

The program identifies non-academic authors by checking affiliations for the absence of keywords like `"university"`, `"institute"`, `"college"`, `"school"`, `"lab"`, and `"hospital"`.

---

## Installation

### Prerequisites

- Python 3.7 or higher
- `requests` library for making API calls

### Steps

1. **Clone the repository**:

    ```bash
    git clone <repository-url>
    cd <repository-folder>
    ```

2. **Install Poetry** (if not already installed):

    - If Poetry is not installed, you can install it using the following command:

    ```bash
    curl -sSL https://install.python-poetry.org | python3 -
    ```

    - Alternatively, follow the installation instructions for your operating system from the official Poetry website: [Poetry Installation Guide](https://python-poetry.org/docs/#installation)

3. **Install the dependencies** using Poetry:

    Run the following command to install all necessary dependencies specified in the `pyproject.toml` file:

    ```bash
    poetry install
    ```

    This will create a virtual environment, install all dependencies (including `requests`), and ensure your environment is set up correctly for the project.

4. **Run the script**:

    After installation, you can run the script with your desired search query:

    ```bash
    poetry run python pubmed_fetcher.py "<your-query>"
    ```

    Example:

    ```bash
    poetry run python pubmed_fetcher.py "cancer treatment"
    ```

    This command will fetch research papers related to the query `"cancer treatment"` from PubMed, filter the results, and save them in a CSV file.

---

## Usage

### Example

1. Run the program with a query, e.g., `"cancer treatment"`:

    ```bash
    poetry run python pubmed_fetcher.py "cancer treatment"
    ```

2. The program fetches, filters, and saves the results to `output.csv`.

3. Open the `output.csv` file to view the results.


### Command-Line Arguments

-   `query` (required): The search query for PubMed.

-   `--file` (optional): The filename to save the results. Default is `output.csv`.

-   `--debug` (optional): Enable debug mode for detailed logs.

Example:

```

python pubmed_fetcher.py "diabetes" --file diabetes_results.csv --debug

```

* * * * *

Code Structure

--------------

### Main Files

-   `pubmed_fetcher.py`: The main script containing the `PubMedFetcher` class and CLI implementation.

-   `requirements.txt`: List of dependencies for the project.

### Key Methods

-   `fetch_papers(query: str)`: Fetches and processes papers matching the query.

-   `_search_papers(query: str)`: Searches for PubMed IDs.

-   `_fetch_details(ids: List[str])`: Retrieves detailed metadata.

-   `_filter_papers(papers: List[Dict])`: Filters papers for non-academic authors.

* * * * *

Results

-------

The output is saved as a CSV file containing:

-   **PubMed ID**: Unique identifier for the paper.

-   **Title**: Title of the paper.

-   **Publication Date**: Date of publication.

-   **Non-academic Author(s)**: Names of non-academic authors.

-   **Company Affiliation(s)**: Affiliations of non-academic authors.

* * * * *

Limitations

-----------

-   API rate limits: Ensure compliance with PubMed's API usage policies.

-   Filtering accuracy: Some affiliations may be incorrectly categorized due to ambiguous keywords.

-   Limited to metadata: The program does not fetch full-text articles.

* * * * *

Future Enhancements

-------------------

-   Implement a graphical user interface (GUI) for easier usage.

-   Add support for additional output formats (e.g., JSON, Excel).

-   Include advanced filtering options for affiliations.

* * * * *

Contributions

-------------

Feel free to contribute by submitting pull requests or opening issues for bugs and feature requests.

* * * * *

Acknowledgments

---------------

This project uses the NCBI PubMed API and Python libraries for implementation. Special thanks to the open-source community for providing resources and guidance.

* * * * *
