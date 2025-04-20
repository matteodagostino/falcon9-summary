# falcon9-summary


# Webscraper chosen was beautiful soup

For this project, I initially made the mistake of trying to web scrape the Falcon 9 booster data using a basic Python approach with `requests` and `print()` statements, rather than using a proper HTML parser like Beautiful Soup. While the initial data extraction appeared to work on a basic level, it quickly became clear that the structure of Wikipedia tables was too complex for that approach. I ran into several formatting and encoding issues, including strange special characters and malformed outputs when saving to CSV files.

After realizing that I needed a proper scraper, I switched to Beautiful Soup. Once I did, I was able to navigate the HTML structure more accurately and extract rows from the different block tables Block 1, Block 4, Block 5 in a consistent way. While the data was still messy at times, this transition was the turning point that allowed me to finally parse and structure the data properly.

One of the trickiest issues was handling the special characters that appeared in launch site names, like weird hyphen variations or invisible spaces. Another was getting the turnaround time column to show up properly. Initially it wasn’t being parsed at all because I had misaligned the keys or missed the column entirely depending on the block version. It took some debugging across multiple table variations, but I was able to clean it up.

I also used pandas for handling and storing the final data, using `.to_csv()` to export everything into a structured CSV format. This fixed most of the formatting problems I had before, and ensured consistent encoding when saving the data.

AI WEB SCRAPING WAS SCRAPEGRAPHAI

For the AI-assisted portion of this assignment, I used Scrapegraphai. I used their web interface since I had issues getting the Python package to work locally and provided a prompt asking the AI to extract fields like:

- Engine Number  
- Block Type  
- Flight Number  
- Flight Type  
- Launch Date  
- Launch Pad  
- Landing Location  
- Turnaround Time  
- Engine Status  
- Total Launches  

The AI-generated data was returned in JSON format. However, it only partially scraped the full page — some blocks were missing, and turnaround time was mostly empty or incorrect. I saved the output as a JSON file, converted it to a CSV using Python, and then used it for the AI versions of the scripts.

Prompt Strategy

The key with AI scraping was to be very clear and literal in the prompt. I had to explicitly state that I needed all rows from each table, and list every field I needed extracted. Even with a solid prompt, the results were still incomplete, which reminded me that AI scraping is more helpful as a starter tool rather than a full replacement for traditional scraping methods.

Tools used

- VSC: For all Python scripting and automation.
- jupyter notebook: To validate CSV files, view dataframes, and inspect problem columns like turnaround time and engine status.
- github: Used to version control and publish my project summary.
- scrapegraphai: Used for AI-assisted scraping.
- python libraries:
  - `beautifulsoup4`
  - `pandas`
  - `requests`
  - `csv`

strategy for development

My approach was to divide the scraping into three distinct extractor functions for Block 1, Block 4, and Block 5. Then I looped through each table on the Wikipedia page and applied the appropriate extractor based on the table caption. I structured the data into rows, created a master dataframe, and exported that to CSV.

Once I had the CSV, I developed 18 separate Python scripts both standard and AI-labeled versions that filtered or summarized different subsets of the Falcon 9 data.

challenges faced

- special characters: Unicode issues caused garbled text in launch sites and engine statuses. I had to manually sanitize or re-encode the data in multiple places.
- turnaround time parsing: The values were text-based 45 days or missing —, which required extra parsing logic to extract numerical values or fill in zero where appropriate.
- ai scraping limitations: Even though the prompts were detailed, ScrapeGraphAI missed a lot of entries. It was more useful for quick exploration but not for complete data scraping

time spent

This assignment took several hours in total between debugging the web scraping issues, handling formatting problems, cleaning up the turnaround times, testing the AI scraper, writing the scripts, and generating the markdown summary. The biggest time sink was making sure the scraped data was clean and consistent across both methods.

---

Overall, this project was a cool crash course in real worldscraping, AI tooling, and data pipeline debugging. It was messy and very frustrating but I learned a lot. IN PANDAS WE TRUST.
