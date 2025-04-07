Single feature linear regression: f_(w,b) (x)=wx+b

ŷ^((i) )=f_(w,b) (x^((i) ) )
f_(w,b) (x^((i) ) )=wx^((i) )+b
Cost function is a measure of the difference between predicted values and actual values.
Squared error cost function: J(w,b)=1/2m ∑_(i=1)^m▒(ŷ^((i) )-y^((i) ) )^2 =1/2m ∑_(i=1)^m▒(f_(w,b) (x^((i) ) )-y^((i) ) )^2 

Goal of linear regression: min┬(w,b)⁡J(w,b)

Outline for the gradient descent algorithm:
	Start with some w,b
	Keep changing w,b to reduce J(w,b) until we settle at or near a minimum (may have more than one minimum).

Gradient descent algorithm:
Repat until convergence :
{█(w∶= w-α ∂/∂w J(w,b)@b∶= b-α ∂/∂b J(w,b) )┤
α = learning rate

Correct implementation (simultaneous update)
tmp_w=w-α ∂/∂w J(w,b)
tmp_b=b-α ∂/∂b J(w,b)
w = tmp_w
b = tmp_b

If α is too small, gradient descent may be slow.
If α is too large, gradient descent may overshoot and never reach the minimum. In other words, it ma fail to converge, it may even diverge.
Near a local value, derivative becomes smaller and update steps becomme smaller. So, a minimum can be reached without decreasing α.
 
∂/∂w J(w,b)=1/m ∑_(i=1)^m▒〖(f_(w,b) (x^((i) ) )-y^((i) ) ) x^((i) ) 〗
∂/∂b J(w,b)=1/m ∑_(i=1)^m▒(f_(w,b) (x^((i) ) )-y^((i) ) ) 

Repat until convergence :
{█(w∶= w-α 1/m ∑_(i=1)^m▒〖(f_(w,b) (x^((i) ) )-y^((i) ) ) x^((i) ) 〗@b∶= b-α 1/m ∑_(i=1)^m▒(f_(w,b) (x^((i) ) )-y^((i) ) ) )┤

Batch gradient descent uses all the training examples in each step.

xj = jth feature
n = number of features
x ⃗^((i) ) = features of ith training example
〖x_j〗^((i) ) = values of feature j in ith training example

f_(w,b) (x ⃗^((i) ) )=w_1 x_1+w_2 x_2+...+w_n x_n+b
w ⃗  =[w_1  w_2  ...  w_n ]
x ⃗  =[x_1  x_2  ...  x_n ]
Multiple linear regression (not multivariate linear regression!): f_(w,b) (x ⃗ )=w ⃗⋅x ⃗+b

Without vectorisation: f_(w,b) (x ⃗  )=∑_(j=1)^n▒〖w_j x_j+〗 b

Vectorisation has two main benefits:
	Makes code shorter
	Computationally more efficient (by using parallel hardware)

Cost function: J(w_1,w_2,...,w_n,b) or J(w ⃗,b)

∂/∂w J(w,b)=1/m ∑_(i=1)^m▒〖(f_(w,b) (x ⃗^((i) ) )-y^((i) ) ) 〖x_j〗^((i) ) 〗
∂/∂b J(w,b)=1/m ∑_(i=1)^m▒(f_(w,b) (x ⃗^((i) ) )-y^((i) ) ) 

Repat until convergence :
{█(w_j ∶= w_j-α 1/m ∑_(i=1)^m▒〖(f_(w,b) (x ⃗^((i) ) )-y^((i) ) ) 〖x_j〗^((i) ) 〗@b∶= b-α 1/m ∑_(i=1)^m▒(f_(w,b) (x ⃗^((i) ) )-y^((i) ) ) )┤

Normal equation
	Only for linear regression
	Solve for w, b without iterations
Disadvantages
	Doesn’t generalise to other learning algorithms
	Slow when number of features is large (n > 10,000)

Feature scaling
	x_i ∶=  x_i/x_max 
	Mean normalisation: x_i ∶=  (x_i-µ_i)/(x_max-x_min )
	Z-score normalisation: x_i ∶=  (x_i-µ_i)/σ_i 

μ_j=1/m ∑_i^m▒〖x_j〗^((i) ) 
σ_j^2=  1/m ∑_i^m▒(〖x_j〗^((i) )-μ_j )^2 

Learning curve (cost vs iteration) helps see whether the cost function converges.
Automatic convergence test can be used too. If J(w ⃗,b) decreases by ≤ε in one iteration, declare convergence.

Values of α to try: 0.001, 0.003. 0.01, 0.03, 0.1, 0.3, 1

