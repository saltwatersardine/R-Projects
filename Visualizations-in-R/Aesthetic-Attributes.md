There are three basic aesthetic attributes to consider when creating ggplot2 visualizations in R: `color`, `size`, and `shape`. These attributes are essential tools for creating data visualizations with ggplot2 and are built directly into its code.

## Aesthetics in ggplot2

`Ggplot2` is an R package that allows you to create different types of data visualizations right in your R workspace. In ggplot2, an `aesthetic` is defined as a visual property of an object in your plot. 

Basic aesthetic attributes in ggplot2:

- `Color:` this allows you to change the color of all of the points on your plot, or the color of each data group
- `Size:` this allows you to change the size of the points on your plot by data group
- `Shape:` this allows you to change the shape of the points on your plot by data group

An example of how aesthetic attributes are displayed in R:

```r
ggplot(data, aes(x=distance, y= dep_delay, color=carrier, size=air_time, shape = carrier)) +
      geom_point()
```
