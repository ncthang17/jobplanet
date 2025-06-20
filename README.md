# JobPlanet Company Review Crawler

A Python-based web crawler for collecting company review data from JobPlanet. This tool automates the process of searching for companies, extracting their review statistics, and saving the results for further analysis.

## Features

- **Automated company search:** Searches for companies by name on JobPlanet.
- **Review statistics extraction:** Collects review counts, overall ratings, and detailed category ratings (e.g., welfare, work-life balance, company culture).
- **Progress tracking:** Saves progress and error logs to avoid redundant crawling and handle errors gracefully.
- **Batch processing:** Processes a list of companies from a CSV file and stores results in CSV format.

## Data Files

| File Name                       | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| enterprise_df_10k_utf8_data.csv  | Input CSV containing company names to search for.                           |
| jobplanet_crawling_progress.csv  | Output CSV containing successfully crawled company review data.             |
| jobplanet_crawling_error.csv     | Output CSV containing company names that failed to be crawled, with errors. |

## Prerequisites

- **Python 3.7+**
- **Chrome WebDriver** (for Selenium)
- **Required Python packages:**
  - `selenium`
  - `beautifulsoup4`
  - `pandas`
  - `tqdm`
  - `urllib`
  - `re`

## Installation

1. **Clone the repository:**
git clone https://github.com/your-username/jobplanet-crawler.git
cd jobplanet-crawler

2. **Install dependencies:**
pip install selenium beautifulsoup4 pandas tqdm

*(If you have a `requirements.txt`, use `pip install -r requirements.txt` instead.)*

3. **Download Chrome WebDriver** and place it in your system PATH or specify the path in the script.

## Usage

1. **Prepare your company list:**  
Place your company names in `enterprise_df_10k_utf8_data.csv` (or update the path in the script).

2. **Run the crawler:**
python Crawling_Jobplanet.py

3. **Check output files:**  
- `jobplanet_crawling_progress.csv`: Contains successful crawl results.
- `jobplanet_crawling_error.csv`: Contains failed companies and error messages.

## Script Overview

- **Targets:** Companies listed in the input CSV.
- **Process:** For each company, the script:
- Searches JobPlanet for the company.
- Extracts review statistics from the company’s page.
- Saves results and logs errors.
- **Progress Saving:** Results are saved periodically and at the end of the script.
- **Error Handling:** Companies that fail to be crawled are logged in the error file.

## Example Output

| company_id | name                        | search_rating | review_count | overall_rating | 복지/급여 | 워라밸 | 사내문화 | 승진 기회 | 경영진 | 기업 추천율 | CEO 지지율 | 성장 가능성 | 검색기업명      |
|------------|-----------------------------|---------------|--------------|----------------|-----------|--------|----------|-----------|--------|-------------|------------|-------------|-----------------|
| 361502     | (주)디에스아키종합건설      | 1.0           | 3            | 1.0            | 1.3       | 1.3    | 1.0      | 1.0       | 1.0    | 0%          | 0%         | 0%          | 디에스아키종합건설 |
| ...        | ...                         | ...           | ...          | ...            | ...       | ...    | ...      | ...       | ...    | ...         | ...        | ...         | ...             |

## Error Handling

- **Error Log:**  
Companies that fail to be crawled (e.g., due to network issues, missing data, or script errors) are logged in `jobplanet_crawling_error.csv` with the error message.
- **Resume Capability:**  
The script automatically skips companies already present in either the progress or error files.

## Notes

- **Respect JobPlanet’s terms of service** and avoid excessive requests.
- **Adjust browser options** in the script (e.g., headless mode, user-agent) as needed.
- **Customize the input/output file paths** in the script if necessary.

---

## License

MIT

