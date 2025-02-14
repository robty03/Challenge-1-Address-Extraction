# Challenge-1-Address-Extraction
This script extracts company headquarters' addresses from a list of websites stored in a Parquet file. It follows a structured approach to retrieve, validate, and process address data efficiently.

Workflow
Reading Data: Loads the Parquet file and ensures all domains have the correct protocol (http:// or https://).

Checking Accessibility: Uses requests to verify if websites are reachable, optimizing the process with multi-threading.

Extracting Addresses: Scrapes common pages (/contact, /about-us, etc.) using BeautifulSoup and regex to detect address patterns.

Validating with Geolocation: Uses Nominatim (geopy) to confirm and standardize addresses. Retries requests if timeouts occur.

Using Google Maps API: If scraping fails, the script searches for the company’s location via Google’s geocoding API.

Extracting Addresses Using Google Search & Web Scraping : Split the dataset into two parts, search on Google for "domain + head office address" and extract the first relevant link.

Exporting Data: The final structured dataset, including country, city, postal code, and street details, is saved as a CSV file.

Challenges
Bot Detection: Initially attempted Google searches ("company_name + head office") but was blocked after processing 1000+ sites.

Website Variability: Different site structures required regex-based text extraction and API verification.

Performance: Multi-threading speeds up processing, with error handling to manage API limits and network issues.

CONCLUSION
The current script successfully processed 2052 valid websites, extracting at least one address-related field for 1094 of them (53.31%).
