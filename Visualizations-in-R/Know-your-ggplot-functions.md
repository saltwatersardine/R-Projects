<img width="373" alt="chart" src="https://user-images.githubusercontent.com/109593672/233394960-cc41d296-fb5a-45c5-9051-d01b9de80a7a.PNG">

- `Chart title:` To add a title to the chart, use a label function: 
```r
title = Average product rating
```
- `Blue and yellow bars:` To highlight underperforming products, use an aesthetics function: 
```r
col = ifelse (x<2, 'blue', 'yellow')
```
- `Bar chart:` To create the bars on the chart, use a geom function: 
```r
geom_bar()
```

<img width="413" alt="features" src="https://user-images.githubusercontent.com/109593672/233396324-1d30befb-b3e8-4423-a4b8-970a945741c3.PNG">

- `Trend line:` To create a trend line, use a geom function: 
```r
geom_smooth()
```
- `Scatter plot chart:` To create the scatter plot, use a geom function: 
```r
geom_point()
```
<img width="800" alt="Compare" src="https://user-images.githubusercontent.com/109593672/233397139-c563637b-495e-4410-9dd8-e0f9ca0551d7.PNG">

- `Axis labels:` To label the axes, use an aesthetics function: 
```r
aes (x = Average price (USD), y = Product)
```
- `Compare data:` To compare data trends across average ratings, use a facets function: 
```r
acet_wrap (~Average Rating)
```

