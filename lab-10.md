Lab 10 - Grading the professor, Pt. 2
================
Alex Connolly
April 22

### Load packages and data

``` r
library(tidyverse) 
library(tidymodels)
library(openintro)
```

### Exercise 1

``` r
m_bty <- lm(score ~ bty_avg, data=evals)
summary(m_bty)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.9246 -0.3690  0.1420  0.3977  0.9309 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  3.88034    0.07614   50.96  < 2e-16 ***
    ## bty_avg      0.06664    0.01629    4.09 5.08e-05 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5348 on 461 degrees of freedom
    ## Multiple R-squared:  0.03502,    Adjusted R-squared:  0.03293 
    ## F-statistic: 16.73 on 1 and 461 DF,  p-value: 5.083e-05

y = .06664x + 3.88034 R2 is .03502, R2 adjusted is .03293

### Exercise 2

``` r
m_bty_gen <- lm(score ~ bty_avg + gender, data=evals)

summary(m_bty_gen)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg + gender, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8305 -0.3625  0.1055  0.4213  0.9314 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  3.74734    0.08466  44.266  < 2e-16 ***
    ## bty_avg      0.07416    0.01625   4.563 6.48e-06 ***
    ## gendermale   0.17239    0.05022   3.433 0.000652 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5287 on 460 degrees of freedom
    ## Multiple R-squared:  0.05912,    Adjusted R-squared:  0.05503 
    ## F-statistic: 14.45 on 2 and 460 DF,  p-value: 8.177e-07

Y= .07416x + .17239z + 3.74734 R2 is .05912, adjusted R2 is .05503.

### Exercise 3

Intercept = 3.7434, that would be the score if the beauty was 0 and the
gender was female .07416 is how much the score would go up for every 1
increase of beauty .17239 is the amount that male professors score
higher than females on average

### Exercise 4

The % of variability in score is 5.5503%

### Exercise 5

y= .07416x + (.17239+3.74734)

### Exercise 6

Males

### Exercise 7

Males will tend to have the higher scores

### Exercise 8

The adjusted R2 is better with m_bty_gen, implying that gender is
important in explaining the variability in evaluation scores when we
already have information on beauty score of the professor.

### Exercise 9

Yes, it raised a little, about .01

### Exercise 10

``` r
m_bty_rank <- lm(score ~ bty_avg + rank, data=evals)

summary(m_bty_rank)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg + rank, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8713 -0.3642  0.1489  0.4103  0.9525 
    ## 
    ## Coefficients:
    ##                  Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)       3.98155    0.09078  43.860  < 2e-16 ***
    ## bty_avg           0.06783    0.01655   4.098 4.92e-05 ***
    ## ranktenure track -0.16070    0.07395  -2.173   0.0303 *  
    ## ranktenured      -0.12623    0.06266  -2.014   0.0445 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5328 on 459 degrees of freedom
    ## Multiple R-squared:  0.04652,    Adjusted R-squared:  0.04029 
    ## F-statistic: 7.465 on 3 and 459 DF,  p-value: 6.88e-05

Tenured, Y = 3.98155 + .06783X -.12623Z Tenure Track, Y = 3.98155 +
.06783X = .16070Z Teaching Track, Y = 3.98155 + .06783X + 0Z

3.98155, if beauty score is 0 and on tenure track that will be their
score .06783, for every one point of beauty, the score will go up that
much -.16070, How much the score will decrease if on tenure track
-.12623, how much the score will decrease if tenured.

### Exercise 11

Probably? Cls did eval. Who cares how many people did the eval? That’s
just sample size I’d assume, which is useful, but not in predicting
scores. Unless some teachers are better at teaching to smaller classes?
But idk.

### Exercise 12

``` r
m_did_eval <- lm(score ~ cls_did_eval, data=evals)

summary(m_did_eval)
```

    ## 
    ## Call:
    ## lm(formula = score ~ cls_did_eval, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8545 -0.3595  0.1303  0.4269  0.8485 
    ## 
    ## Coefficients:
    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  4.1469347  0.0325682 127.331   <2e-16 ***
    ## cls_did_eval 0.0007589  0.0005616   1.351    0.177    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5434 on 461 degrees of freedom
    ## Multiple R-squared:  0.003946,   Adjusted R-squared:  0.001786 
    ## F-statistic: 1.827 on 1 and 461 DF,  p-value: 0.1772

Very small R squared!!

### Exercise 13

Similar to above, i would think cls_did_eval would be useless in this
case. The other two variables should give us all the necessary info for
whetehr people did the eval or not. Nothing else is gained here.

### Exercise 14

``` r
m_everything <- lm(score ~ rank + gender + age + cls_perc_eval + cls_students + cls_level + cls_profs + ethnicity + cls_credits + language+ bty_avg, data=evals)

summary(m_everything)
```

    ## 
    ## Call:
    ## lm(formula = score ~ rank + gender + age + cls_perc_eval + cls_students + 
    ##     cls_level + cls_profs + ethnicity + cls_credits + language + 
    ##     bty_avg, data = evals)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -1.84482 -0.31367  0.08559  0.35732  1.10105 
    ## 
    ## Coefficients:
    ##                         Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            3.5305036  0.2408200  14.660  < 2e-16 ***
    ## ranktenure track      -0.1070121  0.0820250  -1.305 0.192687    
    ## ranktenured           -0.0450371  0.0652185  -0.691 0.490199    
    ## gendermale             0.1786166  0.0515346   3.466 0.000579 ***
    ## age                   -0.0066498  0.0030830  -2.157 0.031542 *  
    ## cls_perc_eval          0.0056996  0.0015514   3.674 0.000268 ***
    ## cls_students           0.0004455  0.0003585   1.243 0.214596    
    ## cls_levelupper         0.0187105  0.0555833   0.337 0.736560    
    ## cls_profssingle       -0.0085751  0.0513527  -0.167 0.867458    
    ## ethnicitynot minority  0.1869649  0.0775329   2.411 0.016290 *  
    ## cls_creditsone credit  0.5087427  0.1170130   4.348  1.7e-05 ***
    ## languagenon-english   -0.1268254  0.1080358  -1.174 0.241048    
    ## bty_avg                0.0612651  0.0166755   3.674 0.000268 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.504 on 450 degrees of freedom
    ## Multiple R-squared:  0.1635, Adjusted R-squared:  0.1412 
    ## F-statistic: 7.331 on 12 and 450 DF,  p-value: 2.406e-12

### Exercise 15

The most significant were cls credit, beatuy, cls perc eval, and gender

``` r
m_best <- lm(score ~  gender + cls_perc_eval + cls_credits + bty_avg, data=evals)
summary(m_best)
```

    ## 
    ## Call:
    ## lm(formula = score ~ gender + cls_perc_eval + cls_credits + bty_avg, 
    ##     data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8421 -0.3384  0.1046  0.3841  1.0547 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)           3.375919   0.128466  26.279  < 2e-16 ***
    ## gendermale            0.176206   0.048679   3.620 0.000328 ***
    ## cls_perc_eval         0.004729   0.001451   3.258 0.001204 ** 
    ## cls_creditsone credit 0.457260   0.102579   4.458 1.04e-05 ***
    ## bty_avg               0.072030   0.015932   4.521 7.84e-06 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5107 on 458 degrees of freedom
    ## Multiple R-squared:  0.1259, Adjusted R-squared:  0.1182 
    ## F-statistic: 16.49 on 4 and 458 DF,  p-value: 1.25e-12

Y= 3.375919 + .176206g + .004p + .457260c + .072030b

### Exercise 16

.176206, this is how much score goes up when the teacher is male
.072030, this is how much score goes up when 1 beauty point is increased

### Exercise 17

A beautiful man who gives out credit for taking the evals will be rated
the highst.

### Exercise 18

Not necessarily. This could be the case, but there could be so many
confounds. I, for one, would try to replicated the study and see if it
could apply.
