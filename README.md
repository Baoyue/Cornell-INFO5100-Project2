# Cornell INFO5100 Data Visualization Project2: Average Household Income in US from 2008-2015

## Overview

Nowadays, it seems that people are making more money than past. Are we making more money
as time going by? Where do we spend our money? How are we doing compared with people in
other states? In this project, we aim to use data visualization to convey clear and intuitive results
we found about the topics above. We firstly implemented a choropleth form visualization
offering the general comparison and distribution across the states. Then we provided access to
detailed information view as well as comparison among states to present more detailed data
feature. With our project, users could gain a general idea about how the average household
income of their state is going in recent years and the performance compared with others.
Additionally, they will also notice some interesting aspects as browsing the information about
where their money has been spent on.

## Data Description

In our project, most of the data comes from the SimplyMap database, which offers various
datasets for different aspects in our life. Each dataset is for one variable in the unit of one year,
and could be downloaded as a CSV file.

To achieve better presentation of our idea, we chose the datasets for 2008-2015 of the following
variables: Household average income, expenditure on food, expenditure on health care,
expenditure on housing and expenditure on transportation. Besides the income variable, which is
main factor in the project, the selection of the other four main categories are made based on full
consideration towards our topic, as these are the four major parts in ordinary life and could
reveal how the income is actually influencing our life. Each CSV file we downloaded contains
the amount of money on corresponding item, the state name, the state fips and the ranking
(discarded in our project). We combined all data into one csv file named money.csv for easier
data use in codes, through simply copy and paste. The data file money.csv is used in producing
the visualization of choropleth, line charts and bar charts.

For the sunburst, we trimmed all datasets and created a json file for each state. The data in the
json file is formed into parent node and child node, which is used for sunburst layers. For each
node, there is “name”, “description”, “size” or “child” parameters inside. All json files are stored
in data file, and called when state detail request is sent from html page.

Additionally, we also used the shape file us.json for the map showing, no change is made on this part.

## Data Mapping

### Choropleth Map with Time Slider
The first part in our project is the choropleth map for United States in the unit of state, using
filled color to reflect value and map location to reflect each state. We used the albersUsa
projection to produce the composition of all states at one place, with the scale factor 1000 and
translating it to the top left part of our page for clear view. The color is assigned to each state
based on the amount of money on corresponding variable following the multi-hue color scale for
better difference representation. The time slider is realized with the range type of input, designed
with min value of 2008 and max value of 2015. The sliding of the thumb button directly change
the data displayed on the map, i.e. showing the distribution in the corresponding year. In addition,
we are providing five buttons (Income, Food, Health, Housing, Transportation) to enable data
visualization on different categories. For detailed data, e.g. the specific amount of money that
people in California state spending on food in 2011, is shown through the user interaction of
hovering the mouse on a specific state. This information is shown in the tip box, appearing next
to the state.

In our project, we enable two display modes to show data in detail. Users can either click on
“one state details” to view a certain state’s line graph and sunburst pie chart, or select “two states
comparison” to view the comparison between them in the form of bar charts and line graphs.

### Line Graphs
The line graph focuses on showing the trend of income and expenditure through years from 2008
to 2015 for specific states. This will shown up both in one-state mode and two-state comparison
mode. The x axis is showing the year and y axis is showing the amount of money spent. For clear
definition and perception, we keep the same unit on the axis and apply the irregular distribution
to y axis for clearer view of the trend. Each line graph has five lines corresponding to the average
household income, food expenditure, housing expenditure, healthcare expenditure and
transportation expenditure, aimed to show reveal the trend in each aspect. Meanwhile, we made
the feature points at each data points, enabling using the hover interaction to see detailed number.
The legend for the line graphs are circle-shaped clickable buttons, letting users set specific lines
invisible to explore the correlation between some certain aspects. In the two states comparison
mode, lines for the same category can be highlighted synchronized for better comparison.

### Sunburst Pie Chart

The sunburst graph presents the expense in different life aspects and how much it takes up in
total expense. Clicking on outer part can trigger zoom in function and see more detailed expense
on that aspect. Click on central circle can trigger zoom out. Generally, the sunburst is divided 
into food, healthcare, housing and transportation part. This four parts basically sum up all normal
daily expense, which is also the major outlay. The breadcrumb on top of the sunburst shows
which part the mouse is hovering on and correspondent data value. The amount shows up only
when the user hovers the most outer layer.

### Bar Chart of Two States Comparison
The bar chart part is used in the two-state comparison mode. After the user selects two states in
the map, the bar chart shows the comparison of expense of the five aspects. The length of base
bar is fixed. And the length of sub bars is calculated using the equation:

_length of the base bar * amount of one state / total amount of the selected two states_

Therefore, if two states have same expense on food, both of the bars will be 50% length of the
base bar. We appended a 50 to 50 line in the center so the user can see which state has more
expense if the difference is subtle. We also displays the national rank of the two states at the end
of the base bars so the user can gain a clear understanding of the states are at which level
nationwide.

## Our Story

We earn money and spend money, but it is not often for us to exam where our money goes and
how much it counts. In this century, credit card is gradually replacing cash in every aspect. This
brings us convenience, as well as causing a lack of understanding of how much we actually
spend. Our group implemented this project to help people get an idea of the living expense in
each state, and provide a way to make comparison between states. The graphs presents datasets
in different aspects of daily expense as a reference for the users. Assume there is a guy called
James, and he wants to know something about his daily expense. He can look into the sunburst
graph, see whether his family is spending too much or too less comparing to average level. Say if
he has a much bigger amount of spending on “food away from home” part, he may consider an
adjustment of lifestyle and start cooking at home. Another situation is that James want to move
to another state, but has no idea whether he can afford the moving expense. He can switch into
“two states” mode, and click the two he wants to compare. The bar chart and line graph will
show how the same expense vary and the expense changing tendency in two states.

## Reference

Our realization for the sunburst referenced to the following resources:

1. [https://bl.ocks.org/mbostock/5944371](https://bl.ocks.org/mbostock/5944371)
2. [http://bl.ocks.org/kerryrodden/7090426](http://bl.ocks.org/kerryrodden/7090426)
3. [http://bl.ocks.org/mbostock/4348373](http://bl.ocks.org/mbostock/4348373)
4. [http://sharonhoward.org/ob/punzoomsunbursttt.html](http://sharonhoward.org/ob/punzoomsunbursttt.html)
5. [http://dhistory.org/trove/zone-explorer/](http://dhistory.org/trove/zone-explorer/)
