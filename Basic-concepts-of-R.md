## Functions

`Function` = A body of reusable code for performing specific tasks in `R`

In `R` a `function` is a piece of code that does a specific job. `Functions` help to keep your code neat and avoid repeating the same code. To create a `function`, you use the word "**function**" and write the code inside curly braces. You can then use the `function` in your program by calling its name and giving it the needed information.

For `example`, here's a simple function that adds two numbers:


```r
my_function <- function() {
  print("Hello World!")
}

my_function() 
```
To use this `function` to add **3** and **7**, you would write:

```r
sum <- add_numbers(3, 7)
```
The `function` takes **3** and **7**, adds them, and gives back the result **(10)**, which is stored in the variable *sum*.

## Operators

`Operator` = A a symbol in programming that does a specific action on values or variables. There are different types of operators:

**Arithmetic operators:** Do math, like addition **(+)**, subtraction **(-)**, multiplication **(*)**, and division **(/)**.

`Example`:

```r
a <- 5 + 3  # a is 8
```

**Comparison operators:** Compare values, like equal to **(==)**, greater than **(>)**, or less than **(<)**.

`Example`:

```r
x <- 5
y <- 3
result <- x > y  # result is TRUE (5 is greater than 3)
```

**Logical operators:** Work with *true* or *false* values, like **AND** (&& or & in R) and **OR** (|| or | in R) **NOT** (!=).

`Example`:

```r
x <- 5
y <- 3
z <- 7
result <- x > y & z > x  # result is TRUE (5 > 3 and 7 > 5)
```

**Assignment operators:** Give a value to a variable. In R, it's **<-** or the equal sign **(=)**.

`Example`:

```r
age <- 11
```

## Argument

`Argument` = information needed by a `function` in `R` in order to run

In `R`, an `argument` is the information you give to a `function` when you use it. `Arguments` are like the ingredients you put into a recipe. When you use a `function`, you need to give it the right `arguments` so it can do its job.

For `example`, in the **add_numbers** `function`:

```r
add_numbers <- function(a, b) {
  result <- a + b
  return(result)
}
```

Here, **a** and **b** are the `arguments`. When you use this `function`, you need to give it two numbers, like this:

```r
sum <- add_numbers(3, 7)
```

In this example, **3** and **7** are the `arguments` for the **add_numbers** `function`. The `function` uses these `arguments` to do its job, which is to add the numbers together and give you the result **(10)**.

## Comment

`Comment` = Helpful text that describes or explains R code, preceded by #

In `R`, you can create a single-line `comment` by using the hash symbol **#** at the beginning of the `comment`. Everything after the hash symbol on that line is treated as a `comment` and ignored by `R`. 

Here's an `example` of using `comments` in `R` code:

```r
# This is a comment in R
add_numbers <- function(a, b) {
  # This function adds two numbers together
  result <- a + b
  return(result) # Return the sum of the two numbers
}

# Call the add_numbers function with arguments 3 and 7
sum <- add_numbers(3, 7)
```

In this `example`, all the lines starting with the hash symbol (#) are `comments`. They help explain what the code is doing without affecting how the program runs.

## Variable

`Variable` = A representation of a value in `R` that can be stored for later use

A `variable` is like a box that holds a piece of information in your code. You give it a name and a value. `Variables` are helpful because they let you store, change, and use values easily.

For `example`, in `R`, you can make a `variable` called *age* and give it the value **11** like this:

```r
age <- 11
```

Now, *age* is the name of the `variable`, and **11** is the value it has. You can use `variables` in your code to do math, make choices, or save the results of a `function`.

## Data Types

`Data Types` = An attribute that describes a piece of data based on its values, its programming language, or the operations it can perform

`Data types` are categories of values in programming, like numbers, text, or other kinds of data. They help the computer understand what kind of information is being used. Some common `data types` are:

***Integer:*** Whole numbers, like **5** or **-3**.
***Float:*** Numbers with decimals, like **3.14** or **-0.5**.
***Boolean:*** *True* or *false* values.
***String:*** Text, like **"hello"** or **"I love coding"**.
***List:*** A collection of values in order, like **[1, 2, 3]**.
***Dictionary:*** A collection of key-value pairs, like **{"name": "Alice", "age": 30}**.

Knowing `data types` in the language you're using is important to store and work with information correctly.

## Vector

`Vector`= A group of data elements of the same type stored in a one-dimensional sequence in `R`

A `vector` is a sequence of values, like a list or row of numbers or words, all of the same type. `Vectors` are important in `R` programming.

To create a `vector` in R`,` use the **c()** function, like this:

```r
# A vector of numbers
numbers <- c(1, 2, 3, 4, 5)

# A vector of words
animals <- c("cat", "dog", "elephant")
```

You can do various things with `vectors`, like adding elements, picking specific items, or finding the length. `R` has many built-in functions to work with `vectors` easily.

## Pipe

`Pipe` = A tool in `R` for expressing a sequence of multiple operations, represented with %>%

A `pipe` is a way to connect `functions` in programming, making it easier to do multiple steps in a clear and organized way. In `R`, the `pipe` operator (%>%) helps you pass the output of one `function` as input to another `function`.

Here's an `example` of using the `pipe` operator in `R`:

```r
# Sample data
data <- data.frame(
  name = c("Alice", "Bob", "Charlie", "David"),
  age = c(30, 25, 35, 28),
  score = c(90, 80, 85, 95)
)

# Using the pipe operator to filter and sort the data
result <- data %>%
  filter(age > 28) %>%
  arrange(score)
```

In this `example`, we filter the data for people older than **28** and sort the rows by their scores. The `pipe` operator makes it easy to do these operations one after another in a readable way. Without `pipes`, your code might look more complicated and be harder to understand.

