# Task

To try resolve real life problems from [Upwork](https://www.upwork.com/freelance-jobs/apply/Data-Scraping-Extract-1164-Records-from-Website-into-Excel_~021889513767713286399/):

![image](https://github.com/user-attachments/assets/a44f284d-f97a-4fbf-86e5-4b8f19c87940)

# Tools

- Web Scraper Chrome Extension: (https://chromewebstore.google.com/detail/web-scraper-free-web-scra/jnhgnonknehpejjnehehllkliplmbmhn?hl=en)
- Excel/PowerQuery

# Steps
## Scraping data

1. Search term was "*". Day later there were 1165/1164 results.
   - in Excel there were 1163 rows?
3. The most time consuming was:
   - Learning how to do pagination part - sure, I do not remember it next time.
   - Getting one company's data into one row.
![image](https://github.com/user-attachments/assets/d9deb2b5-7432-422b-9376-2fab8ba94340)
   - Figuring out that actually quite a few companies had website and it wasn't scraping mistake.
   - Started to cleaning data in Excel and then realized there were <em>company/director<em> vs <em>attrorney/company confusion<em>. So, it was much easier to conifigure scraping part than do it in Excel.
  
   - At first: ![Kuvatõmmis 2025-02-14 093035](https://github.com/user-attachments/assets/29ebe8ba-a1da-45b2-9349-68de7bc8052c)
   - Later

## Cleaning Data





1. ID/webscraper-order
   Duplicated the column webscraper-order, extracted '1739479965-'and changed type to numbers. Id column helps to handle changing/updating in the future.
   
![image](https://github.com/user-attachments/assets/23ff026e-a6f3-4038-959d-ebede03c1085)



2. Email in lowercase
   
   ![image](https://github.com/user-attachments/assets/8bc7dc79-3096-497a-a12f-277816b9763b)

3. Trimming all the string values.
4. Directors column
  - all names to begin with capital letter
5. Address
Replacing with other columns value:
- first replace blank with something, and then replace this in formula bar each [column]  e.g. = Table.ReplaceValue(#"Sorditud read","",each [directors],Replacer.ReplaceValue,
