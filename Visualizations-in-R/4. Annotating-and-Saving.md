In this activity, you'll review a scenario, and practice adding annotations to a data visualization with ggplot2

## The Scenario

As a junior data analyst for a hotel booking company, you have been creating visualizations in `R` with the `ggplot2`  package to share insights about your data with stakeholders. After creating a series of visualizations using `ggplot()`, `ggplot2` aesthetics, and filters, your stakeholder asks you to add annotations to your visualizations to help explain your findings in a presentation. Luckily, `ggplot2` has annotation functions built in.  

## Annotating your chart

Annotations help clarify your plot by adding notes, highlighting important points, or discussing trends. You can add `labels`, `titles`, `subtitles`, and `captions`. You can also use arrows and shapes for emphasis. Usually added in presentation software, you can now directly include `lines`, `arrows`, and `shapes` in your plots using ggplot2.

Highlighting specific points with a lable:
```r
annotate("text", x=200, y=35500, lable="What you want the labe to read", color="purple", fontface="bold", size=4.5, angle=25)

text: information on the type of label
x=200, y=35500: specific location of the lable
lable="What you want the labe to read": context of the label
color="purple": customize our annotation
fontface="bold", size=4.5, angle=25: font style, size, angle of our text
```
As a refresher, here is the chart you created before:
```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = market_segment)) +
  facet_wrap(~hotel)
```

The first step will be adding a title; that is often the first thing people will pay attention to when they encounter a data visualization for the first time. To add a title, you will add `labs()` at the end of your `ggplot()` command and then input a title there:

`Example:`

```r
labs(title="title goes here", subtitle="subtitle goes here", caption="this could be a citation")
```

```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = market_segment)) +
  facet_wrap(~hotel) +
  labs(title="Comparison of market segments by hotel type for hotel bookings")
```

You also want to add another detail about what time period this data covers. To do this, you need to find out when the data is from. 

You realize you can use the `min()` function on the year column in the data:

```r
min(hotel_bookings$arrival_date_year)
```
 
And the `max()` function:
```r
max(hotel_bookings$arrival_date_year)
```

But you will need to save them as variables in order to easily use them in your labeling; the following code chunk creates two of those variables: 
```r
mindate <- min(hotel_bookings$arrival_date_year)
maxdate <- max(hotel_bookings$arrival_date_year)
```

Now, you will add in a subtitle using `subtitle=` in the `labs()` function. Then, you can use the `paste0()` function to use your newly-created variables in your labels. This is really handy, because if the data gets updated and there is more recent data added, you don't have to change the code below because the variables are dynamic:

```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = market_segment)) +
  facet_wrap(~hotel) +
  labs(title="Comparison of market segments by hotel type for hotel bookings",
       subtitle=paste0("Data from: ", mindate, " to ", maxdate))
```

You decide to switch the `subtitle`  to a `caption` which will appear in the bottom right corner instead.

```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = market_segment)) +
  facet_wrap(~hotel) +
  labs(title="Comparison of market segments by hotel type for hotel bookings",
       caption=paste0("Data from: ", mindate, " to ", maxdate))
```

Now you want to clean up the [x] and [y] axis labels to make sure they are really clear. To do that, you can add to the `labs()` function and use `x=` and `y=`. Feel free to change the text of the label and play around with it:

```r
ggplot(data = hotel_bookings) +
  geom_bar(mapping = aes(x = market_segment)) +
  facet_wrap(~hotel) +
  labs(title="Comparison of market segments by hotel type for hotel bookings",
       caption=paste0("Data from: ", mindate, " to ", maxdate),
       x="Market Segment",
       y="Number of Bookings")
```

## Saving your chart

The `ggsave()` function was used to save the last plot that was generated, so if you have run something after running the code chunk above, then run that code chunk again. 

Then run the following code chunk to save that plot as a .png file named `city_payment_chart`, which makes it clear to your stakeholders what the .png file contains. Now you should be able to find this file in your 'Files' tab in the bottom right of your screen. Check it out!

```r
ggsave('hotel_booking_chart.png')
```

If you wanted to make your chart bigger and more rectangular to fit the slide show presentation, you could specify the height and width of your .png in the `ggsave()` command. Edit the code chunk below to create a 16x8 .png image: 

```r
ggsave('hotel_booking_chart.png',
       width=16,
       height=8)
```
