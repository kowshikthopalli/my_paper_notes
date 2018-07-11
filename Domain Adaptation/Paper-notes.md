## [DeepJDOT: Deep Joint distribution optimal
transport for unsupervised domain adaptation](https://arxiv.org/pdf/1803.10081.pdf)
-
They do mainly OT between source and Target domains jointly with the class labels. 

General approaches in OT 
for Domain Adaptation have been to first learn the map without the class labels i.e. only between distributions and then train a classifier. 

The authors in this paper build up on JDOT by courty et al. Relevant lines from the paper are here
"Courty et al. [5] proposed the joint distribution optimal transport (JDOT)
method to prevent the two-steps adaptation (i.e. first adapt the representation
and then learn the classifier on the adapted features) by directly learning a classifier
embedded in the cost function c.The underlying idea is to align the joint
features/labels distribution instead of only considering the features distribution .
" 
i.e their cost function is the weighted sum of both the squared euclidean between the distributions along with the labels - refer to eqn 3.


The use feature outputs(last but one layer) of CNNs as the distribution and try to do OT. Since these are of large size- do stochastic i.e., in minibatches
Two things to be optimized
- the optimal coupling \gamma 
- the CNN's embedding function g:x-> z and f: z-> labels. 
their proposal is to fix one optimize other and repeat this till convergence between all minibatches. 
They get OT coupling by network simplex algorithm. ** Not entropic regularized and hence no sinkhorn ** as this would mean another regualrization term. 

While doing JDOT there could be a possibility that the classifier in a quest to decrease the classification loss on target domain might actually do bad on the source in which it has been trained so add this also to the objective. 

So now we have weighted sum of three loss
1. source classifier loss
2.target classifier loss computed from the source labels and the target labels produced by CNN(f) a
3. the OT loss. which is the dot product of the \gamma and the ground cost or distance between CNN features

See algorithm 1 for a clear understanding. 

