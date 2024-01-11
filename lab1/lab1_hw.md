---
title: "Lab 1 Homework"
author: "Elyse Carosa"
date: "2024-01-11"
output:
  html_document: 
    theme: spacelab
    keep_md: true
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

**1. Please complete the [class survey](https://forms.gle/AHHXd3aobaAdkkFg9) if you have not already done so.**  
Survey completed.  
**2. What is the difference between R and RStudio? What is GitHub and why is it useful to programmers?**  
R is the scripting language. You essentially tell it what you want it to do (give it commands), and it does it for you. It is the program, and RStudio is the GUI (Geographical User Interface). RStudio is easier to use than R, which makes it more popular.  
GitHub is a platform that uses GIT to track changes to code and information written using R. It lets people everywhere view uploaded code and see previous drafts of it. This allows for collaboration and the potential for errors to be found.


**3. Navigate to my [BIS15L](https://github.com/jmledford3115/BIS15LW2024_jledford) repository on GitHub. Notice that near the bottom there is a nice, clean description of the repository. You want this on your repository! It is built by making edits to the `README.md` file using the RMarkdown conventions. Edit your repository's `README.md` file so that you have a clean informative description, including your email address. Be creative! You don't need to just copy mine. There are lots of examples online.**  
Done

**4. Calculate the following expressions. Be sure to include each one in a separate code chunk.**  

```r
5 - 3 * 2  
```

```
## [1] -1
```


```r
8 / 2 * 2 
```

```
## [1] 8
```

**5. Did any of the results in #4 surprise you? Write two programs that calculate each expression such that the result for the first example is 4 and the second example is 8.**    
The results weren't very surprising. Both equations lacked any parenthesis to guide the software in its calculations, so the answers were what I expected based on that. However, it was interesting to see how many ways there are to manipulate equations to get different answers, even if it just means adding something as seemingly insignificant as a set of parenthesis.  


```r
(5 - 3) * 2
```

```
## [1] 4
```


```r
(8 / 2) * 2
```

```
## [1] 8
```

**6. `Objects` in R are a way in which we can store data or operations. We will talk more about objects next week. For now, make a new object `pi` as 3.14159265359 by running the following code chunk. You should now see the object `pi` in the environment window in the top right.**  

```r
pi <- 3.14159265359
```

**7. Let's say we want to multiply `pi` by 2. Using the same arithmetic principles that we just learned, write a code chunk that performs this operation using the object we created.**  


```r
pi*2
```

```
## [1] 6.283185
```

**8. In order to get help with any command in R, just type a `?` in front the command of interest. Practice this by running the following code chunk.**  

```r
?mean
```

```
## starting httpd help server ... done
```

**9. Let's calculate the mean for the numbers 2, 8, 6, 4, 9, 10. I have built an object `x` for you below so all you need to do is run the first code chunk and then create a second code chunk that shows the calculation. Give it a try!**  

```r
x <- c(2, 8, 6, 6, 7, 4, 9, 9, 9, 10)
```


```r
mean(x)
```

```
## [1] 7
```

**10. Repeat the procedure above, but this time calculate the median.**  

```r
median(x)
```

```
## [1] 7.5
```

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.  
