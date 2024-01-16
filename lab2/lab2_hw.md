---
title: "Lab 2 Homework"
author: "Elyse Carosa"
date: "2024-01-16"
output:
  html_document: 
    theme: spacelab
    keep_md: true
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

1. What is a vector in R?    
A vector is a structure designed to group together data. It puts everything into a list with all of your data in it which keeps it organized and together.

2. What is a data matrix in R?  
A data matrix is also a structure and is meant to group together strings of vectors. It also organizes your vectors into rows and columns, which organizes your data and makes it easier to read and analyze.

3. Below are data collected by three scientists (Jill, Steve, Susan in order) measuring temperatures of eight hot springs. Run this code chunk to create the vectors.  

```r
spring_1 <- c(36.25, 35.40, 35.30)
spring_2 <- c(35.15, 35.35, 33.35)
spring_3 <- c(30.70, 29.65, 29.20)
spring_4 <- c(39.70, 40.05, 38.65)
spring_5 <- c(31.85, 31.40, 29.30)
spring_6 <- c(30.20, 30.65, 29.75)
spring_7 <- c(32.90, 32.50, 32.80)
spring_8 <- c(36.80, 36.45, 33.15)
```

4. Build a data matrix that has the springs as rows and the columns as scientists.  


```r
science_data <- c(spring_1, spring_2, spring_3, spring_4, spring_5, spring_6, spring_7, spring_8)
```


```r
temperature_matrix <- matrix(science_data, nrow = 8, byrow = T)
temperature_matrix
```

```
##       [,1]  [,2]  [,3]
## [1,] 36.25 35.40 35.30
## [2,] 35.15 35.35 33.35
## [3,] 30.70 29.65 29.20
## [4,] 39.70 40.05 38.65
## [5,] 31.85 31.40 29.30
## [6,] 30.20 30.65 29.75
## [7,] 32.90 32.50 32.80
## [8,] 36.80 36.45 33.15
```

5. The names of the springs are 1.Bluebell Spring, 2.Opal Spring, 3.Riverside Spring, 4.Too Hot Spring, 5.Mystery Spring, 6.Emerald Spring, 7.Black Spring, 8.Pearl Spring. Name the rows and columns in the data matrix. Start by making two new vectors with the names, then use `colnames()` and `rownames()` to name the columns and rows.


```r
spring_names <- c("Bluebell_Spring", "Opal_Spring", "Riverside_Spring", "Too_Hot_Spring", "Mystery_Spring", "Emerald_Spring", "Black_Spring", "Pearl_Spring")
spring_names
```

```
## [1] "Bluebell_Spring"  "Opal_Spring"      "Riverside_Spring" "Too_Hot_Spring"  
## [5] "Mystery_Spring"   "Emerald_Spring"   "Black_Spring"     "Pearl_Spring"
```


```r
scientists <- c("Jill", "Steve", "Susan")
scientists
```

```
## [1] "Jill"  "Steve" "Susan"
```


```r
rownames(temperature_matrix) <- spring_names
```


```r
colnames(temperature_matrix) <- scientists
```


```r
temperature_matrix
```

```
##                   Jill Steve Susan
## Bluebell_Spring  36.25 35.40 35.30
## Opal_Spring      35.15 35.35 33.35
## Riverside_Spring 30.70 29.65 29.20
## Too_Hot_Spring   39.70 40.05 38.65
## Mystery_Spring   31.85 31.40 29.30
## Emerald_Spring   30.20 30.65 29.75
## Black_Spring     32.90 32.50 32.80
## Pearl_Spring     36.80 36.45 33.15
```


6. Calculate the mean temperature of all eight springs.


```r
Bluebell_Spring <- temperature_matrix[1, ]
mean(Bluebell_Spring)
```

```
## [1] 35.65
```


```r
Opal_Spring <- temperature_matrix[2, ]
mean(Opal_Spring)
```

```
## [1] 34.61667
```


```r
Riverside_Spring <- temperature_matrix[3, ]
mean(Riverside_Spring)
```

```
## [1] 29.85
```


```r
Too_Hot_Spring <- temperature_matrix[4, ]
mean(Too_Hot_Spring)
```

```
## [1] 39.46667
```


```r
Mystery_Spring <- temperature_matrix[5, ]
mean(Mystery_Spring)
```

```
## [1] 30.85
```


```r
Emerald_Spring <- temperature_matrix[6, ]
mean(Emerald_Spring)
```

```
## [1] 30.2
```


```r
Black_Spring <- temperature_matrix[7, ]
mean(Black_Spring)
```

```
## [1] 32.73333
```


```r
Pearl_Spring <- temperature_matrix[8, ]
mean(Pearl_Spring)
```

```
## [1] 35.46667
```


```r
Mean_Values <- c(mean(Bluebell_Spring), mean(Opal_Spring), mean(Riverside_Spring), mean(Too_Hot_Spring), mean(Mystery_Spring), mean(Emerald_Spring), mean(Black_Spring), mean(Pearl_Spring))
```


7. Add this as a new column in the data matrix.  


```r
cbind(temperature_matrix, Mean_Values)
```

```
##                   Jill Steve Susan Mean_Values
## Bluebell_Spring  36.25 35.40 35.30    35.65000
## Opal_Spring      35.15 35.35 33.35    34.61667
## Riverside_Spring 30.70 29.65 29.20    29.85000
## Too_Hot_Spring   39.70 40.05 38.65    39.46667
## Mystery_Spring   31.85 31.40 29.30    30.85000
## Emerald_Spring   30.20 30.65 29.75    30.20000
## Black_Spring     32.90 32.50 32.80    32.73333
## Pearl_Spring     36.80 36.45 33.15    35.46667
```


8. Show Susan's value for Opal Spring only.


```r
temperature_matrix[2,3]
```

```
## [1] 33.35
```


9. Calculate the mean for Jill's column only.  


```r
Jill_Data <- c(36.25, 35.15, 30.70, 39.70, 31.85, 30.20, 32.90, 36.80)
mean(Jill_Data)
```

```
## [1] 34.19375
```

10. Use the data matrix to perform one calculation or operation of your interest.


```r
St.Dev <- c(sd(Bluebell_Spring), sd(Opal_Spring), sd(Riverside_Spring), sd(Too_Hot_Spring), sd(Mystery_Spring), sd(Emerald_Spring), sd(Black_Spring), sd(Pearl_Spring))
```


```r
cbind(temperature_matrix, St.Dev)
```

```
##                   Jill Steve Susan    St.Dev
## Bluebell_Spring  36.25 35.40 35.30 0.5220153
## Opal_Spring      35.15 35.35 33.35 1.1015141
## Riverside_Spring 30.70 29.65 29.20 0.7697402
## Too_Hot_Spring   39.70 40.05 38.65 0.7285831
## Mystery_Spring   31.85 31.40 29.30 1.3610658
## Emerald_Spring   30.20 30.65 29.75 0.4500000
## Black_Spring     32.90 32.50 32.80 0.2081666
## Pearl_Spring     36.80 36.45 33.15 2.0139100
```


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.  
