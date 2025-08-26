# Week 3 
## Lec 5 (Intro to deep learning)

### History
 - In 1943, McCulloch and Pitts came up with the MPNet
 - 1957-58(approx) Frank Rosenblatt proposed idea of perceptron (considered as first neural network)
 - 1965-68 : Multi-Layer Perceptron
 - 1969: Minskey and Papert ; Setback that XOR operation cannot be done using MLP
 - 1986: Backpropogation was introduced 
 - 1989: Universal Approximation Theorem( MLP with one hidden layer can be used to approximate any continuous function to any desired level of precision)


### MPNET
- Input: Binary {0,1}
- Output: Binary {0,1}
- $$g(\sum^{N}_{i=1} x_i) = 1 >= \theta else; =0 if \le \theta$$

- g(x) is usually a Boolean Operation (AND,XOR,OR,etc)
- If g(x) is AND operation ; if $$x_1+x_2 \ge 2$$ : 1 ; else 0

Signum Function is used to mimic the various operations.

Number of layers in the neural network:  Depth of neural network
Number of neurons in every layer: Width of Neural Network

Depth and width are hyperparameters.


Sigmoid Function $$\sigma (n) = \frac {1}{1+e^{-x}}$$

Derivative of sigmoid = $$\sigma (1- \sigma)$$

- Vanishing Gradient Problem: Gradient vanishes slowly
- Sigmoid is not symmetric around 0
- tanh : g(x) = $$\frac { e^x - e^{-x}} {e^x + e^{-x}}$$
- tanh reduces everything from -1 to 1
- Softmax : g(x) =  $$\frac {e^{x_1}} {\sum e^{x_i}  }$$
- ReLu : f(x) = x if x $$\ge$$ 0 ; 0 if x<0
- Dead Neuron problem happens in ReLu. ; To combat this, we have Leaky ReLu : f(x)=x if x>=0 else 0.01*x if x<0
-  Parametric ReLu: f(x) =ax if x<0 ; x otherwise
-  Concatenated ReLu = [ReLu(x) ,ReLu(-x)]
-  GeLU: Gaussian Error Linear Unit; GeLu(x)= $$x \phi(x)$$ where $$\phi(x)$$ is the cumulative standard normal distribution. ;  GeLu(x)= $$x \phi(X \le x)$$ ; Captures the percentile
-  GLU: Gated Linear Unit
-  Swish Activation: Swish(x) = $$x \sigma(\beta x)$$
-  Swish GLU: $$x (dot) Swish(wx+b)$$

---
