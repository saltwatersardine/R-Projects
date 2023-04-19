## Cleaning data solutions

This document focuses on cleaning real data in R. Learn about data cleaning functions and perform basic calculations to gain initial insights into your data.

## The scenario

In this scenario, you are a junior data analyst working for a hotel booking company. You have been asked to clean a .csv file that was created after querying a database to combine two different tables from different hotels. In order to learn more about this data, you are going to need to use functions to preview the data's structure, including its columns and rows. You will also need to use basic cleaning functions to prepare this data for analysis.

## Step 1: Load packages

Start by installing the required packages:`tidyverse`, `skimr`, and `janitor`

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

In the chunk below, you will use the `read_csv()` function to import data from a .csv in the project folder called "hotel_bookings.csv" and save it as a data frame called `bookings_df`:

```r
bookings_df <- read_csv("hotel_bookings.csv")
```
## Step 3: Getting to know your data

Before you start cleaning your data, take some time to explore it. You can use several functions to preview your data, including the `head()` function in the code chunk below:

```r
head(bookings_df)
```

You can summarize or preview the data with the `str()` and `glimpse()` functions to get a better understanding of the data by running the code chunks below:

```r
str(bookings_df)
```

```r
glimpse(bookings_df)
```

You can also use `colnames()` to check the names of the columns in your data set. Run the code chunk below to find out the column names in this data set:

```r
colnames(bookings_df)
```

Use the `skim_without_charts()` function from the `skimr` package by running the code below:

```r
skim_without_charts(bookings_df)
```
## Step 4: Cleaning your data

Based on your notes you are primarily interested in the following variables: hotel, is_canceled, lead_time. Create a new data frame with just those columns, calling it `trimmed_df`.

```r
trimmed_df <- bookings_df %>% 
  select(hotel, is_canceled, lead_time)
```

Rename the variable 'hotel' to be named 'hotel_type' to be crystal clear on what the data is about:

```r
trimmed_df %>% 
  select(hotel, is_canceled, lead_time) %>% 
  rename(hotel_type = hotel)
```

In this example, you can combine the arrival month and year into one column using the unite() function:

```r
example_df <- bookings_df %>%
  select(arrival_date_year, arrival_date_month) %>% 
  unite(arrival_month_year, c("arrival_date_month", "arrival_date_year"), sep = " ")
```
## Step 5: Organizing your Data

To use `arrange()`, `group_by()`, and `filter()` functions, you need to first install and load the `dplyr` and `readr` packages 

```r
install.packages(c("dplyr", "readr"))
library(dplyr)
library(readr)
```

Let's filter the dataset to keep only non-cancelled bookings (is_canceled == 0). Then, arrange the data by lead_time in ascending order and group by hotel type

```r
filtered_arranged_grouped_data <- hotel_bookings %>%
  filter(is_canceled == 0) %>%
  arrange(lead_time) %>%
  group_by(hotel)
```

In this example, we first filter the dataset to keep only non-cancelled bookings using `filter(is_canceled == 0)`. Then, we arrange the data by `lead_time` in ascending order using `arrange(lead_time)`. Finally, we group the data by hotel type using `group_by(hotel)`.

You can adjust the conditions in the `filter()` and columns in the `arrange()` and `group_by()` functions to customize the analysis as needed.

## Step 6: Another way of doing things

You can also use the`mutate()` function to make changes to your columns. Let's say you wanted to create a new column that summed up all the adults, children, and babies on a reservation for the total number of people. Modify the code chunk below to create that new column: 

```r
example_df <- bookings_df %>%
  mutate(guests = adults + children + babies)

head(example_df)
```
Great. Now it's time to calculate some summary statistics! Calculate the total number of canceled bookings and the average lead time for booking - you'll want to start your code after the %>% symbol. Make a column called 'number_canceled' to represent the total number of canceled bookings. Then, make a column called 'average_lead_time' to represent the average lead time. Use the `summarize()` function to do this in the code chunk below:

```r
example_df <- bookings_df %>%
  summarize(number_canceled = sum(is_canceled),
            average_lead_time = mean(lead_time))

head(example_df)
```
