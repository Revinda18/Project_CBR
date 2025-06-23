# Overview
This project involves scraping legal case data from the Indonesian Supreme Court's public case directory. The data is extracted, parsed, and saved in CSV format for further analysis in a case-based reasoning (CBR) system.

# Installation
To set up the environment and install required dependencies, follow these steps:
1. Clone or download the project.
2. Install the required Python packages using requirements.txt or manually with the following command: pip install -r requirements.txt or pip install pandas requests beautifulsoup4 pdfminer.six lxml

# How to Run the Pipeline (End-to-End)
1. Mount Google Drive (if using Google Colab):

   The project uses Google Colab for scraping and saving files to your Google Drive. Mount your Google Drive before running the code:
   from google.colab import drive
   drive.mount('/content/drive')

2. Run the Scraper:
   Call the run_scraper() function with a keyword or url to start scraping the data:
   run_scraper(keyword="CPI" )
   By default, it sorts the cases by date and downloads associated PDF files.

3. Output:
   The scraper will download case details into CSV files and PDF files, stored in the folders on Google Drive.

   - Case metadata will be saved in CSV format inside the folder:
     /content/drive/MyDrive/Penalaran Komputer (UAS)/CSV

   - PDF documents (if selected for download) will be stored in:
     /content/drive/MyDrive/Penalaran Komputer (UAS)/PDF

# Example Commands
1. Basic Scraping by Keyword:
   run_scraper(keyword="CPI")
3. Scraping with Custom URL:
   run_scraper(url="https://putusan3.mahkamahagung.go.id/search.html?q=CPI")

# Dependencies
1. Python 3.x
2. pandas
3. requests
4. beautifulsoup4
5. pdfminer.six
6. lxml

# License
This project is licensed under the MIT License - see the LICENSE file for details.
"# PROJECT-CBR" 
