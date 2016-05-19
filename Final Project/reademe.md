Summary - The objective of the dataset is to show gender equity represented by gender distribution of medals between men
 and women for each country. 
 
 Design - I made many graphs but ended up on these ones because I believe it showed the story 
 that I was telling the best. I wanted to make it interactive by time when possible to show visually how the gender 
 distribution has changed over time and how it still has evolvled to being an equal distribution amoung the majority of countries. 
 
 Previous Versions - ALL PREVIOUS VERSIONS ARE ON GIST, I DON'T HAVE THEM HERE. PLEASE GO TO 
 https://gist.github.com/dougomania/b3755f6fd3dccfe1546eed18d792d3e1

Feedback - 

Feedback 1: 

While it seems like you've done a significant amount of work, it is unclear the main take away is.

Assuming the design is completely intentional, the excessive scrolling needed to view the entirety of the 
visualization really detracts from its effectiveness. It is busy in nature, and in it's current form cannot 
be easily viewed nor understood.

It is hard to understand what the colors on the bubble graphs mean without a legend, also not sure if this is 
intentional. I feel that the bubble graphs can be combined into one bubble graph with a dropdown or buttons to
 select for the countries.

I would encourage a simplification or reduction of information presented, so your main point is apparent. Your 
visualization seems exploratory with some explanations/conclusions but from the visualizations themselves it's 
difficult to come to the same conclusions in the way it is currently presented.

It is also probably necessary to give a little more background on the dataset in the beginning. I would resize 
some of the graphs so they can fit side-by-side, closer to being a single page. 

Keep up the great work!

P.S. I think you should have a visible gap between 1936-1948 in the total medal count graph as the data is missing due to historical events (and maybe annotate it as such).﻿

Feedback 2

the number of cool charts is impressive ! here are a few remarks:

1/ I am missing some comments about the very first chart (what you call the buttons - misnamed ?): naively, 
I would expect that the amount of medals increases over the years since at each Olympic Games some sports get 
accepted while very few others get removed. I think it would be very enlightening if you could give a few examples (e.g. polo, baseball, ...)

2/ The same comment applies to the second and third charts: What strikes is the difference in amount of medals 
per gender. I would expect that you give examples of some sports that were traditionally reserved to men but 
were made accessible to women, and some sports that are still today only played by men. Your charts spark the 
curiosity of the reader (well done!) but I felt frustrated because I had to search for the information on my own.

3/ "Bubble graphs of women in sport" I am not pleased by such a title: I do not think it is a good idea to name 
the type of chart you are using in a title.

4/ wrt the first bubble graph: In the text you talk about the percentage of medal won for men and women, but the 
label on the y-axis mentions only the proportion of women. It is a bit confusing. In fact, I found this chart hard
 to understand: What is the area of the circles proportional to ? after some thoughts it must be the total number 
 of medals for a given country, right ? this chart is amazing but the text does not render justice to it;

5/ still on this chart: The tooltip gives a less accurate number for W% though I would expect the reader would use 
tooltips in particular to get more accuracy (instead of painfully having to guess the accurate numbers by projecting 
the center of the radius on the y-axis). 6/ "usually wom more" typo 7/ graphs spilt the above" typo 8/ for the graph 
splitting: it seems that you did not use the same scale for the radii for all charts, did you ?

regards, Laurent﻿

Feedback 3 You have a lot of information packed into one visualization (maybe too much information with too little 
explanation?). So, I will have to get back to you about your specific questions once I take it all in.

One details point that I will make is that your charts aren't centering (which is visually distracting) as you are 
using absolute positioning for your 'svg's. If you use relative positioning then they will center due to the 'body' CSS.

To do this, there are three changes that you have to make: 1. Give each of your chart divs a view height style (which 
is how much of the screen height you want them to take up). Given that you have a fixed nav bar (which is a nice touch),
 you would want each chart to take up about 70% of the screen:


then: 2. Create your 'svg's using percentage height and width (not absolute values):

var svg = dimple.newSvg("#MedalAndPercent", "100%", "80%"); then: 3. Position the legends using negative percentages for the top postion:

myChart.addLegend("-15%", 10, 100, 20, "left"); that will give you a relative top-x positioning within that svg.

For the control, the 'nav' CSS determines the size of that element, so you approach it slightly differently: 
1. The 'vh' is relative to the 'nav' CSS instructions:
        <div  id="control" style="height: 95vh"></div>


but 2. The svg is still relative to the overall page, so give it a height relative to the page, say 10%:

var svgi = dimple.newSvg("#control", "100%", "10%"); Finally changing your 'body' CSS to:
        body {
            margin: 0 auto;
        }


will center everything.

Resources - list any sources you consulted to create your visualization I used Udacity forums the most as 
well as the dimple examples http://dimplejs.org/advanced_examples_viewer.html?id=advanced_storyboard_control http://dimplejs.org/advanced_examples_viewer.html?id=advanced_interactive_legends
