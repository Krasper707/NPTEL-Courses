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


Lec 6:
PyTorch

- OpenSource framework to build and train DL models.

### Tensors
 - Tensors are a multidimensional array used to store data in ML and DL frameworks..

```python
tenso0=torch.tensor(1)
tensor0

## tensor with one dimension
tensor1=torch.tensor([2,5,34,7,55])
tensor1.shape => torch.Size([5])
## tensor with two dimensions

tensor2=torch.tensor([ [0,1,7],[2,5,67]])
tensor2.size() = > torch.Size([2,3])
```

 - Can find out the number of dimension in a tensor using `.ndim` function
 - Number of `[` gives the dimension of tensor.

### Creating random tensors

```python
size=(3,4)
t4=torch.empty(size)


t5=torch.rand(size)

t6=torch.zeros(size)

t7=torch.ones(size)

```


- Default dtype for tensors with float values is `float32`
```python
##Initializing with particular dtype

t5=torch.rand(size,dtpye=torch.float16)


t4.type(torch.int32)


# Creating tensors from numpy arrays

n1=np.array([[9,4],[5,6]])
t8=torch.from_numpy(n1)
t9=torch.tensor(n1)

# Both the above methods work


# Creating a tensor from another tensor

t10= torch.ones_like(t8)

## Device agnostic code is an imp thing here.

device=torch.device('cuda' if torch.cuda.is_available() else 'cpu')
t11=torch.ones(3,7).to(device)
t11=torch.zeros(3,7,device=device)

#Elementwise addition

t14=t8+t9
# or t14= torch.add(t8+t9)

#Elementwise subtraction
t15= t8-t9
# or t15 = torch.sub(t8,t9)

#Elementwise multiplication

t16=t8*t9
#torch.mul(t8,t9)


#Elementwise division

t17=t8/t9
#torch.div(t8,t9)

x= torch.randint(0,3,(4,5))

randint(start,end,size)


```

- `.view` method shares the common tensors, that is if the values in parent tensor are changed, so is it in the child variable.


### Tensor Reduction Operations
- mean
- argmax
- sum


### Autograd
- Its a differentiation engine that powers neural network training.

```python
x=torch.tensor(2.0)
x.required_grad,x.is_leaf => False,True

# leaf tensors => If required_grad is False, is_leaf will be true i.e. they will be leaf tensors ; When user explicitly sets required_grad as True, the is_leaf will still be true ; but if pytorch implicitly defines it, it will not be a leaf tensor

y=3*torch.sigmoid(x)+5
y.backward() = > Does differentiation
# But gradient gets accumulated, so to prevent that, set `x.grad.zero()`
 
```
