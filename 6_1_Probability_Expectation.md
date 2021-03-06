# Introduction_Statistical Inference
## Statistical inference defined

Statistical inference is the process of drawing formal conclusions from
data. 

In our class, we wil define formal statistical inference as settings where one wants to infer facts about a population using noisy
statistical data where uncertainty must be accounted for.

---

## Motivating example: who's going to win the election?

In every major election, pollsters would like to know, ahead of the
actual election, who's going to win. Here, the target of
estimation (the estimand) is clear, the percentage of people in 
a particular group (city, state, county, country or other electoral
grouping) who will vote for each candidate.

We can not poll everyone. Even if we could, some polled 
may change their vote by the time the election occurs.
How do we collect a reasonable subset of data and quantify the
uncertainty in the process to produce a good guess at who will win?

---

## Motivating example: is hormone replacement therapy effective? 

A large clinical trial (the Women’s Health Initiative) published results in 2002 that contradicted prior evidence on the efficacy of hormone replacement therapy for post menopausal women and suggested a negative impact of HRT for several key health outcomes. **Based on a statistically based protocol, the study was stopped early due an excess number of negative events.**

Here's there's two inferential problems. 

1. Is HRT effective?
2. How long should we continue the trial in the presence of contrary
evidence?

See WHI writing group paper JAMA 2002, Vol 288:321 - 333. for the paper and Steinkellner et al. Menopause 2012, Vol 19:616 621 for adiscussion of the long term impacts

---

## Motivating example: ECMO

In 1985 a group at a major neonatal intensive care center published the results of a trial comparing a standard treatment and a promising new extracorporeal membrane oxygenation treatment (ECMO) for newborn infants with severe respiratory failure. **Ethical considerations lead to a statistical randomization scheme whereby one infant received the control therapy, thereby opening the study to sample-size based criticisms.**

For a review and statistical discussion, see Royall Statistical Science 1991, Vol 6, No. 1, 52-88

---

## Summary

- These examples illustrate many of the difficulties of trying
to use data to create general conclusions about a population.
- Paramount among our concerns are:
  - Is the sample representative of the population that we'd like to draw inferences about?
  - Are there known and observed, known and unobserved or unknown and unobserved variables that contaminate our conclusions?
  - Is there systematic bias created by missing data or the design or conduct of the study?
  - What randomness exists in the data and how do we use or adjust for it? Here randomness can either be explicit via randomization
or random sampling, or implicit as the aggregation of many complex uknown processes.
  - Are we trying to estimate an underlying mechanistic model of phenomena under study?
- Statistical inference requires navigating the set of assumptions and
tools and subsequently thinking about how to draw conclusions from data.

--- 
## Example goals of inference

1. Estimate and quantify the uncertainty of an estimate of 
a population quantity (the proportion of people who will
  vote for a candidate).
2. Determine whether a population quantity 
  is a benchmark value ("is the treatment effective?").
3. Infer a mechanistic relationship when quantities are measured with
  noise ("What is the slope for Hooke's law?")
4. Determine the impact of a policy? ("If we reduce polution levels,
  will asthma rates decline?")


---
## Example tools of the trade 

1. Randomization: concerned with balancing unobserved variables that may confound inferences of interest
2. Random sampling: concerned with obtaining data that is representative 
of the population of interest
3. Sampling models: concerned with creating a model for the sampling
process, the most common is so called "iid".
4. Hypothesis testing: concerned with decision making in the presence of uncertainty
5. Confidence intervals: concerned with quantifying uncertainty in 
estimation
6. Probability models: a formal connection between the data and a population of interest. Often probability models are assumed or are
approximated.
7. Study design: the process of designing an experiment to minimize biases and variability.
8. Nonparametric bootstrapping: the process of using the data to,
  with minimal probability model assumptions, create inferences.
9. Permutation, randomization and exchangeability testing: the process 
of using data permutations to perform inferences.

---
## Different thinking about probability leads to different styles of inference

We won't spend too much time talking about this, but there are several different
styles of inference. Two broad categories that get discussed a lot are:

1. Frequency probability: is the long run proportion of
 times an event occurs in independent, identically distributed 
 repetitions.
2. Frequency inference: uses frequency interpretations of probabilities
to control error rates. Answers questions like "What should I decide
given my data controlling the long run proportion of mistakes I make at
a tolerable level."
3. Bayesian probability: is the probability calculus of beliefs, given that beliefs follow certain rules.
4. Bayesian inference: the use of Bayesian probability representation
of beliefs to perform inference. Answers questions like "Given my subjective beliefs and the objective information from the data, what
should I believe now?"

Data scientists tend to fall within shades of gray of these and various other schools of inference. 

---
## In this class

* In this class, we will primarily focus on basic sampling models, 
basic probability models and frequency style analyses
to create standard inferences. 
* Being data scientists,  we will also consider some inferential strategies that  rely heavily on the observed data, such as permutation testing
and bootstrapping.
* As probability modeling will be our starting point, we first build
up basic probability.

---
## Where to learn more on the topics not covered

1. Explicit use of random sampling in inferences: look in references
on "finite population statistics". Used heavily in polling and
sample surveys.
2. Explicit use of randomization in inferences: look in references
on "causal inference" especially in clinical trials.
3. Bayesian probability and Bayesian statistics: look for basic itroductory books (there are many).
4. Missing data: well covered in biostatistics and econometric
references; look for references to "multiple imputation", a popular tool for
addressing missing data.
5. Study design: consider looking in the subject matter area that
  you are interested in; some examples with rich histories in design:
  1. The epidemiological literature is very focused on using study design to investigate public health.
  2. The classical development of study design in agriculture broadly covers design and design principles.
  3. The industrial quality control literature covers design thoroughly.
 
# Probability

## Notation

- The **sample space**, $\Omega$, is the collection of possible outcomes of an experiment
  - Example: die roll $\Omega = \{1,2,3,4,5,6\}$
- An **event**, say $E$, is a subset of $\Omega$ 
  - Example: die roll is even $E = \{2,4,6\}$
- An **elementary** or **simple** event is a particular result
  of an experiment
  - Example: die roll is a four, $\omega = 4$
- $\emptyset$ is called the **null event** or the **empty set**

---

## Interpretation of set operations

Normal set operations have particular interpretations in this setting

1. $\omega \in E$ implies that $E$ occurs when $\omega$ occurs
2. $\omega \not\in E$ implies that $E$ does not occur when $\omega$ occurs
3. $E \subset F$ implies that the occurrence of $E$ implies the occurrence of $F$
4. $E \cap F$  implies the event that both $E$ and $F$ occur
5. $E \cup F$ implies the event that at least one of $E$ or $F$ occur
6. $E \cap F=\emptyset$ means that $E$ and $F$ are **mutually exclusive**, or cannot both occur
7. $E^c$ or $\bar E$ is the event that $E$ does not occur

---

## Probability

A **probability measure**, $P$, is a function from the collection of possible events so that the following hold

1. For an event $E\subset \Omega$, $0 \leq P(E) \leq 1$
2. $P(\Omega) = 1$
3. If $E_1$ and $E_2$ are mutually exclusive events
  $P(E_1 \cup E_2) = P(E_1) + P(E_2)$.

Part 3 of the definition implies **finite additivity**

$$
P(\cup_{i=1}^n A_i) = \sum_{i=1}^n P(A_i)
$$
where the $\{A_i\}$ are mutually exclusive. (Note a more general version of
additivity is used in advanced classes.)


---


## Example consequences

- $P(\emptyset) = 0$
- $P(E) = 1 - P(E^c)$
- $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
- if $A \subset B$ then $P(A) \leq P(B)$
- $P\left(A \cup B\right) = 1 - P(A^c \cap B^c)$
- $P(A \cap B^c) = P(A) - P(A \cap B)$
- $P(\cup_{i=1}^n E_i) \leq \sum_{i=1}^n P(E_i)$
- $P(\cup_{i=1}^n E_i) \geq \max_i P(E_i)$

---

## Example

The National Sleep Foundation ([www.sleepfoundation.org](http://www.sleepfoundation.org/)) reports that around 3% of the American population has sleep apnea. They also report that around 10% of the North American and European population has restless leg syndrome. Does this imply that 13% of people will have at least one sleep problems of these sorts?

---

## Example continued

Answer: No, the events are not mutually exclusive. To elaborate let:

$$
\begin{eqnarray*}
    A_1 & = & \{\mbox{Person has sleep apnea}\} \\
    A_2 & = & \{\mbox{Person has RLS}\} 
  \end{eqnarray*}
$$

Then 

$$
\begin{eqnarray*}
    P(A_1 \cup A_2 ) & = & P(A_1) + P(A_2) - P(A_1 \cap A_2) \\
   & = & 0.13 - \mbox{Probability of having both}
  \end{eqnarray*}
$$
Likely, some fraction of the population has both.

---

## Random variables

- A **random variable** is a numerical outcome of an experiment.
- The random variables that we study will come in two varieties,
  **discrete** or **continuous**.
- Discrete random variable are random variables that take on only a
countable number of possibilities.
  * $P(X = k)$
- Continuous random variable can take any value on the real line or some subset of the real line.
  * $P(X \in A)$

---

## Examples of variables that can be thought of as random variables

- The $(0-1)$ outcome of the flip of a coin
- The outcome from the roll of a die
- The BMI of a subject four years after a baseline measurement
- The hypertension status of a subject randomly drawn from a population

---

## PMF

A probability mass function evaluated at a value corresponds to the
probability that a random variable takes that value. To be a valid
pmf a function, $p$, must satisfy

  1. $p(x) \geq 0$ for all $x$
  2. $\sum_{x} p(x) = 1$

The sum is taken over all of the possible values for $x$.

---

## Example

Let $X$ be the result of a coin flip where $X=0$ represents
tails and $X = 1$ represents heads.
$$
p(x) = (1/2)^{x} (1/2)^{1-x} ~~\mbox{ for }~~x = 0,1
$$
Suppose that we do not know whether or not the coin is fair; Let
$\theta$ be the probability of a head expressed as a proportion
(between 0 and 1).
$$
p(x) = \theta^{x} (1 - \theta)^{1-x} ~~\mbox{ for }~~x = 0,1
$$

---

## PDF

A probability density function (pdf), is a function associated with
a continuous random variable 

  *Areas under pdfs correspond to probabilities for that random variable*

To be a valid pdf, a function $f$ must satisfy

1. $f(x) \geq 0$ for all $x$

2. The area under $f(x)$ is one.

---
## Example

Suppose that the proportion of help calls that get addressed in
a random day by a help line is given by
$$
f(x) = \left\{\begin{array}{ll}
    2 x & \mbox{ for } 1 > x > 0 \\
    0                 & \mbox{ otherwise} 
\end{array} \right. 
$$

Is this a mathematically valid density?

---


```r
x <- c(-0.5, 0, 1, 1, 1.5)
y <- c(0, 0, 2, 0, 0)
plot(x, y, lwd = 3, frame = FALSE, type = "l")
```

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1.png) 


---

## Example continued

What is the probability that 75% or fewer of calls get addressed?

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2.png) 


---

```r
1.5 * 0.75/2
```

```
## [1] 0.5625
```

```r
pbeta(0.75, 2, 1)
```

```
## [1] 0.5625
```

---

## CDF and survival function

- The **cumulative distribution function** (CDF) of a random variable $X$ is defined as the function 
$$
F(x) = P(X \leq x)
$$
- This definition applies regardless of whether $X$ is discrete or continuous.
- The **survival function** of a random variable $X$ is defined as
$$
S(x) = P(X > x)
$$
- Notice that $S(x) = 1 - F(x)$
- For continuous random variables, the PDF is the derivative of the CDF

---

## Example

What are the survival function and CDF from the density considered before?

For $1 \geq x \geq 0$
$$
F(x) = P(X \leq x) = \frac{1}{2} Base \times Height = \frac{1}{2} (x) \times (2 x) = x^2
$$

$$
S(x) = 1 - x^2
$$


```r
pbeta(c(0.4, 0.5, 0.6), 2, 1)
```

```
## [1] 0.16 0.25 0.36
```


---

## Quantiles

- The  $\alpha^{th}$ **quantile** of a distribution with distribution function $F$ is the point $x_\alpha$ so that
$$
F(x_\alpha) = \alpha
$$
- A **percentile** is simply a quantile with $\alpha$ expressed as a percent
- The **median** is the $50^{th}$ percentile

---
## Example
- We want to solve $0.5 = F(x) = x^2$
- Resulting in the solution 

```r
sqrt(0.5)
```

```
## [1] 0.7071
```

- Therefore, about 0.7071 of calls being answered on a random day is the median.
- R can approximate quantiles for you for common distributions


```r
qbeta(0.5, 2, 1)
```

```
## [1] 0.7071
```


---

## Summary

- You might be wondering at this point "I've heard of a median before, it didn't require integration. Where's the data?"
- We're referring to are **population quantities**. Therefore, the median being
  discussed is the **population median**.
- A probability model connects the data to the population using assumptions.
- Therefore the median we're discussing is the **estimand**, the sample median will be the **estimator**

# Expectations
## Expected values

- The **expected value** or **mean** of a random variable is the center of its distribution
- For discrete random variable $X$ with PMF $p(x)$, it is defined as follows
    $$
    E[X] = \sum_x xp(x).
    $$
    where the sum is taken over the possible values of $x$
- $E[X]$ represents the center of mass of a collection of locations and weights, $\{x, p(x)\}$

---

## Example
### Find the center of mass of the bars
![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1.png) 


---
## Using manipulate
```
library(manipulate)
myHist <- function(mu){
  hist(galton$child,col="blue",breaks=100)
  lines(c(mu, mu), c(0, 150),col="red",lwd=5)
  mse <- mean((galton$child - mu)^2)
  text(63, 150, paste("mu = ", mu))
  text(63, 140, paste("Imbalance = ", round(mse, 2)))
}
manipulate(myHist(mu), mu = slider(62, 74, step = 0.5))
```

---
## The center of mass is the empirical mean

```r
hist(galton$child, col = "blue", breaks = 100)
meanChild <- mean(galton$child)
lines(rep(meanChild, 100), seq(0, 150, length = 100), col = "red", lwd = 5)
```

![plot of chunk lsm](assets/fig/lsm.png) 


---
## Example

- Suppose a coin is flipped and $X$ is declared $0$ or $1$ corresponding to a head or a tail, respectively
- What is the expected value of $X$? 
    $$
    E[X] = .5 \times 0 + .5 \times 1 = .5
    $$
- Note, if thought about geometrically, this answer is obvious; if two equal weights are spaced at 0 and 1, the center of mass will be $.5$

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2.png) 

---

## Example

- Suppose that a die is rolled and $X$ is the number face up
- What is the expected value of $X$?
    $$
    E[X] = 1 \times \frac{1}{6} + 2 \times \frac{1}{6} +
    3 \times \frac{1}{6} + 4 \times \frac{1}{6} +
    5 \times \frac{1}{6} + 6 \times \frac{1}{6} = 3.5
    $$
- Again, the geometric argument makes this answer obvious without calculation.

---

## Continuous random variables

- For a continuous random variable, $X$, with density, $f$, the expected
    value is defined as follows
    $$
    E[X] = \mbox{the area under the function}~~~ t f(t)
    $$
- This definition borrows from the definition of center of mass for a continuous body

---

## Example

- Consider a density where $f(x) = 1$ for $x$ between zero and one
- (Is this a valid density?)
- Suppose that $X$ follows this density; what is its expected value?  
![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3.png) 


---

## Rules about expected values

- The expected value is a linear operator 
- If $a$ and $b$ are not random and $X$ and $Y$ are two random variables then
  - $E[aX + b] = a E[X] + b$
  - $E[X + Y] = E[X] + E[Y]$

---

## Example

- You flip a coin, $X$ and simulate a uniform random number $Y$, what is the expected value of their sum? 
    $$
    E[X + Y] = E[X] + E[Y] = .5 + .5 = 1
    $$ 
- Another example, you roll a die twice. What is the expected value of the average? 
- Let $X_1$ and $X_2$ be the results of the two rolls
    $$
    E[(X_1 + X_2) / 2] = \frac{1}{2}(E[X_1] + E[X_2])
    = \frac{1}{2}(3.5 + 3.5) = 3.5
    $$

---

## Example

1. Let $X_i$ for $i=1,\ldots,n$ be a collection of random variables, each from a distribution with mean $\mu$
2. Calculate the expected value of the sample average of the $X_i$
$$
  \begin{eqnarray*}
    E\left[ \frac{1}{n}\sum_{i=1}^n X_i\right]
    & = & \frac{1}{n} E\left[\sum_{i=1}^n X_i\right] \\
    & = & \frac{1}{n} \sum_{i=1}^n E\left[X_i\right] \\
    & = & \frac{1}{n} \sum_{i=1}^n \mu =  \mu.
  \end{eqnarray*}
$$

---

## Remark

- Therefore, the expected value of the **sample mean** is the population mean that it's trying to estimate
- When the expected value of an estimator is what its trying to estimate, we say that the estimator is **unbiased**

---

## The variance

- The variance of a random variable is a measure of *spread*
- If $X$ is a random variable with mean $\mu$, the variance of $X$ is defined as

$$
Var(X) = E[(X - \mu)^2]
$$
    
the expected (squared) distance from the mean
- Densities with a higher variance are more spread out than densities with a lower variance

---

- Convenient computational form
$$
Var(X) = E[X^2] - E[X]^2
$$
- If $a$ is constant then $Var(aX) = a^2 Var(X)$
- The square root of the variance is called the **standard deviation**
- The standard deviation has the same units as $X$

---

## Example

- What's the sample variance from the result of a toss of a die? 

  - $E[X] = 3.5$ 
  - $E[X^2] = 1 ^ 2 \times \frac{1}{6} + 2 ^ 2 \times \frac{1}{6} + 3 ^ 2 \times \frac{1}{6} + 4 ^ 2 \times \frac{1}{6} + 5 ^ 2 \times \frac{1}{6} + 6 ^ 2 \times \frac{1}{6} = 15.17$ 

- $Var(X) = E[X^2] - E[X]^2 \approx 2.92$

---

## Example

- What's the sample variance from the result of the toss of a coin with probability of heads (1) of $p$? 

  - $E[X] = 0 \times (1 - p) + 1 \times p = p$
  - $E[X^2] = E[X] = p$ 

- $Var(X) = E[X^2] - E[X]^2 = p - p^2 = p(1 - p)$

---

## Interpreting variances

- Chebyshev's inequality is useful for interpreting variances
- This inequality states that
$$
P(|X - \mu| \geq k\sigma) \leq \frac{1}{k^2}
$$
- For example, the probability that a random variable lies beyond $k$ standard deviations from its mean is less than $1/k^2$
$$
\begin{eqnarray*}
    2\sigma & \rightarrow & 25\% \\
    3\sigma & \rightarrow & 11\% \\
    4\sigma & \rightarrow &  6\% 
\end{eqnarray*}
$$
- Note this is only a bound; the actual probability might be quite a bit smaller

---

## Example

- IQs are often said to be distributed with a mean of $100$ and a sd of $15$
- What is the probability of a randomly drawn person having an IQ higher than $160$ or below $40$?
- Thus we want to know the probability of a person being more than $4$ standard deviations from the mean
- Thus Chebyshev's inequality suggests that this will be no larger than 6\%
- IQs distributions are often cited as being bell shaped, in which case this bound is very conservative
- The probability of a random draw from a bell curve being $4$ standard deviations from the mean is on the order of $10^{-5}$ (one thousandth of one percent)

---

## Example

- A former buzz phrase in industrial quality control is Motorola's "Six Sigma" whereby businesses are suggested to control extreme events or rare defective parts
- Chebyshev's inequality states that the probability of a "Six Sigma" event is less than $1/6^2 \approx 3\%$
- If a bell curve is assumed, the probability of a "six sigma" event is on the order of $10^{-9}$ (one ten millionth of a percent)

## Independent events

- Two events $A$ and $B$ are **independent** if $$P(A \cap B) = P(A)P(B)$$
- Two random variables, $X$ and $Y$ are independent if for any two sets $A$ and $B$ $$P([X \in A] \cap [Y \in B]) = P(X\in A)P(Y\in B)$$
- If $A$ is independent of $B$ then 

  - $A^c$ is independent of $B$ 
  - $A$ is independent of $B^c$
  - $A^c$ is independent of $B^c$


---

## Example

- What is the probability of getting two consecutive heads?
- $A = \{\mbox{Head on flip 1}\}$ ~ $P(A) = .5$
- $B = \{\mbox{Head on flip 2}\}$ ~ $P(B) = .5$
- $A \cap B = \{\mbox{Head on flips 1 and 2}\}$
- $P(A \cap B) = P(A)P(B) = .5 \times .5 = .25$ 

---

## Example

- Volume 309 of Science reports on a physician who was on trial for expert testimony in a criminal trial
- Based on an estimated prevalence of sudden infant death syndrome of $1$ out of $8,543$, Dr Meadow testified that that the probability of a mother having two children with SIDS was $\left(\frac{1}{8,543}\right)^2$
- The mother on trial was convicted of murder

---

## Example: continued

- For the purposes of this class, the principal mistake was to *assume* that the probabilities of having SIDs within a family are independent
- That is, $P(A_1 \cap A_2)$ is not necessarily equal to $P(A_1)P(A_2)$
- Biological processes that have a believed genetic or familiar environmental component, of course, tend to be dependent within families
- (There are many other statistical points of discussion for this case.)

---

## Useful fact

We will use the following fact extensively in this class:

*If a collection of random variables $X_1, X_2, \ldots, X_n$ are independent, then their joint distribution is the product of their individual densities or mass functions*

*That is, if $f_i$ is the density for random variable $X_i$ we have that*
$$
f(x_1,\ldots, x_n) = \prod_{i=1}^n f_i(x_i)
$$

---

## IID random variables

- Random variables are said to be iid if they are independent and identically distributed
- iid random variables are the default model for random samples
- Many of the important theories of statistics are founded on assuming that variables are iid


---

## Example

- Suppose that we flip a biased coin with success probability $p$ $n$ times, what is the join density of the collection of outcomes?
- These random variables are iid with densities $p^{x_i} (1 - p)^{1-x_i}$ 
- Therefore
  $$
  f(x_1,\ldots,x_n) = \prod_{i=1}^n p^{x_i} (1 - p)^{1-x_i} = p^{\sum x_i} (1 - p)^{n - \sum x_i}
  $$

---

## Correlation

- The **covariance** between two random variables $X$ and $Y$ is defined as 
$$
Cov(X, Y) = E[(X - \mu_x)(Y - \mu_y)] = E[X Y] - E[X]E[Y]
$$
- The following are useful facts about covariance
  1. $Cov(X, Y) = Cov(Y, X)$
  2. $Cov(X, Y)$ can be negative or positive
  3. $|Cov(X, Y)| \leq \sqrt{Var(X) Var(y)}$

---

## Correlation

- The **correlation** between $X$ and $Y$ is 
$$
Cor(X, Y) = Cov(X, Y) / \sqrt{Var(X) Var(y)}
$$

  1. $-1 \leq Cor(X, Y) \leq 1$
  2. $Cor(X, Y) = \pm 1$ if and only if $X = a + bY$ for some constants $a$ and $b$
  3. $Cor(X, Y)$ is unitless
  4. $X$ and $Y$ are **uncorrelated** if $Cor(X, Y) = 0$ 
  5.  $X$ and $Y$ are more positively correlated, the closer $Cor(X,Y)$ is to $1$
  6.  $X$ and $Y$ are more negatively correlated, the closer $Cor(X,Y)$ is to $-1$

---

## Some useful results

- Let $\{X_i\}_{i=1}^n$ be a collection of random variables
  - When the $\{X_i\}$ are uncorrelated $$Var\left(\sum_{i=1}^n a_i X_i + b\right) = \sum_{i=1}^n a_i^2 Var(X_i)$$  

- A commonly used subcase from these properties is that *if a collection of random variables $\{X_i\}$ are uncorrelated*, then the variance of the sum is the sum of the variances
$$
Var\left(\sum_{i=1}^n X_i \right) = \sum_{i=1}^n Var(X_i)
$$
- Therefore, it is sums of variances that tend to be useful, not sums of standard deviations; that is, the standard deviation of the sum of bunch of independent random variables is the square root of the sum of the variances, not the sum of the standard deviations

---

## The sample mean

Suppose $X_i$ are iid with variance $\sigma^2$

$$
\begin{eqnarray*}
    Var(\bar X) & = & Var \left( \frac{1}{n}\sum_{i=1}^n X_i \right)\\ \\
    & = & \frac{1}{n^2} Var\left(\sum_{i=1}^n X_i \right)\\ \\
    & = & \frac{1}{n^2} \sum_{i=1}^n Var(X_i) \\ \\
    & = & \frac{1}{n^2} \times n\sigma^2 \\ \\
    & = & \frac{\sigma^2}{n}
  \end{eqnarray*}
$$

---

## Some comments

- When $X_i$ are independent with a common variance $Var(\bar X) = \frac{\sigma^2}{n}$
- $\sigma/\sqrt{n}$ is called *the standard error* of the sample mean
- The standard error of the sample mean is the standard deviation of the distribution of the sample mean
- $\sigma$ is the standard deviation of the distribution of a single observation
- Easy way to remember, the sample mean has to be less variable than a single observation, therefore its standard deviation is divided by a $\sqrt{n}$

---

## The sample variance
- The **sample variance** is defined as 
$$
S^2 =   \frac{\sum_{i=1}^n (X_i - \bar X)^2}{n-1} 
$$
- The sample variance is an estimator of $\sigma^2$
- The numerator has a version that's quicker for calculation
$$
\sum_{i=1}^n (X_i - \bar X)^2 = \sum_{i=1}^n X_i^2 - n \bar X^2
$$
- The sample variance is (nearly) the mean of the squared deviations from the mean

---

## The sample variance is unbiased

$$
  \begin{eqnarray*}
    E\left[\sum_{i=1}^n (X_i - \bar X)^2\right] & = & \sum_{i=1}^n E\left[X_i^2\right] - n E\left[\bar X^2\right] \\ \\
    & = & \sum_{i=1}^n \left\{Var(X_i) + \mu^2\right\} - n \left\{Var(\bar X) + \mu^2\right\} \\ \\
    & = & \sum_{i=1}^n \left\{\sigma^2 + \mu^2\right\} - n \left\{\sigma^2 / n + \mu^2\right\} \\ \\
    & = & n \sigma^2 + n \mu ^ 2 - \sigma^2 - n \mu^2 \\ \\
    & = & (n - 1) \sigma^2
  \end{eqnarray*}
$$

---

## Hoping to avoid some confusion

- Suppose $X_i$ are iid with mean $\mu$ and variance $\sigma^2$
- $S^2$ estimates $\sigma^2$
- The calculation of $S^2$ involves dividing by $n-1$
- $S / \sqrt{n}$ estimates $\sigma / \sqrt{n}$ the standard error of the mean
- $S / \sqrt{n}$ is called the sample standard error (of the mean)

---
## Example

```r
data(father.son)
x <- father.son$sheight
n <- length(x)
```


---
![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2.png) 


```r
round(c(sum((x - mean(x))^2)/(n - 1), var(x), var(x)/n, sd(x), sd(x)/sqrt(n)), 
    2)
```

```
## [1] 7.92 7.92 0.01 2.81 0.09
```

## Conditional probability, motivation

- The probability of getting a one when rolling a (standard) die
  is usually assumed to be one sixth
- Suppose you were given the extra information that the die roll
  was an odd number (hence 1, 3 or 5)
- *conditional on this new information*, the probability of a
  one is now one third

---

## Conditional probability, definition

- Let $B$ be an event so that $P(B) > 0$
- Then the conditional probability of an event $A$ given that $B$ has occurred is
  $$
  P(A ~|~ B) = \frac{P(A \cap B)}{P(B)}
  $$
- Notice that if $A$ and $B$ are independent, then
  $$
  P(A ~|~ B) = \frac{P(A) P(B)}{P(B)} = P(A)
  $$

---

## Example

- Consider our die roll example
- $B = \{1, 3, 5\}$
- $A = \{1\}$
$$
  \begin{eqnarray*}
P(\mbox{one given that roll is odd})  & = & P(A ~|~ B) \\ \\
  & = & \frac{P(A \cap B)}{P(B)} \\ \\
  & = & \frac{P(A)}{P(B)} \\ \\ 
  & = & \frac{1/6}{3/6} = \frac{1}{3}
  \end{eqnarray*}
$$



---

## Bayes' rule

$$
P(B ~|~ A) = \frac{P(A ~|~ B) P(B)}{P(A ~|~ B) P(B) + P(A ~|~ B^c)P(B^c)}.
$$
  

---

## Diagnostic tests

- Let $+$ and $-$ be the events that the result of a diagnostic test is positive or negative respectively
- Let $D$ and $D^c$ be the event that the subject of the test has or does not have the disease respectively 
- The **sensitivity** is the probability that the test is positive given that the subject actually has the disease, $P(+ ~|~ D)$
- The **specificity** is the probability that the test is negative given that the subject does not have the disease, $P(- ~|~ D^c)$

---

## More definitions

- The **positive predictive value** is the probability that the subject has the  disease given that the test is positive, $P(D ~|~ +)$
- The **negative predictive value** is the probability that the subject does not have the disease given that the test is negative, $P(D^c ~|~ -)$
- The **prevalence of the disease** is the marginal probability of disease, $P(D)$

---

## More definitions

- The **diagnostic likelihood ratio of a positive test**, labeled $DLR_+$, is $P(+ ~|~ D) / P(+ ~|~ D^c)$, which is the $$sensitivity / (1 - specificity)$$
- The **diagnostic likelihood ratio of a negative test**, labeled $DLR_-$, is $P(- ~|~ D) / P(- ~|~ D^c)$, which is the $$(1 - sensitivity) / specificity$$

---

## Example

- A study comparing the efficacy of HIV tests, reports on an experiment which concluded that HIV antibody tests have a sensitivity of 99.7% and a specificity of 98.5%
- Suppose that a subject, from a population with a .1% prevalence of HIV, receives a positive test result. What is the probability that this subject has HIV?
- Mathematically, we want $P(D ~|~ +)$ given the sensitivity, $P(+ ~|~ D) = .997$, the specificity, $P(- ~|~ D^c) =.985$, and the prevalence $P(D) = .001$

---

## Using Bayes' formula

$$
\begin{eqnarray*}
  P(D ~|~ +) & = &\frac{P(+~|~D)P(D)}{P(+~|~D)P(D) + P(+~|~D^c)P(D^c)}\\ \\
 & = & \frac{P(+~|~D)P(D)}{P(+~|~D)P(D) + \{1-P(-~|~D^c)\}\{1 - P(D)\}} \\ \\
 & = & \frac{.997\times .001}{.997 \times .001 + .015 \times .999}\\ \\
 & = & .062
\end{eqnarray*}
$$

- In this population a positive test result only suggests a 6% probability that the subject has the disease 
- (The positive predictive value is 6% for this test)

---

## More on this example

- The low positive predictive value is due to low prevalence of disease and the somewhat modest specificity
- Suppose it was known that the subject was an intravenous drug user and routinely had intercourse with an HIV infected partner
- Notice that the evidence implied by a positive test result does not change because of the prevalence of disease in the subject's population, only our interpretation of that evidence changes

---

## Likelihood ratios

- Using Bayes rule, we have
  $$
  P(D ~|~ +) = \frac{P(+~|~D)P(D)}{P(+~|~D)P(D) + P(+~|~D^c)P(D^c)} 
  $$
  and
  $$
  P(D^c ~|~ +) = \frac{P(+~|~D^c)P(D^c)}{P(+~|~D)P(D) + P(+~|~D^c)P(D^c)}.
  $$

---

## Likelihood ratios

- Therefore
$$
\frac{P(D ~|~ +)}{P(D^c ~|~ +)} = \frac{P(+~|~D)}{P(+~|~D^c)}\times \frac{P(D)}{P(D^c)}
$$
ie
$$
\mbox{post-test odds of }D = DLR_+\times\mbox{pre-test odds of }D
$$
- Similarly, $DLR_-$ relates the decrease in the odds of the
  disease after a negative test result to the odds of disease prior to
  the test.

---

## HIV example revisited

- Suppose a subject has a positive HIV test
- $DLR_+ = .997 / (1 - .985) \approx 66$
- The result of the positive test is that the odds of disease is now 66 times the pretest odds
- Or, equivalently, the hypothesis of disease is 66 times more supported by the data than the hypothesis of no disease

---

## HIV example revisited

- Suppose that a subject has a negative test result 
- $DLR_- = (1 - .997) / .985  \approx .003$
- Therefore, the post-test odds of disease is now $.3\%$ of the pretest odds given the negative test.
- Or, the hypothesis of disease is supported $.003$ times that of the hypothesis of absence of disease given the negative test result



