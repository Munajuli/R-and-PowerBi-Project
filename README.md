Aim: To analyze the performance of Hollywood movies 

![alt text](https://github.com/Munajuli/R-and-PowerBi-Project/blob/19350846ff48b1a826a258d92ab8899db2f5a542/R%20Dashboard.PNG)

Data: Title, genre, studio, profitability and ratings for movies released 2007-2012. Source: InformationIsBeautiful.net 

Download data from this link: 
https://public.tableau.com/app/sample-data/HollywoodsMostProfitableStories.csv

During the R analaysis, I encountered and error when I ran the code #colSums(is.na(df)) while checking for missing values, after a couple of trials, I found another code #df <- df[rowSums(is.na(df)) == 0, ] which when I ran it, worked perfectly.

Knowing that an outlier can distort the normal distribution of a datatset, I have removed the outliers before checking for scatterplots

Checking for scatterplots using the Bivarient Analysis, was basically to check the existing relationship between the variables (X and Y) before plotting my Bar chart

For the dashboard, I have used the client's specification on what to do;

While creating my dashboard, I realised that there was a Null value in my dataset which was the clean dataset. I went to the original dataset to check it missing there and to know what next to do, I realised that the Null value was also in the original dataset but because it was just 1 Null value I filtered it out when creating my dashboard.

For the dashboard, the company would like you to use their brand colors which are blue, green and brown. You can use light or dark shades of each color. For example, light blue and dark blue are acceptable. You can combine these colors any way that you like. For example, you can use only blue and green if you want to. 

In your power BI Dashboard, the client would like to see: 

The average Rotten Tomatoes ratings of each genre
The number of movies produced per year 
The audience score for each film  
The profitability per studio 
The worldwide gross per genre 

And I have also created a 6th visual called Count of rotten tomatoes by Year





