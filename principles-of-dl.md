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

# Implications


# My Ideas

- There is something that bothers me a lot regarding AI. It feels like 'mathematics applied'. That's y I decided to learn it in the first place. Instead, when I see people '''using''' it on practice, they just run some tutorial on a subset of benchmark data and that's it. Like... wth? Where is the learning? Where is the science of the data? It is frustating because it has no art, no technique. It is even more dump than just writing a script to do the very same task. When reading the chapter's beginning I can only feel hopeless... so at the end there is no learning? Damn bro...

---

# On the pursue of a universal (?) theory...


The ML results are impressive. Curiously, its theory is still new and immature, disconnected from the practice. That is why [Roberts and Yaida decided to write The Principles of Deep Learning Theory](https://arxiv.org/pdf/2106.10165.pdf), aiming to analyze DNN in a relevant way. But how could them do it? We have elementary components changing and reacting at the same time: a baffling situation that _apparently_ hinders any chance of understanding why a given function is learned instead of any other.

Luckly for us, **theoretical physics** is used to find **simple, effective theories** for multi-component complicated systems. Take thermodynamics... in the 18th century some English gentlemen came up with the steam engine. In order to explain the empirical observations on the mechanics of steam, it took an insane amount of effort from guys like Maxwell, Boltzmann and Gibbs to link the experiments to the principles (statistical mechanics).

This works because physical theories aren't concerned about phenomena are natural or artificial. It only connects observables to the fundamental parematers. 
More importantly, we should recall we already know the intricacies of neural nets because each component (neuron) is explicitly placed (or defined) by us. We then know the mechanism transforming inputs in outputs through a cascade of signals. We just need to  grasp the macroscopic behaviour.