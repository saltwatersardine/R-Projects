## Background for this activity
In this activity, you'll review a scenario, and focus on manipulating and changing real data in R. You will learn more about functions you can use to manipulate your data, use statistical summaries to explore your data, and gain initial insights for your stakeholders. 

## The Scenario
In this scenario, you are a junior data analyst working for a hotel booking company. You have been asked to clean a .csv file that was created after querying a database to combine two different tables from different hotels.

## Step 1: Load packages

Start by installing the required packages `tidyverse`, `skimr`, and `janitor`

```r 
install.packages("tidyverse")
install.packages("skimr")
install.packages("janitor")
```

Once a package is installed, you can load it by running the `library()` function with the package name inside the parentheses:

```r
library(tidyverse)
library(skimr)
library(janitor)
```

## Step 2: Import data

The data in this example is originally from the article Hotel Booking Demand Datasets (https://www.sciencedirect.com/science/article/pii/S2352340918315191), written by Nuno Antonio, Ana Almeida, and Luis Nunes for Data in Brief, Volume 22, February 2019.

The data was downloaded and cleaned by Thomas Mock and Antoine Bichat for #TidyTuesday during the week of February 11th, 2020 (https://github.com/rfordatascience/tidytuesday/blob/master/data/2020/2020-02-11/readme.md).

You can learn more about the dataset here:
https://www.kaggle.com/jessemostipak/hotel-booking-demand

In the chunk below, you will use the `read_csv()` function to import data from a .csv called "hotel_bookings.csv" and save it as a data frame called `hotel_bookings`:

```r
hotel_bookings <- read_csv("hotel_bookings.csv")
```

## Step 3: Getting to know your data

Like you have been doing in other examples, use the `head()` function to preview the columns and the first several rows of data by running the chunk below:

```r
head(hotel_bookings)
```

In addition to `head()` you can also use the `str()` and `glimpse()` functions to get summaries of each column in your data arranged horizontally. You can try these two functions by running the code chunks below:

```r
str(hotel_bookings)
```

You can see the different column names and some sample values to the right of the colon. 

```r
glimpse(hotel_bookings)
```

You can also use `colnames()` to get the names of the columns in your data set. Run the code chunk below to get the column names:

```r
colnames(hotel_bookings)
```

## Manipulating your data

Let's say you want to arrange the data by most lead time to least lead time because you want to focus on bookings that were made far in advance. You decide you want to try using the `arrange()` function and run the following command: 

```r
arrange(hotel_bookings, lead_time)
```

`arrange()` automatically orders by ascending order, and you need to specifically tell it when to order by descending order, like the below code chunk below:

```r
arrange(hotel_bookings, desc(lead_time))
```

Notice that when you just run `arrange()` without saving your data to a new data frame, it does not alter the existing data frame. Check it out by running `head()` again to find out if the highest lead times are first: 

```r
head(hotel_bookings)
```

If you wanted to create a new data frame that had those changes saved, you would use the <- as written in the code chunk below to store the arranged data in a data frame named 'hotel_bookings_v2'

```r
hotel_bookings_v2 <-
  arrange(hotel_bookings, desc(lead_time))
```

Check out the new data frame: 

```r
head(hotel_bookings_v2)
```

You can also find out the maximum and minimum lead times without sorting the whole data set using the `arrange()` function. Try it out using the max() and min() functions below:

```r
max(hotel_bookings$lead_time)
```

```r
min(hotel_bookings$lead_time)
```

Remember, in this case, you need to specify which data set and which column using the $ symbol between their names. Try running the below to see what happens if you forget one of those pieces:

```r
min(lead_time)
```

This is a common error that R users encounter. 

Now, let's say you just want to know what the average lead time for booking is because your boss asks you how early you should run promotions for hotel rooms. You can use the `mean()`function to answer that question:

```r
mean(hotel_bookings$lead_time)
```

You should get the same answer even if you use the v2 data set that included the `arrange()` function. 

```r
mean(hotel_bookings_v2$lead_time)
```

You were able to report to your boss what the average lead time before booking is 104.0114, but now they want to know what the average lead time before booking is for just city hotels. They want to focus the promotion they're running by targeting major cities.

You know that your first step will be creating a new data set that only contains data about city hotels. You can do that using the `filter()` function, and name your new data frame 'hotel_bookings_city':

```r
hotel_bookings_city <- 
  filter(hotel_bookings, hotel_bookings$hotel=="City Hotel")
```

Check out your new data set:

```r
head(hotel_bookings_city)
```

You quickly check what the average lead time for this set of hotels is, just like you did for all of hotels before:

```r
mean(hotel_bookings_city$lead_time)
```

Now, your boss wants to know a lot more information about city hotels, including the maximum and minimum lead time. They are also interested in how they are different from resort hotels. You don't want to run each line of code over and over again, so you decide to use the `group_by()`and`summarize()` functions. You can also use the pipe operator to make your code easier to follow. You will store the new data set in a data frame named 'hotel_summary':

```r
hotel_summary <- 
  hotel_bookings %>%
  group_by(hotel) %>%
  summarise(average_lead_time=mean(lead_time),
            min_lead_time=min(lead_time),
            max_lead_time=max(lead_time))
```

Check out your new data set using head() again:

```r
head(hotel_summary)
```
