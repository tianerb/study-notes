*Notes for* [colah's blog : Visual Information Theory (2015-09)](http://colah.github.io/posts/2015-09-Visual-Information/)
### Visualizing Probability Distributions
### Aside: Simpson's Paradox
One thing to keep in mind when designing an experiment/ABtest.

[vector interpretation](https://en.wikipedia.org/wiki/Simpson%27s_paradox#Vector_interpretation)
### Codes
### Variable-Length Codes
Entropy = Optimal Average Code Length = $\sum_xp(x)*\text{codeLength}(x)$
### The Space of Codewords
**prefix property / prefix codes**

Suppose we already decoded previous codes, then as long as every code word is not prefix of other code word, we can just decode the first code word starting from the current digit, then continue. This way, the codes can be uniquely decoded.

<img src="http://colah.github.io/posts/2015-09-Visual-Information/img/CodeSpaceUsed.png"  width="300px"/>

### Optimal Encodings
$e^{-x} = \int_x^{\infty} e^{-t}dt$


<img src="http://colah.github.io/posts/2015-09-Visual-Information/img/code-cost.png"  width="400px"/>

Average Length Contribution = p(x) * codeLength(x)

Codeword Cost = 2^{-codeLength}

Optimal Encoding: 
> Distribute our budget in proportion to how common an event is. So, if one event happens 50% of the time, we spend 50% of our budget buying a short codeword for it. But if an event only happens 1% of the time, we only spend 1% of our budget, because we don’t care very much if the codeword is long

<img src="http://colah.github.io/posts/2015-09-Visual-Information/img/code-auction-balanced-noderivs.png"  width="400px"/>

### [Entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory))
$\frac{1}{2^{L(x)}} = \text{cost}(x)$

optimal encoding: $\text{cost}(x) = p(x)$

$L(x) = \log_2\frac{1}{\text{cost}} = \log_2\frac{1}{p(x)}$

 $H(p) = \sum_xp(x)\log_2\frac{1}{p(x)}=-\sum_xp(x)\log_2p(x)$
 
### [Cross-Entropy](https://en.wikipedia.org/wiki/Cross_entropy)
> This length – the average length of communicating an event from one distribution with the optimal code for another distribution – is called the cross-entropy.

Communicating $q$ using optimal code for $p$

$H_p(q)=\sum_xq(x)\log_2\frac{1}{p(x)}$

Usually, q is true distribution, p is predicted distribution. [source](https://www.youtube.com/watch?time_continue=425&v=ErfnhcEV1O8)

The **[Kullback–Leibler divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)** (KL divergence) of p with respect to q:

$D_q(p) = H_q(p) - H(p)=\sum_xp(x)\log_2\frac{p(x)}{q(x)} = \sum_xp(x)(\log_2p(x) - \log_2q(x))$

A measure of difference between two probability distributions.

Cross entropy and KL divergence are asymmetric.
### Entropy and Multiple Variables
**Joint Entropy**

$H(X,Y) = \sum_{x,y}p(x,y)\log_2\frac{1}{p(x,y)}$

**Conditional Entropy**

$H(X|Y) = \sum_yp(y)\sum_xp(x|y)\log_2\frac{1}{p(x|y)}=\sum_{x,y}p(x,y)\log_2\frac{1}{p(x|y)}$

### Mutual Information
- $H(X,Y)\geq H(X)\geq H(X|Y)$

- info of X and Y = info of Y + extra info from X which Y doesn't tell you
$H(X,Y) = H(Y)+H(X|Y)$

- **Mutual Information**
$I(X,Y) = H(X)+H(Y)-H(X,Y)
=\sum_{x,y}p(x,y)\log_2\frac{p(x,y)}{p(x)p(y)}$

>It’s the KL divergence of P(X,Y) and its naive approximation P(X)P(Y). That is, it’s the number of bits you save representing X and Y if you understand the relationship between them instead of assuming they’re independent.

- **Variation of Information**
$V(X,Y) = H(X,Y)-I(X,Y)$

<img src="http://colah.github.io/posts/2015-09-Visual-Information/img/Hxy-info.png"  width="300px"/>

### Fractional Bits
Optimal length $L(x) =  \log_2\frac{1}{p(x)}$ may not be integer.

Instead of trying to encode `a` and `b`,

we can try to encode all codes of

length 2:

aa,ab,ba,bb;

length 3:

aaa, aab, aba, abb, baa, bab, bba, bbb

...

Then the average length spent on `a` and `b` would be closer and closer to the optimal length.

>As n tends to infinity, the overhead due to rounding our code would vanish, and the number of bits per codeword would approach the entropy.

We can also use more complicated tricks to approach the entropy limit, or use a different encoding scheme: [Arithmetic coding](https://en.wikipedia.org/wiki/Arithmetic_coding) 




