`R` is a versatile language that provides a range of `operators` to perform different operations. These `operators` can be broadly classified into the following categories:

- Arithmetic Operators
- Relational Operators
- Logical Operators
- Assignment Operators
- Miscellaneous Operators

## Arithmetic Operators

`Arithmetic operators` in `R` are used for mathematical calculations. They include:

- `+`: Addition
- `-`: Subtraction
- `*`:  Multiplication
- `/`: Division
- `^` or `**`: Exponent (power of) 
- `%%`: Modulus (returns the remainder after division)
- `%/%`: Integer Division (returns an integer value after division) 

`Example`:

```r
a <- 2
b <- 5

addition <- a + b
  result = 7
subtraction <- a - b
  result = -3
multiplication <- a * b
  result = 10
division <- a / b
  result = 0.4
exponent <- b ^ 2
  result = 25
modulus <- b %% a
  result = 1
integer_division <- b %/% a
  result = 2 
```

## Relational Operators

`Relational operators` compare values and return a logical value (`TRUE` or `FALSE`). They include:

- `==`: Equal to
- `!=`: Not equal to
- `<`: Less than
- `>`: Greater than
- `<=`: Less than or equal to
- `>=`: Greater than or equal to

`Example`:

```r
x <- 5
y <- 10

equal <- x == y
  result = FALSE
not_equal <- x != y
  result = TRUE
less_than <- x < y
  result = TRUE
greater_than <- x > y
  result = FALSE
less_than_or_equal <- x <= y
  result = TRUE
greater_than_or_equal <- x >= y
  result = FALSE
```

## Logical Operators 

`Logical operators` are used to perform logical operations and return a logical value (`TRUE` or `FALSE`). They include:

- `&`: Element-wise AND
- `|`: Element-wise OR
- `!`: NOT
- `&&`: AND
- `||`: OR

`Example`:

```r
a <- TRUE
b <- FALSE

and_operator <- a & b
  result = FALSE
or_operator <- a | b
  result = TRUE
not_operator <- !a
  result = FALSE
double_and_operator <- a && b
  result = FALSE
double_or_operator <- a || b
  result = TRUE
```

## Assignment Operators

Assignment operators are used to assign values to variables. They include:

- `<-`: Leftward assignment
- `->`: Rightward assignment
- `=`: Equals assignment

`Example`:

```r
# Leftward assignment
x <- 10
# Rightward assignment
20 -> y
# Equals assignment
z = 30
```

## Miscellaneous Operators

These operators include:

- `:`: Sequence operator
- `%in%`: Matching operator

`Example`:

```r
# Sequence operator
sequence <- 1:10

# Matching operator
x <- c(1, 2, 3, 4)
y <- c(3, 4, 5, 6)
common_elements <- x %in% y
```
For more information, you can refer to the [R documentation](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/Arithmetic).

