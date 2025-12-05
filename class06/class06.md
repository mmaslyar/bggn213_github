# class06
Maddie Maslyar (PID: A69042845)

# R Functions Lab

I am submitting the grade function R script instead of answering the
“Generate Random Protein In Fasta Format” prompt because I was absent
from class.

Q1. Write a function grade() to determine an overall grade from a vector
of student homework assignment scores dropping the lowest single score.

``` r
# Function grade() determines grade from a vector of student homework assignment 
#scores dropping the lowest score.
grade <- function(x) {
  # Set missing homework values (NA) to zero
  x[is.na(x)] <- 0
  # Exclude the lowest homework score
  mean(x[-which.min(x)])
}
```

``` r
# Input example gradebook in csv format to test grade().
url <- "https://tinyurl.com/gradeinput"
gradebook <- read.csv(url, row.names=1)
```

Q2. Who is the top scoring student in the gradebook?

``` r
results <- apply(gradebook, 1, grade)
sort(results, decreasing = T)
```

    student-18  student-7  student-8 student-13  student-1 student-12 student-16 
         94.50      94.00      93.75      92.25      91.75      91.75      89.50 
     student-6  student-5 student-17  student-9 student-14 student-11  student-3 
         89.00      88.25      88.00      87.75      87.75      86.00      84.25 
     student-4 student-19 student-20  student-2 student-10 student-15 
         84.25      82.75      82.75      82.50      79.00      78.75 

**Student 18 is the top scoring student.**

Q3. Determine the most difficult homework assignment.

``` r
hw.mean <- apply(gradebook, 2, mean, na.rm = T)
hw.median <- apply(gradebook, 2, median, na.rm = T)
sort(hw.mean)
```

         hw3      hw2      hw5      hw1      hw4 
    80.80000 80.88889 83.42105 89.00000 89.63158 

``` r
sort(hw.median)
```

     hw2  hw3  hw5  hw4  hw1 
    72.5 76.5 78.0 88.0 89.0 

**HW3 and HW2 were the most difficult assignments. HW3 has the lowest
mean and HW2 has the lowest median.**
