
# Additive Models, XGBoost
---


```R

```

# Nonparametric Smoothing Splines **$g(x)$**

Types of Splines:
---
(1) cubic splines

(2) natural cubic splines

Model Fitting Procedures
---

(1) min $RSS = \sum_{i=1}^n (y_i - g(x_i))^2$

(2) $g(x)$ needs to be smooth: $\int g''(t)^2dt$ is controlled

minimize cost function: $$\sum_{i=1}^n(y_i - g(x_i))^2 + \lambda \int g''(t)^2dt$$




# XGBoost as an Additive Method

Additive Method
---
* a set of basis functions \{ $h_m(x)$ \}
    
    $h_m(x)$
    -  can be individual classifier $\in \{-1,1\}$
    - simple functions $I(L_m \leq X_k < U_m)$

* a linear combination of basis functions (aka. a linear expansion in $X$)
    $$f(x) = \sum_{m=1}^M\beta_mh_m(x;\gamma_m)$$ 
    $b(x;\gamma_m)$ is simple functions of multivariate $x$
    
* $f(X) = \sum_{j=1}^P f_j(X_j)$, where $f_j(X_j) = \sum_{m=1}^{M_j}\beta_{jm}h_{jm}(X_j)$

    Examples:
    - **Splines**: a piecewise polynomial function of degree $k$ (eg. k=3)
        + continuous and has continuous derivatives at knots
    - **Smoothing Splines**:
        + avoid knot selection
        + maximal set of knots
        + regularization
        + cost function:
        $$RSS(f,\lambda) = \sum_{i=1}^N \{y_i - f(x_i)\}^2 + \lambda\int \{f''(t)\}^2dt$$

* Selection methods: select significant $h_{jm}$
    - stagewise greedy approaches: CART, MARS, boosting


Model Improvement Methods:
---

(1) Bagging

(2) **Boosting**
* Basis function: $b(x;\gamma)\in R$ is simple function of multivariate $x$
* $$f(x) = \sum_{m=1}^M \beta_m b(x;\gamma_m)$$

for trees, $\gamma$ parametrizes the split variables and split points at the internal nodes

* Procedures:

1) initialize $f_0(x) = 0$
2) for m = 1:M:

    (a) Compute: 

$$(\beta_m, \gamma_m) = argmin_{\beta,\gamma}\sum_{i=1}^N L(y_i, f_{m-1}(x_i)+\beta b(x_i;\gamma))$$

    (b) Set 

$$f_m(x) = f_{m-1}(x) + \beta_m b(x;\gamma_m)$$



What topics are you interested in Machine Learning currently?
