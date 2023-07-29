# CS 416 : Data Visualization - Narrative Visualization Project
Akriti Sinha ( akritis5@illinois.edu ) - University of Illinois at Urbana-Champaign Summer 2023


```
Github Page for demo: 
Git Repo: 
```



## Data Source

To achieve this, I will be using the World Bank APIs instead of relying on static, embedded and downloadable bulk CSVs from the World Bank website. By accessing data directly through APIs, I can ensure real-time information and seamless integration with my visualization tool. This approach will enhance the accuracy and reliability of my data visualizations while also providing the flexibility to adapt to any future changes in the data source.

World Bank APIs : 

* Developer Information: https://datahelpdesk.worldbank.org/knowledgebase/topics/125589-developer-information
* API Basic Call Structures: https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structures
* Country API: https://datahelpdesk.worldbank.org/knowledgebase/articles/898590-country-api-queries
* Aggregate API query: https://datahelpdesk.worldbank.org/knowledgebase/articles/898614-aggregate-api-queries
* Metadata API query: https://datahelpdesk.worldbank.org/knowledgebase/articles/1886695-metadata-api-queries
etc

World Bank API provides APIs that users can call with specific indicators, and I used `SL.EMP.WORK.ZS` to get % of employment for average wage and salary workers. The API also provides the way to obtain either world information(with country code `WLD`) or each country's unique three-digit country code. (Example: USA for the United States of America, RUS for Russia, CHN for China and further more.)

## How to use World Bank APIs

Following HTTP Get request for the API is to get average wage and salary worker's % of employment(`SL.EMP.WORK.ZS`), worldwide(`WLD`), and between 2000 and 2020.(`date=2000:2020`).

```
http://api.worldbank.org/v2/country/WLD/indicator/SL.EMP.WORK.ZS?format=json&date=2000:2020
```
The response for above will be as follows : 

```
[
    {
        "page":1,
        "pages":1,
        "per_page":50,
        "total":21,
        "sourceid":"2",
        "lastupdated":"2023-07-25"
    }
    [
        {
            "indicator":
            {
                "id":"SL.EMP.WORK.ZS",
                "value":"Wage and salaried workers, total (% of total employment) (modeled ILO estimate)"
            },
            "country":{"id":"1W","value":"World"},
            "countryiso3code":"WLD",
            "date":"2020",
            "value":52.9649980795557,
            "unit":"",
            "obs_status":"",
            "decimal":1
            },
     // more data, skipped
```
Which means that wage and salary workers' percentage in 2020 worldwide was 52.96%.


# Review Criteria 
An essay is required to be submitted through which understanding of the concepts of narrative visualizatio and how they apply has been created.

The essay should contain the following sections.

* <b>Messaging.</b> What is the message you are trying to communicate with the narrative visualization?


>For this visualization assignment, I decided to explore the intriguing differences in the average rate of waged and salaried workers between countries. As part of the visualization, I have also included a feature that enables users to investigate other countries' WDI (World Development Indicators) data related to employment rates.

>The worldwide rate for wage and salary workers has been steadily increasing over the years, surpassing 50%. Common knowledge suggests that in well-developed countries, this rate should rise while the self-employment rate decreases. However, what caught my attention was that some countries, like the US, have astonishingly high rates, exceeding 90%, while this rate hovers around 50% for many other developed western countries.

> Initially, I hypothesized that the rate of waged and salaried workers' indicators in highly developed countries would indeed be higher than those in developing countries. However, when I checked the data for China and Russia, this assumption was proven wrong. I anticipated both countries to have similar rates, around 50%, with China potentially slightly higher than Russia. Surprisingly, Russia's data resembled that of the US, whereas China's rate barely crossed the 50% mark.

> Through this storytelling approach, I aim to stimulate critical thinking and foster a deeper understanding of the complexities surrounding employment rates and how they vary across different countries. And in the end by inviting viewers to explore the data themselves, I hope to initiate insights that shed light on this phenomenon.

* <b>Narrative Structure.</b> Which structure was your narrative visualization designed to follow (Martini glass, interactive slide show or drop-down story)? How does your narrative visualization follow that structure? (All of these structures can include the opportunity to "drill-down" and explore. The difference is where that opportunity happens in the structure.)

>I've used Martini Glass structure, where the message is delivered without allowing user exploration until the end.  It has four scenes showing line charts for different countries(USA, Russia, China), including the world average. In the fifth/last scene, viewers can actively explore specific country data like male, female, or total ratio.

>This interactive design makes it easy for viewers to understand and draw conclusions about employment differences across countries and demographic groups. It empowers them to explore and customize their data analysis actively.

* <b>Visual Structure.</b> What visual structure is used for each scene? How does it ensure the viewer can understand the data and navigate the scene? How does it highlight to urge the viewer to focus on the important parts of the data in each scene? How does it help the viewer transition to other scenes, to understand how the data connects to the data in other scenes?

>The visualization follows a simplified scene navigation in the Martini Glass model, allowing viewers to smoothly move to the next scene also previlige to go one scene previous until they reach the last page. This reduces interruptions caused by multiple navigation buttons and menus.

>Each of the five scenes in the visualization utilizes the same template. The top area of the template provides a clear description of the data displayed to the viewers, followed by detailed questions that I pondered and wished to share with others.

>In the middle of the page, the plotting section (SVG) presents the line chart, while the line chart color information explains the significance of each color used in the chart.


>At the bottom of all five scenes, I included a WDI indicator explanation section. This way, viewers can easily double-check the meaning of the current WDI indicator without having to navigate back to previous pages or click a help button when needed. This feature enhances the user experience and ensures seamless access to relevant information throughout the visualization.



* <b>Scenes.</b> What are the scenes of your narrative visualization? How are the scenes ordered, and why

>The story unfolds in five scenes, starting with the world average data to provide viewers with a benchmark for comparison. The second scene focuses on the US, a highly developed country with a significantly high rate of wage/salaried employment.

>Scenes three and four are particularly striking, featuring two countries ruled by communist parties. China, known for its economic and military power in the 21st century, surprisingly exhibits a wage/salary employment rate at the world average level. On the other hand, the second country, Russia, with its military might, displays a surprisingly high percentage comparable to that of the US.

>I wanted to make the viewer think, "Hmmm, that's interesting. Yeah, now I want to know why?". If you feel the way as I hoped, I can say my narrative visualization completed the mission.

* <b>Annotations.</b> What template was followed for the annotations, and why that template? How are the annotations used to support the messaging? Do the annotations change within a single scene, and if so, how and why

>I added each year's rate value as d3-tooltip on each datapoint's circle, so when a viewer performs mouseover event, tooltip annotation pops up and shows what the rate for that specific year was. d3-tooltip also provides 3-digit country code in the last scene and help the viewer to distinguish between multiple line charts.

>I've tried to add general annotation on the chart, but there weren't significant changes I found for the wage/salary worker's average ratio. If zoomed in, the rate might drop 2~3% on a specific event; however, the overall percentage doesn't get impacted by individual activities. That said, I've decided not to add redundant and useless annotation on the chart.

* <b>Parameters.</b> What are the parameters of the narrative visualization? What are the states of the narrative visualization? How are the parameters used to define the state and each scene?

>Current visualization impementation has a few parameters internally. 

>1) Plotting works differently based on given 3-digit country code. 
>
>2) Gender type for data navigation. D3 code calls different APIs to get separate dataset, and also draw a chart with differet color based on this selection. (orange: total, blue: male, red: female )
>
>3) Based on current scene location, visualization page shows different option. For page 1~4, it doesn't show any option for viewer to nagivate; However the page shows gender radio box and country select box in scene 5.

* <b>Triggers.</b> What are the triggers that connect user actions to changes of state in the narrative visualization? What affordances are provided to the user to communicate to them what options are available to them in the narrative visualization?

>1) Page navigation link: D3 code internally keep track of current scebne location and call different WDI APIs and different function with parameter to draw differet chart. In WorldBank WDI API side, there are three different indicator name depends on "total", "male", and "female", and JSON query in the code also need to be changed.

>2) Radio box: gender radio box in scene 5 directly decide which parmater to use for data query.

>3) country select list: Depends on which country viewer choose in scene 5, it also impacts the behavior of WDI API call, and D3 code either calls world data or each country's data.

# Why my visualization is different than others?

My visualization is based on realtime WorldBank API calling and parse the JSON result. This behavior caused lots of data parsing and data sync issue but also taught me a lot more than I learned from the classes. e.g., how to pass extra function parameter to the callback function which usually takes only `d` or `d`,`i`. 
Also, the visualization page will work well with updated data on WDI Worldbank data change as my code don't use locally loaded CSV.

# Future work

* There is still some display issue on the last page during overlapping the line chart. 
* Also, internal chart drawing functions are flexible enough to take a query period(year) as a parameter, but I didn't have enough time to add it as query parameter, so the date is hardcoded from 2000 to 2017. It would be better with some range/scroller to allow viewers to control of it.
