# Sustainable Scrapers
@author: David Eads, NPR Visuals

[slides](https://shoutkey.com/from)
[blog post](http://blog.apps.npr.org/2016/06/17/scraping-tips.html)
[github](https://github.com/nprapps/armslist-scraper)

## data journalism
- small budget, quick deadlines
- have to think about when it's worth it
- will it help tell the story
- widely applicable skills: find lots of info, summarize and visual to tell the story

## NPR story: availbility of guns in the non regulated private market, online marketplaces
- map of US viewing availability on armslist.com
- how it overlaps small cities, near state borders based on gun law restrictions, near major transit intersections
- ohio and NC are msot trafficed
- states with lots of guns doesn't necessarily translate to online market

## Planning to scrape
### ask first: do i need a scraper?
don't have access to DB, only website, public data not provided
- the good stuff is hard to get
consider ethical ramifications
- read terms of service
- check with legal

### can you scrape?
- console and curl detective
- URL and DOM structures
- HTML formats
- Consistency across pages

### Example: armslist
- no one is tracking this data
- easy URL structure
- HTML is well formatted, so easy to extract and parse
- okay terms of service and okay with legal

## Process
Gathering data
- using curl to check server version and response time
``` curl -I <web address> -w <Response time>````
Modeling data
- Features: title, category, price, location, date posted

## architecture
controller script: scrape various sites, segments by state  
listing scraper: takes URL, makes http request  
- csvkit  
- beautifulsoup4  
- property decorator: getter/setting for the python class  
GNU Parallel: at the command script level  
EC2: use data center close to the site you are scraping
- MaxMind GeoIP
other tools: scrapy, mechanize




