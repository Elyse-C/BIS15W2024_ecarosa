---
title: "Lab 3 Homework"
author: "Elyse Carosa"
date: "2024-01-18"
output:
  html_document: 
    theme: spacelab
    keep_md: true
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the tidyverse

```r
library(tidyverse)
```

### Mammals Sleep  
1. For this assignment, we are going to use built-in data on mammal sleep patterns. From which publication are these data taken from? Since the data are built-in you can use the help function in R. The name of the data is `msleep`.  

```r
?msleep
```

```
## starting httpd help server ... done
```

2. Store these data into a new data frame `sleep`.  

```r
sleep <- msleep
```

3. What are the dimensions of this data frame (variables and observations)? How do you know?  The dimensions are 83 variables and 11 observations. I know this because I ran the dimensions using the code below. I also opened the file, which tells me the format (including rows and variables).  

Please show the *code* that you used to determine this below.  

```r
dim(sleep)
```

```
## [1] 83 11
```

4. Are there any NAs in the data? How did you determine this? Please show your code.   Yes, there are NAs in the data. I determined this by running glimpse, and noticed there were a few NAs in it.  

```r
glimpse(sleep)
```

```
## Rows: 83
## Columns: 11
## $ name         <chr> "Cheetah", "Owl monkey", "Mountain beaver", "Greater shor…
## $ genus        <chr> "Acinonyx", "Aotus", "Aplodontia", "Blarina", "Bos", "Bra…
## $ vore         <chr> "carni", "omni", "herbi", "omni", "herbi", "herbi", "carn…
## $ order        <chr> "Carnivora", "Primates", "Rodentia", "Soricomorpha", "Art…
## $ conservation <chr> "lc", NA, "nt", "lc", "domesticated", NA, "vu", NA, "dome…
## $ sleep_total  <dbl> 12.1, 17.0, 14.4, 14.9, 4.0, 14.4, 8.7, 7.0, 10.1, 3.0, 5…
## $ sleep_rem    <dbl> NA, 1.8, 2.4, 2.3, 0.7, 2.2, 1.4, NA, 2.9, NA, 0.6, 0.8, …
## $ sleep_cycle  <dbl> NA, NA, NA, 0.1333333, 0.6666667, 0.7666667, 0.3833333, N…
## $ awake        <dbl> 11.9, 7.0, 9.6, 9.1, 20.0, 9.6, 15.3, 17.0, 13.9, 21.0, 1…
## $ brainwt      <dbl> NA, 0.01550, NA, 0.00029, 0.42300, NA, NA, NA, 0.07000, 0…
## $ bodywt       <dbl> 50.000, 0.480, 1.350, 0.019, 600.000, 3.850, 20.490, 0.04…
```

5. Show a list of the column names is this data frame.

```r
colnames(sleep)
```

```
##  [1] "name"         "genus"        "vore"         "order"        "conservation"
##  [6] "sleep_total"  "sleep_rem"    "sleep_cycle"  "awake"        "brainwt"     
## [11] "bodywt"
```

6. How many herbivores are represented in the data?  
32  

```r
table(sleep$vore)
```

```
## 
##   carni   herbi insecti    omni 
##      19      32       5      20
```

7. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 19kg body weight and large as greater than or equal to 200kg body weight. Make two new dataframes (large and small) based on these parameters.

```r
large <- filter(sleep, bodywt>=200)
large_mammals <- data.frame(large)
large_mammals
```

```
##               name         genus  vore          order conservation sleep_total
## 1              Cow           Bos herbi   Artiodactyla domesticated         4.0
## 2   Asian elephant       Elephas herbi    Proboscidea           en         3.9
## 3            Horse         Equus herbi Perissodactyla domesticated         2.9
## 4          Giraffe       Giraffa herbi   Artiodactyla           cd         1.9
## 5      Pilot whale Globicephalus carni        Cetacea           cd         2.7
## 6 African elephant     Loxodonta herbi    Proboscidea           vu         3.3
## 7  Brazilian tapir       Tapirus herbi Perissodactyla           vu         4.4
##   sleep_rem sleep_cycle awake brainwt   bodywt
## 1       0.7   0.6666667 20.00   0.423  600.000
## 2        NA          NA 20.10   4.603 2547.000
## 3       0.6   1.0000000 21.10   0.655  521.000
## 4       0.4          NA 22.10      NA  899.995
## 5       0.1          NA 21.35      NA  800.000
## 6        NA          NA 20.70   5.712 6654.000
## 7       1.0   0.9000000 19.60   0.169  207.501
```


```r
small <- filter(sleep, bodywt<=19)
small_mammals <- data.frame(small)
small_mammals
```

```
##                              name         genus    vore           order
## 1                      Owl monkey         Aotus    omni        Primates
## 2                 Mountain beaver    Aplodontia   herbi        Rodentia
## 3      Greater short-tailed shrew       Blarina    omni    Soricomorpha
## 4                Three-toed sloth      Bradypus   herbi          Pilosa
## 5                    Vesper mouse       Calomys    <NA>        Rodentia
## 6                             Dog         Canis   carni       Carnivora
## 7                        Roe deer     Capreolus   herbi    Artiodactyla
## 8                      Guinea pig         Cavis   herbi        Rodentia
## 9                          Grivet Cercopithecus    omni        Primates
## 10                     Chinchilla    Chinchilla   herbi        Rodentia
## 11                Star-nosed mole     Condylura    omni    Soricomorpha
## 12      African giant pouched rat    Cricetomys    omni        Rodentia
## 13      Lesser short-tailed shrew     Cryptotis    omni    Soricomorpha
## 14           Long-nosed armadillo       Dasypus   carni       Cingulata
## 15                     Tree hyrax   Dendrohyrax   herbi      Hyracoidea
## 16         North American Opossum     Didelphis    omni Didelphimorphia
## 17                  Big brown bat     Eptesicus insecti      Chiroptera
## 18              European hedgehog     Erinaceus    omni  Erinaceomorpha
## 19                   Patas monkey  Erythrocebus    omni        Primates
## 20      Western american chipmunk      Eutamias   herbi        Rodentia
## 21                   Domestic cat         Felis   carni       Carnivora
## 22                         Galago        Galago    omni        Primates
## 23                     Gray hyrax   Heterohyrax   herbi      Hyracoidea
## 24                 Mongoose lemur         Lemur   herbi        Primates
## 25           Thick-tailed opposum    Lutreolina   carni Didelphimorphia
## 26                        Macaque        Macaca    omni        Primates
## 27               Mongolian gerbil      Meriones   herbi        Rodentia
## 28                 Golden hamster  Mesocricetus   herbi        Rodentia
## 29                          Vole       Microtus   herbi        Rodentia
## 30                    House mouse           Mus   herbi        Rodentia
## 31               Little brown bat        Myotis insecti      Chiroptera
## 32           Round-tailed muskrat      Neofiber   herbi        Rodentia
## 33                     Slow loris     Nyctibeus   carni        Primates
## 34                           Degu       Octodon   herbi        Rodentia
## 35     Northern grasshopper mouse     Onychomys   carni        Rodentia
## 36                         Rabbit   Oryctolagus   herbi      Lagomorpha
## 37                Desert hedgehog   Paraechinus    <NA>  Erinaceomorpha
## 38                          Potto  Perodicticus    omni        Primates
## 39                     Deer mouse    Peromyscus    <NA>        Rodentia
## 40                      Phalanger     Phalanger    <NA>   Diprotodontia
## 41                        Potoroo      Potorous   herbi   Diprotodontia
## 42                     Rock hyrax      Procavia    <NA>      Hyracoidea
## 43                 Laboratory rat        Rattus   herbi        Rodentia
## 44          African striped mouse     Rhabdomys    omni        Rodentia
## 45                Squirrel monkey       Saimiri    omni        Primates
## 46          Eastern american mole      Scalopus insecti    Soricomorpha
## 47                     Cotton rat      Sigmodon   herbi        Rodentia
## 48                       Mole rat        Spalax    <NA>        Rodentia
## 49         Arctic ground squirrel  Spermophilus   herbi        Rodentia
## 50 Thirteen-lined ground squirrel  Spermophilus   herbi        Rodentia
## 51 Golden-mantled ground squirrel  Spermophilus   herbi        Rodentia
## 52                     Musk shrew        Suncus    <NA>    Soricomorpha
## 53            Short-nosed echidna  Tachyglossus insecti     Monotremata
## 54      Eastern american chipmunk        Tamias   herbi        Rodentia
## 55                         Tenrec        Tenrec    omni    Afrosoricida
## 56                     Tree shrew        Tupaia    omni      Scandentia
## 57                          Genet       Genetta   carni       Carnivora
## 58                     Arctic fox        Vulpes   carni       Carnivora
## 59                        Red fox        Vulpes   carni       Carnivora
##    conservation sleep_total sleep_rem sleep_cycle awake brainwt bodywt
## 1          <NA>        17.0       1.8          NA   7.0 0.01550  0.480
## 2            nt        14.4       2.4          NA   9.6      NA  1.350
## 3            lc        14.9       2.3   0.1333333   9.1 0.00029  0.019
## 4          <NA>        14.4       2.2   0.7666667   9.6      NA  3.850
## 5          <NA>         7.0        NA          NA  17.0      NA  0.045
## 6  domesticated        10.1       2.9   0.3333333  13.9 0.07000 14.000
## 7            lc         3.0        NA          NA  21.0 0.09820 14.800
## 8  domesticated         9.4       0.8   0.2166667  14.6 0.00550  0.728
## 9            lc        10.0       0.7          NA  14.0      NA  4.750
## 10 domesticated        12.5       1.5   0.1166667  11.5 0.00640  0.420
## 11           lc        10.3       2.2          NA  13.7 0.00100  0.060
## 12         <NA>         8.3       2.0          NA  15.7 0.00660  1.000
## 13           lc         9.1       1.4   0.1500000  14.9 0.00014  0.005
## 14           lc        17.4       3.1   0.3833333   6.6 0.01080  3.500
## 15           lc         5.3       0.5          NA  18.7 0.01230  2.950
## 16           lc        18.0       4.9   0.3333333   6.0 0.00630  1.700
## 17           lc        19.7       3.9   0.1166667   4.3 0.00030  0.023
## 18           lc        10.1       3.5   0.2833333  13.9 0.00350  0.770
## 19           lc        10.9       1.1          NA  13.1 0.11500 10.000
## 20         <NA>        14.9        NA          NA   9.1      NA  0.071
## 21 domesticated        12.5       3.2   0.4166667  11.5 0.02560  3.300
## 22         <NA>         9.8       1.1   0.5500000  14.2 0.00500  0.200
## 23           lc         6.3       0.6          NA  17.7 0.01227  2.625
## 24           vu         9.5       0.9          NA  14.5      NA  1.670
## 25           lc        19.4       6.6          NA   4.6      NA  0.370
## 26         <NA>        10.1       1.2   0.7500000  13.9 0.17900  6.800
## 27           lc        14.2       1.9          NA   9.8      NA  0.053
## 28           en        14.3       3.1   0.2000000   9.7 0.00100  0.120
## 29         <NA>        12.8        NA          NA  11.2      NA  0.035
## 30           nt        12.5       1.4   0.1833333  11.5 0.00040  0.022
## 31         <NA>        19.9       2.0   0.2000000   4.1 0.00025  0.010
## 32           nt        14.6        NA          NA   9.4      NA  0.266
## 33         <NA>        11.0        NA          NA  13.0 0.01250  1.400
## 34           lc         7.7       0.9          NA  16.3      NA  0.210
## 35           lc        14.5        NA          NA   9.5      NA  0.028
## 36 domesticated         8.4       0.9   0.4166667  15.6 0.01210  2.500
## 37           lc        10.3       2.7          NA  13.7 0.00240  0.550
## 38           lc        11.0        NA          NA  13.0      NA  1.100
## 39         <NA>        11.5        NA          NA  12.5      NA  0.021
## 40         <NA>        13.7       1.8          NA  10.3 0.01140  1.620
## 41         <NA>        11.1       1.5          NA  12.9      NA  1.100
## 42           lc         5.4       0.5          NA  18.6 0.02100  3.600
## 43           lc        13.0       2.4   0.1833333  11.0 0.00190  0.320
## 44         <NA>         8.7        NA          NA  15.3      NA  0.044
## 45         <NA>         9.6       1.4          NA  14.4 0.02000  0.743
## 46           lc         8.4       2.1   0.1666667  15.6 0.00120  0.075
## 47         <NA>        11.3       1.1   0.1500000  12.7 0.00118  0.148
## 48         <NA>        10.6       2.4          NA  13.4 0.00300  0.122
## 49           lc        16.6        NA          NA   7.4 0.00570  0.920
## 50           lc        13.8       3.4   0.2166667  10.2 0.00400  0.101
## 51           lc        15.9       3.0          NA   8.1      NA  0.205
## 52         <NA>        12.8       2.0   0.1833333  11.2 0.00033  0.048
## 53         <NA>         8.6        NA          NA  15.4 0.02500  4.500
## 54         <NA>        15.8        NA          NA   8.2      NA  0.112
## 55         <NA>        15.6       2.3          NA   8.4 0.00260  0.900
## 56         <NA>         8.9       2.6   0.2333333  15.1 0.00250  0.104
## 57         <NA>         6.3       1.3          NA  17.7 0.01750  2.000
## 58         <NA>        12.5        NA          NA  11.5 0.04450  3.380
## 59         <NA>         9.8       2.4   0.3500000  14.2 0.05040  4.230
```


8. What is the mean weight for both the small and large mammals?

```r
s <- small_mammals$bodywt
mean(s)
```

```
## [1] 1.797847
```


```r
l <- large_mammals$bodywt
mean(l)
```

```
## [1] 1747.071
```

9. Using a similar approach as above, do large or small animals sleep longer on average?  The smaller animals sleep longer on average.    


```r
larger <- (large_mammals$sleep_total)
larger_mammals <- data.frame(larger)
larger_mammals
```

```
##   larger
## 1    4.0
## 2    3.9
## 3    2.9
## 4    1.9
## 5    2.7
## 6    3.3
## 7    4.4
```


```r
smaller <- small_mammals$sleep_total
smaller_mammals <- data.frame(smaller)
smaller_mammals
```

```
##    smaller
## 1     17.0
## 2     14.4
## 3     14.9
## 4     14.4
## 5      7.0
## 6     10.1
## 7      3.0
## 8      9.4
## 9     10.0
## 10    12.5
## 11    10.3
## 12     8.3
## 13     9.1
## 14    17.4
## 15     5.3
## 16    18.0
## 17    19.7
## 18    10.1
## 19    10.9
## 20    14.9
## 21    12.5
## 22     9.8
## 23     6.3
## 24     9.5
## 25    19.4
## 26    10.1
## 27    14.2
## 28    14.3
## 29    12.8
## 30    12.5
## 31    19.9
## 32    14.6
## 33    11.0
## 34     7.7
## 35    14.5
## 36     8.4
## 37    10.3
## 38    11.0
## 39    11.5
## 40    13.7
## 41    11.1
## 42     5.4
## 43    13.0
## 44     8.7
## 45     9.6
## 46     8.4
## 47    11.3
## 48    10.6
## 49    16.6
## 50    13.8
## 51    15.9
## 52    12.8
## 53     8.6
## 54    15.8
## 55    15.6
## 56     8.9
## 57     6.3
## 58    12.5
## 59     9.8
```


```r
larger_mammals_means <- colMeans(larger_mammals, na.rm=T)
larger_mammals_means
```

```
## larger 
##    3.3
```


```r
smaller_mammals_means <- colMeans(smaller_mammals, na.rm=T)
smaller_mammals_means
```

```
##  smaller 
## 11.78644
```


10. Which animal is the sleepiest among the entire dataframe?  The Little Brown Bat.  


```r
most_sleep <- max(sleep$sleep_total, na.rm=T)
most_sleep
```

```
## [1] 19.9
```


```r
sleeps <- data.frame(sleep$name, sleep$sleep_total)
sleeps
```

```
##                        sleep.name sleep.sleep_total
## 1                         Cheetah              12.1
## 2                      Owl monkey              17.0
## 3                 Mountain beaver              14.4
## 4      Greater short-tailed shrew              14.9
## 5                             Cow               4.0
## 6                Three-toed sloth              14.4
## 7               Northern fur seal               8.7
## 8                    Vesper mouse               7.0
## 9                             Dog              10.1
## 10                       Roe deer               3.0
## 11                           Goat               5.3
## 12                     Guinea pig               9.4
## 13                         Grivet              10.0
## 14                     Chinchilla              12.5
## 15                Star-nosed mole              10.3
## 16      African giant pouched rat               8.3
## 17      Lesser short-tailed shrew               9.1
## 18           Long-nosed armadillo              17.4
## 19                     Tree hyrax               5.3
## 20         North American Opossum              18.0
## 21                 Asian elephant               3.9
## 22                  Big brown bat              19.7
## 23                          Horse               2.9
## 24                         Donkey               3.1
## 25              European hedgehog              10.1
## 26                   Patas monkey              10.9
## 27      Western american chipmunk              14.9
## 28                   Domestic cat              12.5
## 29                         Galago               9.8
## 30                        Giraffe               1.9
## 31                    Pilot whale               2.7
## 32                      Gray seal               6.2
## 33                     Gray hyrax               6.3
## 34                          Human               8.0
## 35                 Mongoose lemur               9.5
## 36               African elephant               3.3
## 37           Thick-tailed opposum              19.4
## 38                        Macaque              10.1
## 39               Mongolian gerbil              14.2
## 40                 Golden hamster              14.3
## 41                          Vole               12.8
## 42                    House mouse              12.5
## 43               Little brown bat              19.9
## 44           Round-tailed muskrat              14.6
## 45                     Slow loris              11.0
## 46                           Degu               7.7
## 47     Northern grasshopper mouse              14.5
## 48                         Rabbit               8.4
## 49                          Sheep               3.8
## 50                     Chimpanzee               9.7
## 51                          Tiger              15.8
## 52                         Jaguar              10.4
## 53                           Lion              13.5
## 54                         Baboon               9.4
## 55                Desert hedgehog              10.3
## 56                          Potto              11.0
## 57                     Deer mouse              11.5
## 58                      Phalanger              13.7
## 59                   Caspian seal               3.5
## 60                Common porpoise               5.6
## 61                        Potoroo              11.1
## 62                Giant armadillo              18.1
## 63                     Rock hyrax               5.4
## 64                 Laboratory rat              13.0
## 65          African striped mouse               8.7
## 66                Squirrel monkey               9.6
## 67          Eastern american mole               8.4
## 68                     Cotton rat              11.3
## 69                       Mole rat              10.6
## 70         Arctic ground squirrel              16.6
## 71 Thirteen-lined ground squirrel              13.8
## 72 Golden-mantled ground squirrel              15.9
## 73                     Musk shrew              12.8
## 74                            Pig               9.1
## 75            Short-nosed echidna               8.6
## 76      Eastern american chipmunk              15.8
## 77                Brazilian tapir               4.4
## 78                         Tenrec              15.6
## 79                     Tree shrew               8.9
## 80           Bottle-nosed dolphin               5.2
## 81                          Genet               6.3
## 82                     Arctic fox              12.5
## 83                        Red fox               9.8
```

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
