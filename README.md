---

# R Programming Comprehensive Notes

## Lecture 1: Introduction to R

### What is R?

* R is a **free and open-source** programming language.
* Primarily used for **statistical computing**, **data analysis**, and **data visualization**.
* Developed by **Robert Gentleman** and **Ross Ihaka** in 1995.
* Available at: [www.r-project.org](http://www.r-project.org)

### Why Learn R?

* Cross-platform: works on Windows, Mac, and Linux.
* Powerful graphing capabilities.
* Extensive built-in and user-contributed packages (>15,000).
* Easily integrates with C++, Java, Python, PHP, and others.

### Installing R and RStudio

1. Go to [CRAN](https://cran.r-project.org)
2. Choose your OS and download base system.
3. Install RStudio from [www.rstudio.com](https://www.rstudio.com)

### Code Editors

* **R Console**: good for quick commands.
* **Script Editor**: for saving, editing code.
* **RStudio**: integrated environment with syntax highlighting, tabbed panes, and history.

### Getting Help in R

```r
help(mean)    # documentation
?mean         # same as help()
args(mean)    # function arguments
example(mean) # usage example
??histogram   # search keyword
help.search("pattern")
```

### Printing in R

```r
print(pi)              # [1] 3.141593
cat("Pi is", pi, "\n")  # Pi is 3.141593
```

> Note: `print()` prints one object; `cat()` is better for formatted output.

---

## Constants and Variables in R

### Constants

```r
typeof(5)      # "double"
typeof(5L)     # "integer"
typeof(5i)     # "complex"
typeof("5")    # "character"
typeof(TRUE)   # "logical"
```

### Built-in Constants

* `LETTERS`, `letters`, `month.abb`, `month.name`, `pi`

### Variables

* Valid: `x`, `total_score`, `.var1`, `user1`
* Invalid: `5x`, `_name`, `TRUE`, `x@y`

### Data Types

* `numeric`, `integer`, `complex`, `character`, `logical`
* `vector`, `list`, `matrix`, `array`, `data.frame`, `factor`

### Type Conversion

```r
a <- 0:6
as.numeric(a)
as.character(a)
as.complex(a)
as.logical(a)
is.numeric(a)
is.character(a)
```

### Listing & Removing Variables

```r
ls()         # list variables
rm(x)        # remove x
rm(list=ls())# clear workspace
```

---

## Lecture 2: Data Structures & Input/Output

### Vectors

```r
a <- c(1, 2, 3)
b <- c("apple", "banana")
c <- c(TRUE, FALSE, TRUE)

seq(2, 10, 2)     # 2 4 6 8 10
rep(1:3, each=2)  # 1 1 2 2 3 3
```

#### Indexing

```r
w <- c(1,3,5,2,10)
w[3]        # 5
w[-2]       # all except 2nd
w[w > 3]    # 5, 10
```

### Matrices

```r
A <- matrix(1:12, nrow=3, byrow=TRUE)
dim(A) <- c(3,4)
cbind(1:3, 4:6)
rbind(1:3, 4:6)
```

### Arrays

```r
arr <- array(1:12, dim=c(2,3,2))
arr[2,3,1]   # value at [2,3] in 1st matrix
apply(arr, 2, sum)  # sum by column
```

### Lists

```r
x <- list(num=c(1,2,3), name="Nick", mat=diag(2))
x[[1]]       # first element
x$name       # access by name
```

### Data Frames

```r
id <- c(1,2)
age <- c(25,30)
gender <- c("M", "F")
mydata <- data.frame(id, age, gender)
mydata$age
mydata[ ,1:2]
```

---

## Data Input / Output

### Manual Input

```r
mydata <- data.frame(age=numeric(0), gender=character(0), weight=numeric(0))
mydata <- edit(mydata)
```

### Importing Data

```r
read.table("file.txt", header=TRUE, sep=",")
read.csv("file.csv", header=TRUE)
library(xlsx)
read.xlsx("file.xlsx", 1)
```

### Exporting Data

```r
write.table(mydata, "output.txt", sep=",")
write.csv(mydata, "output.csv")
write.xlsx(mydata, "output.xlsx")
```

---

## Lecture 3: Graphs in R

### Line Plots

```r
dose <- c(20, 30, 40, 45, 60)
drugA <- c(16, 20, 27, 40, 60)
plot(dose, drugA, type="b", col="red", pch=19, lty=2)
```

### Customizations

* `pch`: point symbol (e.g., 19)
* `lty`: line type (e.g., 2=dashed)
* `col`: color
* `lwd`: line width
* `cex`: point size

### Titles and Labels

```r
title(main="Main", sub="Subtitle", xlab="X", ylab="Y")
```

### Axes

```r
axis(2, at=1:10, las=2)
axis(4, at=c(1,2), labels=c("A","B"), col.axis="blue")
```

### Reference Lines

```r
abline(h=c(1,5), col="gray")
abline(v=seq(1,10,2), lty=2, col="blue")
```

### Legends

```r
legend("topleft", title="Drug", legend=c("A","B"), pch=c(19,17), col=c("red","blue"))
```

### Combining Graphs

```r
par(mfrow=c(2,2))
hist(mtcars$mpg)
plot(mtcars$wt, mtcars$mpg)
```

---

## Specific Plot Types

### Bar Plot

```r
counts <- table(Arthritis$Improved)
barplot(counts, main="Barplot", col="blue")
```

### Stacked / Grouped Bar Plot

```r
counts <- table(Arthritis$Improved, Arthritis$Treatment)
barplot(counts, beside=TRUE, col=c("red","green","blue"))
```

### Histogram

```r
hist(mtcars$mpg, breaks=12, col="orange")
```

### Pie Chart

```r
slices <- c(10, 20, 30)
labels <- c("A", "B", "C")
pie(slices, labels=labels)
```

### Box Plot

```r
boxplot(mpg ~ cyl, data=mtcars, col="lightblue")
```

---

> End of Markdown Notes
