# Victims of Auschwitz — Read Me

***TO VIEW THE PROJECT, [GO HERE.](https://xanderdavies.github.io/victims-of-auschwitz/website/)***
***TO ACCESS THE DOCUMENTATION, [GO HERE.](https://github.com/xanderdavies/victims-of-auschwitz)***

Between 1941 and 1945, the Nazis and their collaborators murdered six million Jews. Despite the Central Database of Shoah Victims’ Names containing the names and basic biographical data for almost 4.8 million of these victims, very little graphical analysis has been performed on the data. For this project, I constructed seven animated maps to visually represent a portion of the total data, namely the lives of Auschwitz victims. The maps contain hundreds of thousands of blue dots against a backdrop of the map of Europe. Each dot is the life of a specific Jew murdered in Auschwitz. A dot appears in the year of its corresponding victim’s birth and in the city of their pre-war location, and disappears in the year of the victim’s death. To handle overlapping dots (corresponding to victims with the same pre-war location), dots with the same coordinates were organized in concentric circles surrounding their location. One map (displayed on the website’s homepage) shows all of the data. Six maps break down the data by year of death, showing, for example, only victims who died in Auschwitz in 1942. 

The files attached can be broken down into four categories:
1. The *html*, *css*, and *gif* files stored in */website*. These are used in the website, with index.html, 1940.html, 1941.html, 1942.html, 1943.html, 1944.html, and 1945.html being very simple pages styled by styles.css. Gif files correspond to each page, assigned in the styles.css page as the corresponding page's background image. Each page also has a secondary background of a loading gif, to serve as a loading icon before the background image comes in and convers it up.
2. *YadScrape.ipynb*, *chromedriver*, and *scraped*. The first two files are used to scrape data from yvng.yadvashem.org. The chromedriver is used in tandem with the selenium python extension. The third is a folder with scraped data stored in a csv, as well as a cleaned folder with only non-null entries.
3. *qgis-data-and-background*. This folder contains all necessary files to implement the mapping in 1940, 1941, 1942, 1943, 1944, and 1945. Note that it does not include the merging of these years, which must be implemented using the merge layers in the vector menu.
4. *DESIGN.md* and *README.md,* which serve as the projects documentation.

As outlined in DESIGN.md, implementing the project entails three steps. First, collecting data, second cleaning the data, and third representing the data. 

### Collecting
I used selenium (https://selenium-python.readthedocs.io) to filter results and click through the pages, lifting data on pre-war location and birth year. The code is fairly straightforward, with the only complexities closing pop-up advertisement and looping over the total number of pages lifted from the page itself. Of course, I have already done the scraping, and the information can be found in the *scraped* folder.

### Cleaning
The first step in the data cleaning, and perhaps the most regrettable step, was deleting every data point that did not contain both a location and a date of birth. Future iterations of this project could instead assign the data points values based on known statistics on victims. Next, the location names must be geocoded to xy values. After playing around with quite a few geocoders (including the Google Maps API, and several built in QGIS functions), I settled on the ArcGIS Online Geocoding Service. I thank Harvard's Center for Geographic Analysis for their financial assistance. Again, I have already done the process, so geocoded data can be found as shape files and .dbf files in the *qgis-data-and-background* folder.

### Representing
Shape files were represented with point displacement in QGIS to display many points with the same coordinates. Animations were created with start times based on birth year and end times based on death year (a new column created in the field calculator). See documentation for TimeManager (https://anitagraser.com/projects/time-manager/) for more information. To create the gif used on the home page, the files were merged to create an animation with all of the data, as found in the merge layers property in the processing toolbar. The animations stored in Time Manager were exported as .png files to Photoshop and converted into .gif files with specified time increments. A quick website was then setup to display the results.

-- Alexander Davies

Never Forget • לא נשכח


