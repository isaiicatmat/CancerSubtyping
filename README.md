# CancerSubtyping
Cancer subtyping using ML

Dept. of Computer Software Engineering 
2020.11.30

SW프로젝트 요약서

  During the cancer subtyping with biometric data classification, we deduced the intensity of tumors. Human architecture is independently constructed by different patterns of genes and proteins. Hence, determined patients with the same cancer, also have divergences in their cancer structure or subtype. Our goal is to select the right peptides on our data, create visual samples to finally classify them as different types of cancers. Since we had limited data to work with, we used one-shot learning algorithm which tries to mimic human intelligence in that we are able to instinctively weigh the similarities from just one sample of a given object and use it to differentiate new samples.  It is a relatively new field in supervised learning.

  In this project, we used a Siamese Neural Network (a type of one-shot learning) that exerts a distinctive structure to rank resemblance between inputs. Applying a convolutional architecture, we managed to achieve reasonable results. The model is capable of learning generic image features practical for predictions about class distributions with hardly any available sample from these new distributions. And it is trained using standard optimization methods on pairs sampled from the source data. The validation model learns to recognize input pairs related to the possibility that they fit in to a similar or different class. The pairing with the highest score according to validation network is assigned the highest probability for the one-shot task. If the features stored by the model are adequate to approve or refuse the likeness of images from one set of types, then they must be ample for other types, as the model has already been exposed to different type of tissues to stimulate deviation amongst the identified features.

  We divided our dataset into 2 main categories. They are images_background (used to train) and images_evaluation (used to evaluate).
Once the learning curve flattened out, we used the weights which got the best validation 20-way accuracy for testing. Our network averaged ~50% accuracy for tasks from the evaluation set, compared to 93% in the original paper. The original paper works with grayscale alphabets from 50 different languages. Probably the difference is because we didn’t implement many of the performance enhancing tricks from the original paper, like layer wise learning rates/momentum, data augmentation with distortions, Bayesian hyperparameter optimization and we also probably trained for less epochs. We are not too worried about this because this project was more about implementing one-shot learning in general, than squeezing the last few % performance out of a classifier. 
  
  We were curious to see how accuracy varied over different values of “N” in N way one shot learning, so we plotted it, with comparisons to k nearest neighbors, random guessing and training set performance.

1. 프로젝트 개요
1.1 산학프로젝트 목적 및 동기
Because the composition of the genome and protein is different from person to person, the cause and the appearance may be different even for the same cancer. This can be regarded as a "subtype" of cancer, which can be classified through the composition of genomes and proteins.
In general, the composition of proteins is inferred through the pattern of peptides, which are fragments of proteins. In this project, we will image the pattern of peptides as a 3D map, and by implementing machine learning algorithms, subtypes of cancer will be identified and classified. 
In order to accomplish the project definition, we are going to apply all the knowledge acquired these past 4 years in computer software engineering department, specifically, we will focus on machine learning:  an application of artificial intelligence that provides systems the ability to automatically learn and improve from experience without being explicitly programmed. 
Machine learning is taking a bigger part in our health and well-being on a daily basis, and it is already being used for faster patient diagnosis. Even the prevention of illness in the first place has been aided by predicting the potential health problems one may be susceptible to, based on age, socio-economic status, genetic history, etc. The use of programs to analyze and cross-reference symptoms against databases containing millions of other cases and illnesses has led to faster diagnoses of illness and disease, saving lives through quicker treatment and decreasing the time a patient spends in the health system. Hospitals are currently using AI algorithms to detect tumors more accurately in radiology scans and analyze different moles for skin cancer, and machine learning is being adapted to accelerate research toward a cure for cancer.
In other words, the necessity of this project relies on the discovery of cancer subtypes which is useful for guiding clinical treatment of multiple cancers. Progressive profile technologies for tissue have accumulated diverse types of data. Based on these types of expression data, various computational methods have been proposed to predict cancer subtypes. It is crucial to study how to better integrate these multiple profiles of data for better clinical treatment of cancer.


1.2 산학프로젝트 목표
Several patients can possess the same type of cancer. However, each person has different patterns of genes/proteins, which implies that the same cancer can have different patterns as well, and this is called a cancer subtype. In other words, the aim of this project is to find cancer subtypes from each patient through the analysis of peptides (small fragments of protein). To achieve this, we will image the pattern of peptides as a 3D map. The images produced will be used as a dataset to feed our deep learning model named Siamese neural networks for one-shot learning. This model is going to use a combination of convolutional neural networks for image classification and cluster techniques to detect and classify all the subtypes of cancer.

2. 산학프로젝트 내용
The prerequisites needed to achieve the specific goals of this project involve having knowledge of concepts like statistics, linear algebra, calculus, probability, bioinformatics and programming languages. It is also required to have a strong background in machine learning, deep learning, and convolutional neural networks. Statistics contain tools that can be used to get some outcome from the data. There is descriptive statistics which is used to transform raw data into some important information. Also, inferential statistics can be used to get important information from a sample of data instead of using a complete dataset. Linear algebra deals with vectors, matrices, and linear transformations. It is very important in machine learning as it can be used to transform and perform operations on the dataset. Also, Calculus is an important field in mathematics, and it plays an integral role in many machine learning algorithms. Data sets having multiple features are used to build machine learning models where integrations and differentiations are a must. Probability helps predict the likelihood of the occurrences, it helps us to reason the situation may or may not happen again. For machine learning, probability is a foundation.
Furthermore, to achieve the main goal of this project, having a background on deep learning is also a requirement. This is a computer science branch that studies the design of algorithms that can learn. Deep learning is a subfield of machine learning that is inspired by artificial neural networks, which in turn are inspired by biological neural networks. 
 Also, it is essential to know programming languages like Python, which is the programming language that will be used for this project, in order to implement the whole Machine Learning process. Moreover, Python provide in-built libraries that make it very easy to implement Machine Learning algorithms. 
Another necessary field is Bioinformatics. Bioinformatics is a subdiscipline of biology and computer science concerned with the acquisition, storage, analysis, and dissemination of biological data, most often DNA and amino acid sequences. Bioinformatics uses computer programs for a variety of applications, including determining gene and protein functions, establishing evolutionary relationships, and predicting the three-dimensional shapes of proteins. We had the help of our TA (Teacher’s assistant) and mentor Mr. Baek Je Hyun, Director of the R&D Center for Clinical Mass Spectrometry, Seegene Medical Foundation, to guide us with this matter. 
To conclude, been familiar with the basics of machine learning, bioinformatics, deep learning and having some experience on using Convolutional Neural Networks with Python and Keras are the main requirements for the completion of this project.
Deep Convolutional Neural Networks have become the state-of-the-art methods for image classification tasks. However, one of the biggest limitations is that they require lots of labelled data. In many applications, collecting this many data are sometimes not feasible. In addition, the process of learning good features for machine learning applications can be very computationally expensive and may prove difficult in cases where little data is available. Since our project is based on a relatively small dataset, the model needs to do the learning just with a couple of labeled images instead of huge number of images. One Shot Learning aims to solve this problem.
Convolutional Neural networks (CNN)
CNN is a type of deep learning model for processing data that has a grid pattern, such as images, which is inspired by the organization of animal visual cortex [13, 14] and designed to automatically and adaptively learn spatial hierarchies of features, from low- to high-level patterns. CNN is a mathematical construct that is typically composed of three types of layers (or building blocks): convolution, pooling, and fully connected layers. The first two, convolution and pooling layers, perform feature extraction, whereas the third, a fully connected layer, maps the extracted features into final output, such as classification. A convolution layer plays a key role in CNN, which is composed of a stack of mathematical operations, such as convolution, a specialized type of linear operation. In digital images, pixel values are stored in a two-dimensional (2D) grid, i.e., an array of numbers (Fig. 2), and a small grid of parameters called kernel, an optimizable feature extractor, is applied at each image position, which makes CNNs highly efficient for image processing, since a feature may occur anywhere in the image. As one layer feeds its output into the next layer, extracted features can hierarchically and progressively become more complex. The process of optimizing parameters such as kernels is called training, which is performed so as to minimize the difference between outputs and ground truth labels through an optimization algorithm called backpropagation and gradient descent, among others.
