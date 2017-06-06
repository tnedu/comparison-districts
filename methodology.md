### Methodology

This document outlines TDoE's procedure for identifying similar districts. Begin with district profile data, available in data/achievement_profile_data_2015_2016.csv or [here](http://www.tn.gov/education/topic/data-downloads).

1) Select the following information from the data:

* Student Enrollment
* Percent Black
* Percent Hispanic
* Percent Native American
* Percent Economically Disadvantaged
* Percent Students with Disabilities
* Percent English Learners
* Per-Pupil Expenditures from Local Sources
* CORE Region
* Grade Span

2) Clean data

* Drop Systems 0 (State), 960, 961, 963, 964, 970 (Blind, Alvin C. York, Deaf, DCS)
* Impute 0 for missing

3) Using the Grade Span variable, create an indicator for districts serving only grades K-8. Using the CORE Region variable, create 8 indicator variables, one corresponding to each region.

4) Standardize non-indicator characteristic variables by subtracting each variable by its mean and dividing by its standard deviation. This puts variables on a common scale so that we can compare magnitudes of difference across district characteristics.

5) Calculate a similarity score between each district and all others. The similarity score between district *i* and district *j* is the following:

$Similarity_{ij} = ((Enrollment_i - Enrollment_j)^2 + (Percent Black_i - Percent Black_j)^2  + ... + (Grade Span_i - Grade Span_j)^2)^{1/2}$

A similarity score between two identical districts is zero, and a higher similarity score signifies more dissimilar districts. Thus, a district *i*'s most similar districts are those that have the lowest similarity scores.
