### Background for this activity
This activity is focused on creating and using data frames in `R`. A data frame is a collection of columns containing data, similar to a spreadsheet or SQL table. Data frames are one of the basic tools you use when working with data in `R`. And you can create data frames from different data sources.  

There are three common sources for data:

- A`package` with data that can be accessed by loading that `package`
- An external file like a spreadsheet or CSV that can be imported into `R`
- Data that has been generated from scratch using `R` code

Wherever data comes from, you will almost always want to store it in a data frame object to work with it.

### Step 1: Load packages

Start by installing the required package; in this case, you will want to install `tidyverse`. If you have already installed and loaded `tidyverse` in this session, feel free to skip the code chunks in this step.

```r
install.packages("tidyverse")
```

Once a package is installed, you can load it by running the `library()` function with the package name inside the parentheses:

```r
library(tidyverse)
```

### Step 2: Create data frame

Sometimes you will need to generate a data frame directly in `R`. There are a number of ways to do this; one of the most common is to create individual vectors of data and then combine them into a data frame using the `data.frame()` function.

Here's how this works. First, create a vector of names by inserting four names into this code block between the quotation marks and then run it:

```r
names <- c("", "", "", "")
```

Then create a vector of ages by adding four ages separated by commas to the code chunk below. Make sure you are inputting numeric values for the ages or you might get an error. 

```r
age <- c(, , , )
```

With these two vectors, you can create a new data frame called `people`:

```r
people <- data.frame(names, age)
```

### Step 3: inspect the data frame

Now that you have this data frame, you can use some different functions to inspect it.

One common function you can use to preview the data is the `head()` function, which returns the columns and the first several rows of data. You can check out how the `head()` function works by running the chunk below:

```r
head(people)
```

In addition to `head()`, there are a number of other useful functions to summarize or preview your data. For example, the `str()` and `glimpse()` functions will both provide summaries of each column in your data arranged horizontally. You can check out these two functions in action by running the code chunks below:

```r
str(people)
```

```r
glimpse(people)
```

You can also use `colnames()` to get a list the column names in your data set. Run the code chunk below to check out this function:

```r
colnames(people)
```

Now that you have a data frame, you can work with it using all of the tools in `R`. For example, you could use `mutate()` if you wanted to create a new variable that would capture each person's age in twenty years. The code chunk below creates that new variable:

```r
mutate(people, age_in_20 = age + 20)
```


### Step 4: Try it yourself

To get more familiar with creating and using data frames, use the code chunks below to create your own custom data frame. 

First, create a vector of any five different fruits. You can type directly into the code chunk below; just place your cursor in the box and click to type. Once you have input the fruits you want in your data frame, run the code chunk.

```r
fruit <- c("apple", "strawberry", "peach", "banana")
```

Now, create a new vector with a number representing your own personal rank for each fruit. Give a 1 to the fruit you like the most, and a 5 to the fruit you like the least. Remember, the scores need to be in the same order as the fruit above. So if your favorite fruit is last in the list above, the score `1` needs to be in the last position in the list below. Once you have input your rankings, run the code chunk.

```{r}
rank <- c(2, 3, 1, 4)
```

Finally, combine the two vectors into a data frame. You can call it `fruit_ranks`. Edit the code chunk below and run it to create your data frame.

```{r}
fruit_ranks <- data.frame(fruit, rank)
```

After you run this code chunk, it will create a data frame with your fruits and rankings.

<img width="200" alt="fruit_rank" src="https://user-images.githubusercontent.com/109593672/232287150-b561e5ae-7ea3-4ea6-b694-6c3861a05dbd.PNG">
