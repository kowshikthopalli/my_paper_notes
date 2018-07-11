[DeepJDOT: Deep Joint distribution optimal
transport for unsupervised domain adaptation](https://arxiv.org/pdf/1803.10081.pdf)
-
They do mainly OT between source and Target domains jointly with the class labels. General approaches in OT 
for Domain Adaptation have been to first learn the map without the class labels i.e. only between distributions and then train a classifier. 
The authors in this paper build up on JDOT by courty et al. Relevant lines from the paper are here
"Courty et al. [5] proposed the joint distribution optimal transport (JDOT)
method to prevent the two-steps adaptation (i.e. first adapt the representation
and then learn the classifier on the adapted features) by directly learning a classifier
embedded in the cost function c.The underlying idea is to align the joint
features/labels distribution instead of only considering the features distribution .
" 
i.e their cost function is the weighted sum of both the squared euclidean between the distributions along with the labels - refer to eqn 3.
