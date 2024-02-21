# Basic Legislation Tracker

## Requirements
- sqlite
- pandas
- feedparser
- yagmail

## Setup process
1. Create database
2. Create bill table (id, chamber, number, year, url, rss, lastBuildDate)
3. create action table (title, description, pubDate)
   1. bills 1-to-n actions
4. For each bill, grab all actions from RSS
5. Set up daily cron
   1. https://www.geeksforgeeks.org/schedule-a-python-script-on-pythonanywhere/
   2. https://cron-job.org/en/
   
## Ongoing process
1. Import bill and actions tables
2. For each bill, check RSS for updates
3. If updated
   1. Update bill lastBuildDate
   2. Grab latest item
   3. Parse latest item
   4. Add latest item to actions
4. Validate changes
5. Log changes
6. Save dataframes to file
7. Email notification of changes with files attached

## Data
URL format: 
https://www.capitol.hawaii.gov/session/measure_indiv.aspx?billtype=HB&billnumber=2090&year=2024

RSS format:
https://www.capitol.hawaii.gov/sessions/session2024/rss/HB2090.xml

## References
- https://feedparser.readthedocs.io/en/latest/
- https://docs.python.org/3/library/sqlite3.html#sqlite3-tutorial
- https://docs.python.org/3/library/email.html#module-email
- https://realpython.com/python-send-email/
- https://docs.python.org/3/library/webbrowser.html