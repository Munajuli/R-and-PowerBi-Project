# Source-Code
Data Analytics with R, Data Visualisation with Power Bi
# Project Analysis
Here, i will be guiding you through what i have done in the project, outputs, errors encountered and how i have managed to solve them as well.

This is a stpe by step quide on the codes i ran, outputs and the comments.

#Load data:
df<- read.csv("C:/Users/julie/Downloads/HollywoodsMostProfitableStories.csv")

#Take a look at the data:
View(df)

#Load library:

install.packages("tidyverse")

#Import library

library(tidyverse)

# Check data types:

str(df)

# Check for missing values:

#When i ran the colSums code i encountered an error, went online to do some findings and i found the 2nd code which worked
colSums(is.na(df))
df <- df[rowSums(is.na(df)) == 0, ]
#or use this code 
missing <- !complete.cases(df)
#check the output of the missing values
df[missing, ]


#Drop missing values

na.omit(df)


# check to make sure that the column has been removed
head(df)

#Check for duplicates
dim(df[duplicated(df$Film),])[1]

#round off values to 2 places

df$Profitability <- round(df$Profitability ,digit=2)

df$Worldwide.Gross <- round(df$Worldwide.Gross ,digit=2)

View(df)

dim(df)

#Check for outliers using a boxplot

library(ggplot2)

#remove outlier

#install the package
install.packages("ggstatsplot")

# Load the package
library(ggstatsplot)

#Create a boxplot that labels the outliers
ggplot(df, aes(x=Profitability, y=Worldwide.Gross)) + geom_boxplot(outlier.colour = "red", outlier.shape = 1)+ scale_x_continuous(labels = scales::comma)+coord_cartesian(ylim = c(0, 1000))

#Remove outliers in 'Profitability'
Q1 <- quantile(df$Profitability, .25)
Q3 <- quantile(df$Profitability, .75)
IQR <- IQR(df$Profitability)

no_outliers <- subset(df, df$Profitability> (Q1 - 1.5*IQR) & df$Profitability< (Q3 + 1.5*IQR))

dim(no_outliers) 

# Remove outliers in 'Worldwide.Gross'
Q1 <- quantile(no_outliers$Worldwide.Gross, .25)
Q3 <- quantile(no_outliers$Worldwide.Gross, .75)
IQR <- IQR(no_outliers$Worldwide.Gross)

df1 <- subset(no_outliers, no_outliers$Worldwide.Gross> (Q1 - 1.5*IQR) & no_outliers$Worldwide.Gross< (Q3 + 1.5*IQR))

dim(df1) 

#Summary Statistics:
summary(df1)

#bivariate analysis
#Scatterplots

ggplot(df1, aes(x=Lead.Studio, y=Rotten.Tomatoes..)) + geom_point()+ scale_y_continuous(labels = scales::comma)+coord_cartesian(ylim = c(0, 110))+theme(axis.text.x = element_text(angle = 90))

#Bar chart
ggplot(df1, aes(x=Year)) + geom_bar()

#Export clean data
write.csv(df1,"clean_df.csv")

#Create dashboards on PowerBi

