# CancerSubtyping
Cancer subtyping using ML

Dept. of Computer Software Engineering 
2020.11.30

SW프로젝트 요약서

  During the cancer subtyping with biometric data classification, we deduced the intensity of tumors. Human architecture is independently constructed by different patterns of genes and proteins. Hence, determined patients with the same cancer, also have divergences in their cancer structure or subtype. Our goal is to select the right peptides on our data, create visual samples to finally classify them as different types of cancers. Since we had limited data to work with, we used one-shot learning algorithm which tries to mimic human intelligence in that we are able to instinctively weigh the similarities from just one sample of a given object and use it to differentiate new samples.  It is a relatively new field in supervised learning.

  In this project, we used a Siamese Neural Network (a type of one-shot learning) that exerts a distinctive structure to rank resemblance between inputs. Applying a convolutional architecture, we managed to achieve reasonable results. The model is capable of learning generic image features practical for predictions about class distributions with hardly any available sample from these new distributions. And it is trained using standard optimization methods on pairs sampled from the source data. The validation model learns to recognize input pairs related to the possibility that they fit in to a similar or different class. The pairing with the highest score according to validation network is assigned the highest probability for the one-shot task. If the features stored by the model are adequate to approve or refuse the likeness of images from one set of types, then they must be ample for other types, as the model has already been exposed to different type of tissues to stimulate deviation amongst the identified features.

  We divided our dataset into 2 main categories. They are images_background (used to train) and images_evaluation (used to evaluate).
Once the learning curve flattened out, we used the weights which got the best validation 20-way accuracy for testing. Our network averaged ~50% accuracy for tasks from the evaluation set, compared to 93% in the original paper. The original paper works with grayscale alphabets from 50 different languages. Probably the difference is because we didn’t implement many of the performance enhancing tricks from the original paper, like layer wise learning rates/momentum, data augmentation with distortions, Bayesian hyperparameter optimization and we also probably trained for less epochs. We are not too worried about this because this project was more about implementing one-shot learning in general, than squeezing the last few % performance out of a classifier. 
