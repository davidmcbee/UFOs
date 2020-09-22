# UFOs, The Truth is Out There
## Background and Purpose
Dana, a data journalist, is given the opportunity to write about her home town, McMinnville,
Oregon. McMinnville is noted for UFO sightings and has a yearly gathering on the subject. A subject
that Dana is very interested in so she dives in to create an analysis and web site to show that analysis.
Her only source of material is a Java Script file filled with UFO sighting information. This java Script file is available here (https://github.com/davidmcbee/UFOs/blob/master/static/js/data.js)

## Overview of analysis
The data.js file has an array of information on sightings. Each sighting has the date it occurred on, the city, the state, the country,
the shape, the duration and comments. It's a large file and would be unwieldly for a user to sift.
Dana's plan is to display the data as a table on a web page and provide filters so one can filter by date, city, state, country and shape.
Dana's project will consist of a neat looking web page that will consist of this table, it's filters and an article.

### Analysis Steps
The products needed to produce this are:
* The data.js file, available here (https://github.com/davidmcbee/UFOs/blob/master/static/js/data.js)
* The index.html file that will display the data on a web page, available here (https://github.com/davidmcbee/UFOs/blob/master/index.html)
* A style.css file that will help her style the web page, available here (https://github.com/davidmcbee/UFOs/blob/master/static/css/style.css)
* A app.js file, to put it altogether, available here (https://github.com/davidmcbee/UFOs/blob/master/static/js/app.js)

#### The app.js file
The app.js file does the following:
1. It reads in the data file and assigns it to a variable
2. It clears the html table she builds so it is fresh each time.
3. It reads the data in and fills the table she will use.
4. She creates two main functions, the updateFilters function and the filterTable function
5. The updateFilters function:
	* Saves the element that was changed in the filter
	* Saves the value that was entered into the filter
	* Saves the id of the filter that was changed
	* She saves the changed value and deletes the filter(s) that were not changed
	* It then calls the filterTable function
6. The filterTable function:
	* Assigns all the data to the Table variable. In case no filters were used, the entire table will be displayed
	* it goes through each row of the table and for each filter used, it captures the applicable rows that meet that filter criteria
	* It builds the table showing only the filtered data.
additionally, the app.js file assigns a listener to notice when an entry occured in the filters on the web page and provides this to the update Filters function

#### the index.html and style.css files
The index.css file puts the data into a viewable form that was based on a storyboard:
	* It creates a nav bar on top. This allows one to reset the table.
	* It creates a jumbotron. This is the top main area that holds the title and, using the style.css file it displays a picture.
	* It holds a container for the article. This container is split into one section 4 columns wide for the article title and one section 8
	columns wide to hold the actual article.
	* It holds a second container that is also split into two sections. This time into a section that is 3 columns wide. This section holds the filters. The
	filters consist of a label and a input box with a placeholder value so the user can see what should be entered. There is one of these combinations
	for date, city, state, country and shape.
	The second section, which is 9 columns wide which holds the data table. It has column headings for date, city, state, country and shape
	* finally the index.html file holds scripts to read in and use the d3 library, the data.js file and the app.js file
Additionally each section is styled using a combination of styling, some applied directly to the index.html file and some stored in the style.css file. The style.css
file is very useful in that it allows for containerization. This way if Dana wants to change the style of the web page but keep the basic parts she can just change
the style sheet. Also, if she ever builds a second web page, she can re-use the style.css file and now both web pages will have a consistent look.
## Results
The web page looks like this ![](https://github.com/davidmcbee/UFOs/blob/master/static/images/initial_wp.png)

Figure 1

note that all the data is in the table but this figure is cut off so it will fit in this readme appropriately.

#### Filters
using the filter lets start with just looking at date. Notice in the initial look, the placeholder date value is 1/10/201, Lets change that to 1/9/2010. See figure 2
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/date_filter.png)

Figure 2

You can see that there are now 11 entries.

Using the city filter while leaving the date filter as is, we'll filter on Cleveland, See figure 3.
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/city_filter.png)

Figure 3

In figure 3, you can now see only one entry. Cleveland doesn't appear to get many UFOs.

Lets remove the city filter and skip down to the country filter. Here we'll filter on the us. See figure 4.
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/country_filter.png)

Figure 4

In figure 4 you can now see there are 10 entries. Originally there were 11 but one was in Canada (ca) so its not shown here.

Now, leaving the data and country filter in place lets filter down to state. We'll use California (ca). See figure 5.
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/ca_filter.png)

Figure 5

In figure 5 you can now see two entries, both in California. Now for the last filter. lets filter down one more level and pick UFOS that are shaped like triangles.
See figure 6
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/shape_filter.png)

Figure 6

In figure 6 we see the only triangle shaped UFO, in California on 1/9/2010. 

One last image. To reset the table back to the entire table, go back to the beginning. just click the "UFO Sightings text in the top left of the web page. Figure 7.
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/reset.png)

Figure 7

## Summary
The web page works as designed and overall, is pretty good. There is one fairly material drawback to this web page though.

### Drawback
the filters are not forgiving at all to the way a user might enter a filter value. The capitalization and spelling need to be exact. This is not very user friendly.
Looking at figure 8, if el cajon is entered in the city filter it works fine.
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/drawback1.png)


Figure 8

But if were to use correct chaptalization nothing would show up. See figure 9
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/drawback2.png)


Figure 9
To improve this performance code should be written that transforms the entry into lower case. This way it would be consistent with the data, what is needed but allow
some flexibility. I tried to use the loose equality "==" versus strict equality "===" but that doesn't work here. It would work if what was entered was a different data type
but that is not the case. Both the data and the entry are strings.

### Additional recommendations
1. The filter entry blocks are not all aligned due to the different length of text. By adding the code shown here in Figure 10 to the style.css file. the input fields are aligned and look much neater. See figure 11.
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/filter_block_css.png)

Figure 10

![](https://github.com/davidmcbee/UFOs/blob/master/static/images/filter_block_aligned.png)

Figure 11

2. Its not intuitive to know that one can click on the "UFO Sightings to reset the table. The code in figure 12 add text to make this known and is shown in figure 13
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/reset_code.png)

Figure 12
![](https://github.com/davidmcbee/UFOs/blob/master/static/images/reset_image.png)

Figure 13

