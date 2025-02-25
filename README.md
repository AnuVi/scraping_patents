# Task

Tried to resolve real life problems from [Upwork](https://www.upwork.com/freelance-jobs/apply/Data-Scraping-Extract-1164-Records-from-Website-into-Excel_~021889513767713286399/):

![image](https://github.com/user-attachments/assets/a44f284d-f97a-4fbf-86e5-4b8f19c87940)

# Source
https://www.ttipattorney.gov.au/for-clients/how-to-engage-an-attorney/find-an-ip-attorney-or-firm#als_iptags=Patents&als_e=0

# Cleaned/Raw file
Phone/email columns are deleted and only first 101 rows.
https://1drv.ms/x/c/315a2e7b2c65925e/EedJadjmkrhLkzuZev4rJ94BFFbAgx3IP6GFFLdFPKpZPA?e=1Hd2xi


# Tools

- Web Scraper Chrome Extension: (https://chromewebstore.google.com/detail/web-scraper-free-web-scra/jnhgnonknehpejjnehehllkliplmbmhn?hl=en)
- Excel/Power Query

# Lessons
1. PowerQuery
   - To see content of the previous steps -> look at the command line.
   - If you look older steps keep in mind that it doesn't show later changes - just to avoid WTF! I just did it where it is now moments.
2. Scraping is a process. Some things are easier to fix with scraping (to get the correct data to correct column) than with Excel/PowerQuery.
3. And some things are still pure handwork in Excel, at least in my case it helps to keep the control.



# Steps
## Scraping data

1. Search term was "*".
   - In Excel there were 1163 rows?
3. The most time consuming was:
   - Learning how to do pagination part - sure, I do not remember it next time.
   - Getting one company's data into one row.
![image](https://github.com/user-attachments/assets/d9deb2b5-7432-422b-9376-2fab8ba94340)
   - Figuring out that actually quite a few companies had website and it wasn't scraping mistake.
   - Started to cleaning data in Excel and then realized there were <em>company/director<em> vs <em>attrorney/company confusion<em>. So, it was much easier to conifigure scraping part than do it in Excel.
  

## Cleaning Data

1. Adding RowID. Duplicated the column webscraper-order, extracted '-'and changed type to numbers. RowID column helps to handle changing/updating in the future.
   
![image](https://github.com/user-attachments/assets/194a7b9b-c00f-48d0-8e89-ae88b10c596b)

2. Company's name. All the PTY LTD and names in capital letters to start with capital leter.
![image](https://github.com/user-attachments/assets/6c1ffcd8-fbe1-46a1-96c7-db578a9a0e1d)

3. Phone grouping by 4.
   ![image](https://github.com/user-attachments/assets/e0f93a40-adee-44d2-a5c6-74b5f05cb093)


2. Emails to lowercase.

![image](https://github.com/user-attachments/assets/8bc7dc79-3096-497a-a12f-277816b9763b)

4. Directors column
  - all names to begin with capital letter
  - replacing "and" -> ", "
  - replacing ";" -> ", "

![image](https://github.com/user-attachments/assets/d911d34b-8a15-4be5-9e55-fe266d0a70b0)

5. Address/Company_works
Replacing with other columns value:
- first replace blank with something, and then replace this in formula bar each [column]  e.g. = Table.ReplaceValue(#"Sorted rows","",each [directors],Replacer.ReplaceValue,
- replacing , with _blank_
- separating country
- comparing two strings and replacing them =IF(EXACT([@address];[@[company_works]]);" ";[@[company_works]])

Before:
![image](https://github.com/user-attachments/assets/5fee69e3-dda5-4439-a9ee-c28463fc1047)
After:
![image](https://github.com/user-attachments/assets/8dcdc955-ee72-4e0b-8d31-1f43a0cf471c)

## Further steps can be:
- Replacing all the <em>blank</em> and <em>null</em> values with TBA or N/A.
- According to Client's overview with Address/Phone column - maybe some extra work e.g 4 or 04.
- Make two separated tables: Comapanies and Attorneys. And connecting data based on these.
- Some graphics about main trends.
