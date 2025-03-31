# Cold Email Generator

This is a Streamlit-based application integrated with LangChain to automatically generate cold email content for job applications. The application can extract information from job posting websites and utilize a language model to create tailored email content for specific job positions.

## Key Features

- **Scraping & Data Processing:**  
  - Uses `WebBaseLoader` to fetch content from job posting websites.
  - The `clean_text` function (in `utils.py`) cleans HTML content by removing URLs, special characters, and excessive whitespace.

- **Job Information Extraction:**  
  - The `Chain` class (in `chain.py`) sends prompts to the ChatGroq model (`llama-3.3-70b-versatile`) to extract job-related information from cleaned text.
  - Extracted fields include: `role`, `experience`, `skills`, and `description`.

- **Portfolio Integration:**  
  - The `Portfolio` class (in `portfolio.py`) manages a portfolio loaded from a CSV file (e.g., `app/resource/my_portfolio.csv`).
  - Portfolio data is stored in a vectorstore using ChromaDB, enabling queries for relevant links based on job skills.

- **Email Content Generation:**  
  - Based on job information and portfolio query results, the system generates cold email content in Markdown format.
  - Email content is created by combining prompts with the language model.

- **Web Interface:**  
  - The application uses Streamlit (in `main.py`) to build a user-friendly interface.
  - Users simply input the URL of a job posting and click "Submit" to receive automatically generated cold email content.
  - Results are displayed alongside an illustrative image (`assets/image.jpg`)
  ![](assets/image.jpg)

## Project Structure

```
app_1/
├── chain.py         # Defines the Chain class for interacting with the LLM, extracting info, and generating emails.
├── main.py          # Main Streamlit application, handles user input and displays results.
├── portfolio.py     # Manages portfolio data, loads from CSV, and queries with ChromaDB.
├── utils.py         # Contains text processing functions, e.g., cleaning HTML.
├── resource/
│   └── my_portfolio.csv   # Sample portfolio data (CSV) for the system.
└── assets/
    └── image.jpg    # Illustration image for result display.
```

## Requirements
- Python 3.7 or higher
- Streamlit
- LangChain
- dotenv
- ChromaDB

