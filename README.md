#1. When do sharks tend to attack the most?

The aim of my project was to analyze data from shark attacks that ocurred between 1900-2018, with the purpose of identifying common seasonal patterns regarding the frequency of these incidents over time. 

Notice: For this purpoose of this project, I was not allowed to eliminate columns.


1. First and foremost, I got rid of all the duplicate rows, as well as those that consisted only of nulls. With that simple move, the number of rows went down by around 75%.
2. Afterwards, I decided to adapt the 'Case Number' column as my new date column, since both had the same information (but in a different format) and interestingly, the 'Case Number' column's format was easier to manipulate and to work with, as it had a more consistent strucutre. So I changed my focus to that one and used the .split() function:
    <sharks[['Real_Year','Month','Day']] = sharks['Date'].str.split('.',2,expand=True)>
    to separate each of those values into new columns.
3. After converting each of them to strings, I used REGEX to eliminate any non-numerical characters. After finishing that cleaning process, I made them go back to the int data dtype.
4. Now, I filtered the incidents for those that took place post-1900, eliminating previious ones which were ambiguous.
5. Referring back to my objective I knew that if I wanted to identify the seasons (which directly affter the shark's environment) these occur at different moments of the year depending on the hemisphere. For this reason, I started by creating two lists, one for countries in the Northern Hemisphere and another for countries in the Southern Hemisphere. These lists contained the names of the countries that corresponded to each hemisphere.
Next, I iterated through the rows of the DataFrame containing information about shark attacks. I added a new column named 'hemisphere' to the DataFrame based on the country mentioned in the 'Country' column. If the country was found in the 'northern_hemisphere_countries' list, the 'hemisphere' value for that row was set to 'northern'. If it was found in the 'southern_hemisphere_countries' list, the 'hemisphere' value was set to 'southern'. For other countries not in either list, the 'hemisphere' value was left blank.
Finally, I applied the 'find_season' function to the DataFrame to create a new column named 'season'. For each row, the function was called with the 'Month' and 'hemisphere' values, and the corresponding season was returned and assigned to the 'season' column
With these steps completed, the DataFrame 'sharks' now contains two new columns, 'hemisphere' and 'season', which represent the hemisphere of the shark attack and the corresponding season, respectively. These columns can be analyzed to identify patterns and trends in shark attacks based on different seasons and hemispheres.


