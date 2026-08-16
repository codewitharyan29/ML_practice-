# AmbitionBox Web Scraping

This project demonstrates web scraping of company information from
AmbitionBox's public company listing pages using Python.

## Source

Data was collected from:

https://www.ambitionbox.com/list-of-companies

The scraper processes company listing pages using the `page` parameter.

Example:

https://www.ambitionbox.com/list-of-companies?page=105

## Technologies Used

- Python
- Requests
- BeautifulSoup
- Pandas
- Jupyter Notebook

## Data Collected

The scraper collects the following information:

| Column | Description |
|---|---|
| `Company_Name` | Name of the company |
| `Rating` | Rating given on AmbitionBox |
| `Review_Count` | Number of reviews |
| `Industry` | Industry/category of the company |
| `Headquarters` | Location displayed for the company |

## Scraping Process

1. Send HTTP requests to AmbitionBox company listing pages.
2. Parse the HTML using BeautifulSoup.
3. Extract company details from the company cards.
4. Handle missing values using `None` where information is unavailable.
5. Store the extracted information in a Pandas DataFrame.
6. Combine data from multiple pages.
7. Save the final data as a CSV dataset.

## Dataset

The final dataset is stored as:

```text
ambitionbox_companies.csv