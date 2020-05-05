hello everyone, today I am going to introduce a system for large-scale machine learning -- tensorflow

At the beginning of my presentation, I have to clarify that all the pictures in slides are either from unsplash website which is free of charge and copyright problem or drawn by myself.

OK lets's get started. So what is Tensorflow? TensorFlow is a machine learning system that operates at large scale and in heterogeneous environments.

let me put it in this way,. The core purpose of tensorflow is to unify various forms of machine learning  on top of the single flexible platform. Several Google services use TensorFlow in production, which we may heard of. Google rankBrain, which uses machine learning to determine the most relevant results to search engine queries. and smart reply, here is vivid example of smart reply. If you got an email sent by your friend saied that she cannot make it to the party tonight. Therefore, gmail to automatically generate replys based on the content of email. You may send ... The first time I saw this technique, oh I was astonished,  it is amazing, such a convinent and powerful tool

Then I want to emphsize the motivation why on earth shoud we need tensorflow?

machine learning is becoming a pretty hot topic due to many reasons. More Well designed machine learning models and Large datasets contribute to the thriving of ML.

And there are three things in machine learning we do care about and have huge potential applications in the industry world

large-scale training, which takes masses of data in the computer and trains machine learning models, let's say face recongnition and object detection

take those models into production, which means to place the models on small agent serverice, like google web ranking or place models on mobile device, like smart reply we just mentioned about minutes ago.

machine learning research, which is to use various forms of model archetecture and algorithms to test our ideas. Hopely it can be the furture production.

The problem is that there is no one system that actually support these three needs. Speaking of large-scale training, google do have system called disbelief, wihch can train deep neural networks in hundreds of machines. However, it does not scale down to the application case, and it has several defects.

### layers

this is the question I faced in my creative experiment. All the exsiting layer cannot satisfy my need. So I have to write my own designed layer to see the outcome.

### Optimization Techniques

here I list some of the Optimization Techniques that we may use in our own NN models. Mini-batch gradient descent: when we deal with large dataset and we want to reduces the variance of the parameter updates, which can lead to more stable convergence

Adaptive Moment Estimation (Adam) [[14\]](https://ruder.io/optimizing-gradient-descent/index.html#fn14) is another method that computes adaptive learning rates for each parameter. In addition to storing an exponentially decaying average of past squared gradients. 

I am not going to dicuss the detail of diffrent Optimization Techniques. I just want to point out that there are many amazing gradient deceding methods, which Disbelief may not implement. 

### NN structures 

DistBelief workers follow a fixed execution pattern: read a batch of input data and the current parameter values, compute the loss function (a forward pass through the network), compute gradients for each of the parameter (a backward pass), and write the gradients back to the parameter server. this is the sequence of the simplest forms of NN structure. what if we have more sophiscated structure, like **Generative Adversarial** network, where we have train generate and discriminator in a loop. Or we want to add dropout to the NN, that is randomly disable some of the nodes in the network to prevent overfitting 



computation state 



![v2-88bbe819b8c9a75a438bb62086174650_r](/Users/zhengruiqi/Documents/junior/2020spring/操作系统/project/v2-88bbe819b8c9a75a438bb62086174650_r.jpg)









## 4 core idea

TensorFlow model represents 具体的很多流程都可以简化成一个有向图

individual mathematical operators (such as matrix multiplication,

convolution, etc.) as nodes in the dataflow

graph. This approach makes it easier for users to compose

novel layers using a high-level scripting interface.

Tensors represent the inputs to and results of common operations such as matrix multiplication

Operations take tensors as input and produce tensors as output. They can have mutable state that

is read and/or written each time it is executed (advantages to this to be discussed)

Departing from traditional dataflow systems where graph vertices represent

functional computation on immutable data,

○ the TensorFlow graph vertices may have mutable state that can be shared between different

executions of the graph

using the graph’s

dependency structure to issue a sequence of kernels to the

GPU without waiting for intermediate results.











Insead of introdcing the verey specific technique details, I want to give you a general picture of tensorflow. what is tensorflow, why we need tensorflow, the application of tensorflow and my personal opinion about it. If you have any questions, please feel free to ask. We can also discuss the  technique details if you are interested. 

提一些建议哦 听了两天的presentation  大家都主要侧重于技术和实验结果，这样的presentation不是那么的完整  
建议大家增加一些背景、motivation的介绍，以及更加生动的应用场景 ，毕竟听你们Presentation的同学可能并不特别了解你看的这篇主要在做什么，所以要说清楚为什么做这个东西 做这个东西能干吗  不能只是讲怎么做
另外就是对于论文希望大家可以增加自己的理解 毕竟大家不是作者，你不要只是看论文讲了什么，请增加一些自己的想法比如优点、缺点、改进之处、或者作者故意隐藏的可能的问题