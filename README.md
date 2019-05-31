# Institute of Economic Studies
# Data Processing in Python
## Prague Marathon Results
#### David Koubek, Jiri Zelenka
31 May 2019

### Introduction
We are scraping the RUNCZECH website ([RunCzech.com](https://www.runczech.com/))for results of marathon runners. The scraping essentially consist of retrieving the table of results (times of runners etc.) which is spread out across various pages, and across various years of marathon events. The data analysis delves into how the distributions of finishing times of runners varies across past 25 years. We expected the finishing times to be improving over past decades which turned out to be true. Different visualisation techniques were suitable here for the cross-section data that also contains gender, nationalities, and age category.

### Scraping procedure
 - use dynamic JavaScript (JS) scraping methods to scrape the website's content that is loaded from their servers dynamically
 - use BeautifulSoup package among others, for creation of a soup variable containing the required html code in a clean format
 - in "Results" menu (https://www.runczech.com/srv/www/qf/en/ramjet/results/list) of the website, scrape all marathon weekend links on all 7 pages and save their urls. It should be 24 links for 24 years of marathon results (1995-2011, 2013-2019). 2012 is for some reason missing from the website and hence can't be acquired. The links look e.g. like https://www.runczech.com/srv/www/qf/en/ramjet/resultsEventDetail?eventId=21429. The links are found in "a" HTML elements using soup.findAll('a',{'class':'indexList_link'})
 - for each of the 24 links (for each marathon year), scrape the hundreds of pages of table rows and save the data. The table of results for a marathon is structured in "tr" HTML rows which we save to a dataframe
 
### Contribution
The contribution of this topic is in further interesting analyses performed than provided by the RUNCZECH website. Getting the data from the website is not very simple without scraping techniques, as they allow just 15 rows of results displayed on a page, and more importantly there is no option of downloading the whole dataset in any way or form, e.g. CSV. So scraping is the only option here. Since the website uses scripts to load the content of the pages (it pulls JSON data from their servers), the scraping needs to use JS methods. Static scraping doesn't get the main content of the website needed for analysis.