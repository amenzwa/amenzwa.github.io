---
title: "How Artificial Intelligence Works"
tags:
  - mathjax
use_math: true
---

# INTRODUCTION

In this article, I present a high-level overview of artificial intelligence (AI). I describe what AI is, its inner workings, its uses, and its social and ethical implications. The intended audience is anyone curious about how AI works.

# APPROACHES

There are two main AI paradigms: connectionist and rule-based. *Connectionist* AI is commonly known as neural networks. *Rule-based* AI is traditionally associated with the LISP programming language.

## *connectionist*

The myriad AI techniques that are in popular use today, different as they may appear, all share a common foundation: they all come under the umbrella term *artificial neural network* (NN). NN is a computational approach inspired by the quintessential biological neural network—the [brain](https://en.wikipedia.org/wiki/Brain). The most basic processing unit in the brain is the [neuron](https://en.wikipedia.org/wiki/Neuron). See the figure below. The [dendrites](https://en.wikipedia.org/wiki/Dendrite) of the neuron receive electrochemical signal inputs as weighted outputs from the upstream neurons. The weight can be negative, zero, or positive. The [soma](https://en.wikipedia.org/wiki/Soma_(biology)), the cell body, sums up the weighted input signals. The neuron also receives activation signals via the dendrites. Inhibitory (negative) activation signal keeps the neuron inactive. Excitatory (positive) activation signal causes the neuron to fire its output, which is derived from the weighted sum of its inputs. The [axon](https://en.wikipedia.org/wiki/Axon) trunk carries the output signal to the [synapses](https://en.wikipedia.org/wiki/Synapse), which make electrochemical connections to the input dendrites of downstream neurons. Learning involves establishing, strengthening, weakening, and removing signal pathways among the neurons. Although the structure and functions of the brain are far more intricate and complex, the simply-butchered description above suffices for our purposes, here.

![biological neuron](./figures/AI/BiologicalNeuron.jpg)

The earliest, practical NN model was invented in 1943 by neuroscientist [McCulloch](https://en.wikipedia.org/wiki/Warren_Sturgis_McCulloch) and logician [Pitts](https://en.wikipedia.org/wiki/Walter_Pitts). The diagram below shows the [McCulloch-Pitts](https://en.wikipedia.org/wiki/Artificial_neuron) artificial neuron. The neuron $n_j$ computes $y_j = f(∑_{j=0}^{N} w_{ji} x_i)$. The $x_i$ are the output signals from the upstream neurons that arrive via an input connection, which has an associated multiplier called the weight $w_{ji}$. The neuron then sums all its weighted inputs $w_{ji} x_i$, and passes this value through the transfer function $f$ to compute its output $y_j$. The McCulloch-Pitts neuron uses a simple threshold function as its transfer function, which models the activation behaviour of the biological neuron. The output is then sent to the downstream neurons via weighted connections.

![McCulloch-Pitts neuron](./figures/AI/McCullochPitts.jpg)

Neurons are assembled into a neural network by arranging them in layers. Classic NNs typically used one or two layers of neurons, along with their weighted connections, as shown below. Learning involves presenting a list of input pattern vectors to the network and then modifying its connection weights in accordance with how well the network recognises each pattern. This weight adjustment method is referred as the *learning algorithm*. The final weight values produced by the algorithm encode the salient features present in the training patterns. In this context, a *feature* is a distinctive attribute of an entity. It could be breadth, curvature, colour, texture, edges, anything the network can use reliably to identify the entity.

![neural network](./figures/AI/NeuralNetwork.jpg)

The two main types of learning algorithms are the supervised and the unsupervised varieties. A *supervised* learning algorithm requires a target (desired output) pattern for each input pattern, whereas an *unsupervised* learning algorithm does not require target patterns.

There have been many classic NN learning algorithms. The first was the unsupervised [self-organising](https://ieeexplore.ieee.org/document/1057468) learning algorithm invented by Farley and [Clark](https://en.wikipedia.org/wiki/Wesley_A._Clark) in 1954. Although unsupervised learning algorithms are less frequently used today, the [self-organising map](https://en.wikipedia.org/wiki/Self-organizing_map) (SOM) algorithm is well known. It was invented in 1982 by Finnish engineering professor [Kohonen](https://en.wikipedia.org/wiki/Teuvo_Kohonen), who was inspired by the human perceptual systems, specifically the visual and the aural. Most learning algorithms in use today, however, are of the supervised variety. They trace their origins to the [Perceptron](https://en.wikipedia.org/wiki/Perceptron), a supervised learning algorithm for linear classifiers. It was invented by American psychologist [Rosenblatt](https://en.wikipedia.org/wiki/Frank_Rosenblatt) in 1957. He first implemented the algorithm on Cornell's IBM 704 mainframe. Subsequently, he built a custom, electromechanical [analogue computer](https://en.wikipedia.org/wiki/Analog_computer), called the Mark I Perceptron, which used motorised [potentiometers](https://en.wikipedia.org/wiki/Potentiometer) to represent trainable (adjustable) weights. Perceptron was capable of recognising letters. The eye of the Perceptron was a $20 × 20$ grid of photocells that produced a [greyscale](https://en.wikipedia.org/wiki/Grayscale) image. This resolution, though very low, was adequate to encode letters presented to the sensor.

## *rule-based*

The main weakness of Perceptron was its linearity: it can only learn to discern patterns if they are linearly separable, that is their classifier boundary is a straight line. The Perceptron's inability to learn even the simplest of non-linear classifiers, like the one required to implement the [exclusive or](https://en.wikipedia.org/wiki/Exclusive_or) (XOR) function shown below, led to its eventual downfall.

![non-linear classifier](./figures/AI/NonLinearClassifier.jpg)

In 1969, [Minsky](https://en.wikipedia.org/wiki/Marvin_Minsky) and [Papert](https://en.wikipedia.org/wiki/Seymour_Papert) of MIT AI Lab published their book, [*Perceptrons*](https://en.wikipedia.org/wiki/Perceptrons_(book)). This book contains mathematical proofs of why the Perceptron algorithm is incapable of solving non-linear problems. Minsky and Rosenblatt were childhood friends. Minsky dedicated his book to Rosenblatt—cheeky.

Minsky was motivated, at least in part, to show the limitations of the connectionist approach, because his AI Lab at MIT was wholly dedicated to rule-based approach. In 1958, [McCarthy](https://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist)) created the [LISP](https://en.wikipedia.org/wiki/Lisp_(programming_language)) programming language at MIT. Incidentally, the first implementation of LISP was for the IBM 704. LISP was a machine implementation of [𝜆-calculus](https://en.wikipedia.org/wiki/Lambda_calculus), a mathematical model of computation created by [Church](https://en.wikipedia.org/wiki/Alonzo_Church) in 1936. Indeed, LISP was the second high-level programming language (after FORTRAN) and the first [functional](https://en.wikipedia.org/wiki/Functional_programming) programming language. The mathematical nature and the [symbolic processing](https://en.wikipedia.org/wiki/Computer_algebra) abilities of LISP was well suited to implementing rule-based AI programmes, and it quickly became the favourite among the rule-based crowd, [especially at MIT](https://en.wikipedia.org/wiki/Lisp_machine). Suffice it to say, Minsky's *Perceptrons* killed off Perceptron and other NNs in the early 1970s, and expert systems dominated AI over the next decade.

An [expert system](https://en.wikipedia.org/wiki/Expert_system) is an AI application modelled upon the way human experts make technical decisions in the course of performing their daily duties. Early automated theorem proving systems, chess playing systems, and decision support systems were, in essence, expert systems. Such a system is preconfigured with a set of rules for making decisions—selecting a `yes` or a `no` at each step. When the user provides an input, the system applies the rules against the input and, step by step, arrives at a decision. When the set of rules is comprehended and comprehensive, expert systems work exceedingly well. Another major advantage of expert systems is that the results can always be explained fully by simply tracing the algorithm's path down the decision tree.

But few things in nature exhibit such orderly behaviour. Moreover, humans understand even fewer things in nature at such a level of detail. Even if we manage to grasp the dynamics of a large problem, the rules and their interactions would be intractable. Unfortunately, the purveyors of expert systems over promised and the media over reported the hype. By the early 1980s, the users and the public had lost interest in expert systems, and the funding spigot was shut. This period is now known as [AI Winter](https://en.wikipedia.org/wiki/AI_winter).

## *backpropagation*

A few researchers who saw the true strengths of AI continued working in the field, underground. In 1986, [Rumelhart](https://en.wikipedia.org/wiki/David_Rumelhart), [Hinton](https://en.wikipedia.org/wiki/Geoffrey_Hinton), and [Williams](https://en.wikipedia.org/wiki/Ronald_J._Williams) published their seminal paper, *[Learning representations by back-propagating errors](https://www.nature.com/articles/323533a0)*. Their learning algorithm became known as *backpropagation* (BP). BP is a supervised learning algorithm that modifies the network's weights in proportion to the amount of representation error the network commits in each pass through the data set. In that respect, BP's learning process is no different in kind than that of the Perceptron: find the optimal set of weights that minimise representation errors. But BP's main advantage over the Perceptron is its ability to learn non-linear classifiers. Indeed, non-linearity was why BP works and Perceptron did not. Mathematically, the BP learning algorithm is a simple, [gradient descent](https://en.wikipedia.org/wiki/Gradient_descent) optimisation scheme known to mathematicians since [Cauchy](https://en.wikipedia.org/wiki/Augustin-Louis_Cauchy) introduced it in 1847. But practically, it was capable of solving substantive problems which, until then, were deemed too difficult for machines.

In the 1980s, a room-sized minicomputer, like the [DEC VAX-11/780](https://en.wikipedia.org/wiki/VAX-11), had 1 MB of RAM, usually much less. So, networks were very small, a typical model having just two layers and a handful of neurons in each layer. Despite such restrictions, BP-based networks were able to solve efficiently a number of complex, non-linear problems, like speech recognition, image classification, robotics control, etc. Within a couple of years, BP single-handedly resuscitated the dying AI field. Many variants and improvements soon followed, further improving network performance. Understandably, the AI community was cautiously optimistic, this time round.

Most users of NNs simulate on mainstream computing hardware, like the VAX-11 or RISC workstations. But these machines, though powerful for their day, are severely limited in both CPU power and RAM capacity. In response, a number of groups developed custom hardware for neural computing. Some built machines out of common digital hardware but optimised for neural computing, but others designed custom analogue VLSI chips. The Stanford group led by [Mead](https://en.wikipedia.org/wiki/Carver_Mead) was especially productive in this area. His PhD student, [Mahowald](https://en.wikipedia.org/wiki/Misha_Mahowald), developed the [silicon retina](https://en.wikipedia.org/wiki/Event_camera), which is an image sensor technology that out performs the human eye and the best DSLRs by several orders of magnitude. This technology was further developed by Mead's company, [Foveon](https://en.wikipedia.org/wiki/Foveon), which is now part of [SIGMA](https://www.sigma-global.com/en/).

Most folks today are unaware that there was a AI Mini Ice Age during the mid 1990s. Although the hardware capabilities had increased leaps and bounds, the storage technology was still somewhat limited. Disc sizes were still measured in MB, albeit in hundreds thereof. Most data sets used in AI were only a few MBs in size. The lack of storage capacity necessarily constrained the completeness of data sets. So, neither humans nor networks could see the true nature of massive, complex, dynamical systems. The lack of data, thus, stunted the growth of AI. To get around some of the limitations, many experimented melding rule-based and connectionist techniques. But for the most part, NNs were confined to academic research and to small-scale commercial use to the end of the 1990s. The [dot-com collapse](https://en.wikipedia.org/wiki/Dot-com_bubble) at the end of the 1990s and the subsequent economic stagnation did no favours to AI.

## ***deep learning***

Then came the age of Internet Giants—the early 2000s. Massive, simultaneous advances in computing power, storage capacity, network connectivity, graphics technology, and software techniques conspired to create the fastest growth in the history of human invention. The Web came of age. Online shopping became the norm. Billion-user social media platforms became a reality. The Internet Giants saw gold in the users' private data, which they procured by giving away free online services. [Big data](https://en.wikipedia.org/wiki/Big_data) was born. It was in this era of data that people began recognising the true potential of BP, rather its descendant—[deep learning](https://en.wikipedia.org/wiki/Deep_learning) (DL).

Whereas the classic BPs of the 1990s could only use two or three layers of neurons due to hardware limitations, the modern DLs routinely employ many layers and many different types of neurons. Typically, home users of DLs train their networks on high-end, desktop graphics cards, like the [nVIDIA RTX](https://www.nvidia.com/en-us/design-visualization/desktop-graphics/) so as to exploit the graphics card's built-in support for parallel matrix operations across tens of thousands of cores. The "deep" in deep learning refers to the depth of those many layers, as shown below.

![deep learning neural network](./figures/AI/DeepLearningNetwork.jpg)

Another substantial advantage of modern DLs over classic BPs is feature extraction. Feature extraction required the use of sophisticated, mathematical techniques such as [digital signal processing](https://en.wikipedia.org/wiki/Digital_signal_processing) (DSP), [digital image processing](https://en.wikipedia.org/wiki/Digital_image_processing) (DIP), [natural language processing](https://en.wikipedia.org/wiki/Natural_language_processing) (NLP), etc. Each such technique constitutes a highly specialised, not to mention expansive, subfield within mathematics or engineering. So, competent practitioners were relatively few in numbers in the early days of BPs, which limited their usefulness. But DLs subsume feature extraction into the front-end layers of the network. That is, a DL network automatically extracts salient features from the data, and learns to represent those features in its connection weights, with little or no guidance from human experts. Hence, DL networks can be used effectively even by non-experts. Paradoxically, this characteristic of DLs is also a disadvantage, of sort: if a complex AI problem can be solved merely by clicking a button on a GUI, there is no need for the user to perform any analysis of the problem domain and of the massive amounts of data accumulated, so he gains no insight into the problem and he cannot explain the reasons why the solution appears to work. Regardless, DLs are here to stay; now is their day.

Over the past quarter century, our shopping habits, social media propensities, blogging activities, email exchanges, cloud-borne personal information—just about every aspect of our lives, both personal and professional—have been collected, analysed, categorised, tracked, and predicted by Internet Giants' DLs. Despite their prominence in modern life, however, DLs are but a small part of a much broader category of powerful modern methods known collectively as [machine learning](https://en.wikipedia.org/wiki/Machine_learning) (ML) algorithms, which in turn are a subfield within AI.

# APPLICATIONS

classification

recognition—character, image, speech

trending

control

composition—text, music, painting

# ALGORITHMS

categories—statistics, connectionist, hybrid, etc.

classic techniques—SOM, BP, analogue VLSI

modern techniques—DL

data collection, analysis, cleansing—statistics, projection, DSP, DIP, wavelets

# AWARENESS

dangers—lack of moral and ethical grounding, inability to explain discriminatory decisions

ethical implications—privacy, liberty, life, democracy

regulations

# CONCLUSION

There are three types of people interested in AI: the curious public, the incurious users, and the eager researchers. The curious public are those who do not work with AI but just want to understand how AI works at a basic level. The incurious users are coders in the IT industry who could care less about how AI works and they just want to slap together some AI programme. The eager researchers are the ones who have their skins in the game. Although this article is aimed at the curious public, the other two groups may benefit from it, as well: coders and their managers may benefit from understanding better what the code is doing; aspiring researchers and beginning graduate students may benefit from knowing the historical background of their field of interest.

Some years ago, I was shooed off the NN forum on the now-defunct Google+ platform by a gang of young AI enthusiasts for suggesting that all researchers should be familiar with the classic works of researchers, like McCulloch, Pitts, Rosenblatt, Widrow, Kohonen, Hopfield, Rumenhart, LeCun, etc., in addition to the modern literature. Despite my resounding defeat on social media, I stand by that view: they who admire only the newest and the most fashionable learn nothing from history, and they lack the requisite background of the field. It is important to realise that knowing how to code an AI application using library calls is not the same as understanding what that application is actually doing. Those who use AI without comprehending its strengths, weaknesses, and ethical implications bring no long-term benefits to society. Indeed, they may do more harm than good to humanity.

Lastly, the public must recognise that the founders and leaders of Internet Giants do not necessarily understand the AI technologies their companies are employing. The chief executive of a corporation is legally responsible for maximising the shareholders' returns. This legal mandate often conflicts with ethical, social, and equitable concerns of the public. The IT executives should wield their powers, by all means; but they ought to act in a socially responsible manner. When these large, powerful international conglomerates wilfully breach the public's trust, the only recourse is the law. In a democracy, the law derives its powers from the public. As such, the public must exercise its duty to study the impacts and trends of AI technologies and to monitor the activities of AI users.
