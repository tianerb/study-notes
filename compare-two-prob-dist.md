***Question**: How to compare two probability distributions?*

[Wikipedia: Statistical_distance](https://en.wikipedia.org/wiki/Statistical_distance)

[Distances between probability measures](https://statweb.stanford.edu/~souravc/Lecture2.pdf)

[On choosing and bounding probability metrics](https://www.math.hmc.edu/~su/papers.dir/metrics.pdf) [(bak)](https://drive.google.com/file/d/1Dgo2er_lKY3_AIecxnLR_oaFT0KyOir0/view?usp=sharing)

[Numerical Recipes in C: 14.3 Are Two Distributions Different?](http://www.aip.de/groups/soe/local/numres/bookcpdf/c14-3.pdf) [(bak)](https://drive.google.com/file/d/1cxljFo7SKOesV1vp_xaHpeKjZhnSo_5i/view?usp=sharing)

### Measuring Distance
KL divergence is popular.

A lot of other metrics...

### Testing
Use [two sample Chi-squared test](https://www.itl.nist.gov/div898/software/dataplot/refman1/auxillar/chi2samp.htm) or [Kolmogorov-Smirnov test](https://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Smirnov_test), which are related to Chi-square distance and Kolmogorov metric.
> The accepted test for differences between binned distributions is the chi-square test. For continuous data as a function of a single variable, the most generally accepted test is the Kolmogorov-Smirnov test.

### Just compare multidimensionally
mean, median, variance, percentiles, counts in each bucket





