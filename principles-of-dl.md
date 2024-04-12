# Principle Concepts

Current AI systems contain billions of elementary components, or computational blocks, loosely based on biological neurons. These are organized into sequential computational layers (called deep neural nets, or DNN) that, after some initialization and training, _learn_ a refined representation capable of transforming data into something useful for a given task.

How does it work? Here goes a high level overview...

First of all, a **neural net** (NN) computes a function built out of many many simpler others (neurons). Each simpler ones are weighted sums of incoming signals that fires when the sums crosses some threshold. The parameters of the big function (NN) are the weights on the connections and the thresholds. 

> Modern DNN have billions of parameters 

In other words, we consider a NN a parametrized function of the form:

$f(x;\theta)$

with $x$ being the inputs and $\theta$ a vector containing the aforementioned parameters.

The first step is to initialize the net by sampling $\theta$ from a probability distribution $p(\theta)$.

We then adjust the parameter vector in order to make the network function as close as possible to the desired target function. That is:

$\theta \rightarrow \theta\ast \implies f(x;\theta\ast) \approx f(x)$ 

This function approximation (a.k.a. training) happens by **fitting $f(x;\theta)$ to training data**. Such data consists of pairs of the form

$(x,f(x))$

observed from the desired – but only partially observable target function $f(x)$.

Moreover, the method used to tune $\theta$ is called **learning algorithm**.

Our goal is to understand how the macroscopical behaviour emerges from the microscopic definitions. Moreover, we want to catch a glimpse of how the function approximation works and how data is consumed to make it happen.

To do that we could expand $f(x;\theta\star)$ around the initial values of $\theta$. But this has its own issues, like: $\theta$ is sampled and the training dynamics is non linear. This makes any possibility of following up the training impossible. 

To bypass it, let's suppose an infinite-width net. For reasons outside the scope of this short text, it causes the taylor expansion to be limited to the first derivative, the sampling in function of the derivatives independent, and the dynamics linear. This is cool, but mismatch the empirical findings about multi-layered NN.

To correct it, we use **perturbation theory** and define the inverse of layer width $\epsilon$. Again, I'm not going to go into the details here. It is important to know that, by defining this way, we solve the issues mentioned and keep things tractable and realistic. This is a promising way of discovering general rules and of understanding the overall behaviour of NN.

# Implications 

The definitions introduced above can be understood in the following terms:
- Neural Nets are function approximators;
- NN training is the same as function fitting (as we see in Numerical Analysis 101);
- The final network behaviour depends on the parameters learned. 

# My Personal Take 

First of all... the definitions here are fundamental to understand NN. Similar definitions can be seen in [Mitchell, 1997](http://www.cs.cmu.edu/afs/cs.cmu.edu/user/mitchell/ftp/mlbook.html) and [Goodfellow et al, 2016](https://www.deeplearningbook.org/). By seeing them as universal approximators and providing definitions regarding their behaviour and mechanisms we can them not as magical tools, but as clever solutions. More specifically, the definition of learning as an iterative optimization process helps to link the 'training' techniques to more intelligible mathematical processes, like interpolation and regression.

Regarding the desire to understand the global behaviour, the analogy of applied physics looks adequate. I'd rather say, though, that I do not know if the comprehension of neural nets in a universal, theoretical framework is possible, or if the empirical nature of Deep Learning and Big Data makes such a endeavour too complex.

---

# On the pursue of a universal (?) theory...


The ML results are impressive. Curiously, its theory is still new and immature, disconnected from the practice. That is why [Roberts and Yaida decided to write The Principles of Deep Learning Theory](https://arxiv.org/pdf/2106.10165.pdf), aiming to analyze DNN in a relevant way. But how could them do it? We have elementary components changing and reacting at the same time: a baffling situation that _apparently_ hinders any chance of understanding why a given function is learned instead of any other.

Luckly for us, **theoretical physics** is used to find **simple, effective theories** for multi-component complicated systems. Take thermodynamics... in the 18th century some English gentlemen came up with the steam engine. In order to explain the empirical observations on the mechanics of steam, it took an insane amount of effort from guys like Maxwell, Boltzmann and Gibbs to link the experiments to the principles (statistical mechanics).

This works because physical theories aren't concerned about phenomena are natural or artificial. It only connects observables to the fundamental parematers. 
More importantly, we should recall we already know the intricacies of neural nets because each component (neuron) is explicitly placed (or defined) by us. We then know the mechanism transforming inputs in outputs through a cascade of signals. We just need to  grasp the macroscopic behaviour.