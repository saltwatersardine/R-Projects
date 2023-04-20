In this activity, you'll make use of the filters and facets features of ggplot2 to create custom visualizations based on different criteria. 

## The Scenario

As a junior data analyst for a hotel booking company, you have been asked to clean hotel booking data, create visualizations with `ggplot2` to gain insight into the data, and present different facets of the data through visualization. Now, you are going to build on the work you performed previously to apply filters to your data visualizations in `ggplot2`.  

## Making many different charts

As a refresher, here's the `scatter plot`:

```r
ggplot(data = hotel_bookings) +
  geom_point(mapping = aes(x = lead_time, y = children))
```

You decide to create a `bar chart` showing each hotel type and market segment. You use different colors to represent each market segment:

```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = hotel, fill = market_segment))
```

You decide to use the `facet_wrap()` function to create a separate plot for each market segment: 

```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = hotel)) +
  facet_wrap(~market_segment)
```

## Filtering

Filtering your data before you plot it allows you to focus on specific subsets of your data and gain more targeted insights. To do this, just include the `dplyr` filter() function in your `ggplot` syntax. 

`Example:`

```r
data %>%
    filter(variable1 == "DS") %>%  
    ggplot(aes(x = weight, y = variable2, colour = variable1)) +  
    geom_point(alpha = 0.3,  position = position_jitter()) + stat_smooth(method = "lm")
```

Use the `filter()` function to create a data set that only includes the data you want: 

```r
onlineta_city_hotels <- filter(hotel_bookings, 
                           (hotel=="City Hotel" & 
                             hotel_bookings$market_segment=="Online TA"))
```
`'$':` dollar symbol is used to extract or subset a specific part of a data object

You can use the`View`() function to check out your new data frame:

```r
View(onlineta_city_hotels)
```

You can use the `pipe operator` (%>%) to do this in steps! 

You name this data frame `onlineta_city_hotels_v2`:

```r
onlineta_city_hotels_v2 <- hotel_bookings %>%
  filter(hotel=="City Hotel") %>%
  filter(market_segment=="Online TA")
```

This code chunk generates the same data frame by using the `View()` function:

```r
View(onlineta_city_hotels_v2)
```

## Use your new dataframe

Using the code for your previous scatterplot, replace `variable_name` in the code chunk below with either `onlineta_city_hotels` or `onlineta_city_hotels_v2` to plot the data your stakeholder requested:

```r
ggplot(data = onlineta_city_hotels) +
  geom_point(mapping = aes(x = lead_time, y = children))
```
