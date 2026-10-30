# Analysis of OpenAI partnership dataset — 10/2026 

## Data

This analysis used the following data:

Announcements made by OpenAI [here]([url](https://openai.com/news/company-announcements/))
Announcments made in [SEC/Edgar]([url](https://www.sec.gov/edgar/search/)) filings 
Announcements in newswire services such as [PR Newswire]([url](https://www.prnewswire.com/))

These websites were scraped via ClaudeAI which can be seen in the chat file in the Github repository named: Claude_Data_Collect.pdf

The scrape culminated in the xlsx file attached to this repository: Open_AI_Partners.xlsx - important tabs below

- First Sweep - The first major and braod scrape done by ClaudeAI
- Edge Cases - Rows of data that ClaudeAI was not able to definitively say counted as a partnership or not
- Filtered Data - The filtered version of First Sweep, following a strict definition of partnership
- Sheet1 - The human verified data from Filtered Data, rows that were manually verified to be considered a partnership
    - Within Sheet1 the following Columns were used:
 
    - Date of Partnership Announcment
    - Partner Name
    - Partnership Sector

## Methodology

##### Part 1: Gathering the Data

For my dataset, I analyzed the different partnerships that OpenAI has announced. To identify partnerships, I used ClaudeAI to scrape the OpenAI news/company announcements page found here. To make Claude’s scrape as accurate and exhaustive as possible, I fed it links to articles where OpenAI had previously announced the type of partnerships I was looking for, as well as OpenAI’s own defined “partner network.” I also had it search SEC EDGAR filings and press-release wire services such as PR Newswire for any language reflecting a partnership with OpenAI. Once I had an exhaustive yet targeted list of potential OpenAI partners, I narrowed my definition of a partnership and had Claude filter the data strictly sticking to this definition. The definition is as follows:

A partnership in this instance is a specific arrangement between OpenAI and a named outside organization, acknowledged by OpenAI, in which at least one side commits something of value to the other beyond an ordinary purchase: money or investment, compute or infrastructure, content or data rights, technology or IP rights, product access on negotiated terms, or dedicated staff working toward a defined joint goal.

I instructed it to separate the results into new tabs within the spreadsheet so I could see exactly how each potential partner was sorted, and to not delete anything already created. The tab named “First Sweep” is the unfiltered results from my initial results. I then had it copy any rows from the First Sweep to “Filtered Data” if they fit my definition of a partnership, which ultimately became my dataset for this analysis. For entries where Claude could not make a definitive judgment on whether they fit my definition of partnership, rows were placed into an “Edge Cases” tab, rather than forcing them to be in one tab or another. Any entry from the first sweep that no longer qualified as a partnership was highlighted in red in the “First Sweep” tab, and then placed in its own “Non-Partnership” tab. 
Then, finally, I manually looked at all the results that landed in the “Filtered Data tab” and verified myself whether they fit my description, and then added them into their respective sector/industry.



##### Part 2: Analyzing the Data

To analyze the data I used pandas and matplotlib.pyplot. I extracted the year from the Date of Partnership from Sheet1 (the confirmed partnerships), and kept only the 3 columns I needed: the year, the partner's name, and the partner's sector. I then grouped the partnerships by year and sector and counted how many fell into each combination. 

Using those countws, I built a stacked bar chart. Each bar represents a year, and the hight of teh bar shows the total number of partnerships announced that year. Each color represents a different sector, such as technology, journalism, or government. There are no bars for 2020 and 2021 because no partnerships in my dataset were announced those years. 

I plan to build on this data by going through the Edge Cases sheet to further add more data to my analysis, and add tooltips so users can hover over the table and read the names of partnerships that fall within each bucket.


## Outputs

The output table can be found at the bottom of analysis.ipynb

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- pandas and matplotlib libraries
  
## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact me, Delwin Portillo at d.orellana33@journalism.cuny.edu
