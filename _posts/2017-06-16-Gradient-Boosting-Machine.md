Gradient Boosting = Gradient + Boosting
---
## 1. Boosting
    sequentially adding weak learners at each stage to compensate existing weak learners

## 2. Gradient
    identify shortcomings of exisiting weak learners


Algorithm
---
* At iteration i: model is $$F_i(x_1)$$, response is $$y_1$$, residual is $$y_1 - F_i(x_1)$$

(1) let $$h_i(x_1)$$ = $$y_1 - F_i(x_1)$$

(2) fit regression tree $$h$$ to data $$(x_1, y_1 - F_i(x_1)), (x_2, y_2 - F_i(x_2))$$ - Boosting concept to compensate the shortcomings of existing weak learners

(3) Gradient concept: 
        
Loss function $$L(y, F(x)) = (y-F(x))^2$$, 

Cost function $$J = \sum L(y_i, F(x_i))$$, treat $$F(x_i)$$ as a parameter and take derivatives:

$$\frac{dJ}{dF(x_i)} = F(x_i) - y_i$$, which is the residual - shortcoming, hence update $$F(x_i)$$ by the gradient:

$$F(x_i) = F(x_i) + \frac{dJ}{dF(x_i)} = F(x_i) - y_i$$
