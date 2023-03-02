# 310D_Project1
Data Curation and Analysis Project Repository

The goal of this project is to scrape Wikipedia and create a data set and then analyze that set. The page scraped is https://en.wikipedia.org/wiki/Lists_of_American_universities_and_colleges and the pages linked on it that refer to states and territories of the USA. The data scraped is a table that records colleges and some of their attributes. The criteria for the tables scraped is: describes current institutions (graduate or undergraduate) that are in state and accredited. To scrape the data, Wikipedia API (https://pypi.org/project/Wikipedia-API/) and Beautiful Soup (https://www.crummy.com/software/BeautifulSoup/bs4/doc/) was used. For analysis, Pandas (https://pandas.pydata.org/docs/) and NumPy (https://numpy.org/doc/) were used.


Licenses:

MIT License

Copyright (c) 2023 aarora1689

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Wikipedia's License for the Source Data:

CC-BY-SA

Attribution
To re-distribute a text page in any form, provide credit to the authors either by including a) a hyperlink (where possible) or URL to the page or pages you are re-using, b) a hyperlink (where possible) or URL to an alternative, stable online copy which is freely accessible, which conforms with the license, and which provides credit to the authors in a manner equivalent to the credit given on this website, or c) a list of all authors. (Any list of authors may be filtered to exclude very small or irrelevant contributions.) This applies to text developed by the Wikipedia community. Text from external sources may attach additional attribution requirements to the work, which should be indicated on an article's face or on its talk page. For example, a page may have a banner or other notation indicating that some or all of its content was originally published somewhere else. Where such notations are visible in the page itself, they should generally be preserved by re-users.
Copyleft/Share Alike
If you make modifications or additions to the page you re-use, you must license them under the Creative Commons Attribution-Share-Alike License 3.0 or later.
Indicate changes
If you make modifications or additions, you must indicate in a reasonable fashion that the original work has been modified. If you are re-using the page in a wiki, for example, indicating this in the page history is sufficient.
Licensing notice
Each copy or modified version that you distribute must include a licensing notice stating that the work is released under CC-BY-SA and either a) a hyperlink or URL to the text of the license or b) a copy of the license. For this purpose, a suitable URL is: http://creativecommons.org/licenses/by-sa/3.0/
For further information, please refer to the legal code of the CC-BY-SA License.


Data Dictionary:

"column_a": type=int, An index that follows a sequential order for each data point.
"index": type=int, An index that does not follow a sequential order. The index skips over numbers, showing the number of rows that have been removed.
"institution": type=str, Institution name. Ex: "University of Georgia".
"state": type=str, The state the institution is located in. Ex: "Georgia".
"location": type=str, The location within the state where the institution is located. Ex: "Atlanta".
"type": type=str, The type of the institution. Ex: "Law School".
"enrollment": type=int, The number of students enrolled in the institution. Beware, as not all these numbers come form the same year, due to current data not being available for all institutions. Most data comes from 2019-2022. Ex: 2384.
"accreditation": type=str, The name of the accreditor of the institution. Ex: "HLC".
"public_private": type=str, The public/private status of the institution. "Public" and "Private" are not the only data stored here. Ex: "Private not for profit".
"endowment": type=float, The endowment received by the institution. Ex: 34000000.
"athletics": type=str, Information about the athletics of the institution. Ex: "NCAA Division I".
"founded": type=int, When the institution was founded. Ex: 1944.
"closed": type=int, When the institution was closed. Ex: 2022.
"control": type=str, Which organizations control the institution. Ex: "Air Force".


Data Issues:

There is an oversimplification of some data columns, like "enrollment". In the case of enrollment, this is because not all institutions have the most up to date data available (some had data from fall 2020, some from spring 2021, etc.). Additionally, there was no enrollment data for the past (meaning the data could not be standardized to one time period). However, most enrollment data comes from the time period of 2019-2022. While COVID-19 may have caused enrollment numbers to change wildly during these years, most of this data can be considered recent.

Some columns have values that can be considered the same, yet are different (oftentimes because one value provides a little more information than the other one). For example, in the "public_private" column there is both "private" and "private not for profit" as data points. While these are both private, the second value was left because it provided more information.

This data is biased towards well documented institutions that are part of a system of institutions. This means that oftentimes, institutions in smaller states/territories or that are independent of belonging to any university system were left out because they were not included in a table. Ex: Guam's University of Guam is not included in the data because it was not in a table (only tables were extracted from Wikipedia). University of Guam was likely not in a table because there are only two universities in Guam, and it was easier for the author to simply write the university names rather than make a whole table. Bulleted lists of universities were fairly common in the pages this dataset was extracted from, meaning a lot of data was left out.


Data Analysis:

A lot of universities seem to be concentrated in the Northeast and on the East Coast of the Untied States. The exception to this is California, which ranked 3rd in a comparison of the number of institutions each state has.

Associates colleges are the most common type of college in the United States, closely followed by Baccalaureate colleges. There are also a surprisingly high number of special focus institutions (this type of institution was the 4th most common), only a couple fewer than Master's institutions.

Most institutions are accredited by either SACS of HLC, with a few accredited by smaller organizations. There seem to be 20-25 institutions that are not accredited, however, this may be due to error in data processing.
