# Birdsong Self-supervised Learning

This repository complements the paper 'Using Self-Supervised Learning of Birdsong for Downstream Industrial Audio Classification' presented at ICML 2020 Workshop on Self-supervision in Audio and Speech on July 17, 2020. https://openreview.net/forum?id=_P9LyJ5pMDb

In manufacturing settings, workers rely on their sense of hearing and their knowledge of what sounds correct to help them identify machine quality problems based on the sound pitch, rhythm, timbre and other characteristics of the sound of the machine in operation. Using machine learning to classify these sounds has broad applications for automating the manual quality recognition work currently being done, including automating machine operator training, automating quality control detection, and diagnostics across manufacturing and mechanical service industries. 

We demonstrate the efficacy of using self-supervision with a pitch-intensive birdsong model to allow downstream classification of pitch-intensive industrial motor audio. We apply the 'Shuffle and Learn' temporal sequence validation methodology on the Constant Q Transform for self-supervised training.  Our downstream task is classifying ferry motor audio, identifying whether the audio belongs to the Wenatchee or the Tacoma ferry.

For the upstream self-supervised training on the birdsong, following the “Shuffle and Learn” design, we designed a Triplet Siamese network for sequence verification.  We implement this architecture within Kears.  We reduced the last dense layer of the AlexNet architecture modestly to fit available computational resources. We applied the Lecun normal initializer, leaky ReLu and liberally applied drop-out. We balanced the datasets.

For our downstream architecture, we took just one of the Siamese Triplets to form the basis of our downstream model.  We loaded the pre-trained weights on each of the convolutional layers, and added two trainable dense layers and an output layer. We froze the first three layers and allowed the last three layers to be trainable. We trained the downstream task for 20 epochs with each of the data augmentation permutations.

We also demonstrate the impact of using various data augmentation techniques to the upstream birdsong dataset.  In this case you can see that pitch shifting and time stretching has the most impact boosting classification accuracy on the downstream task.

In the preprocessing scripts you can find two methods we used to filter out undesirable audio samples, finding and eliminating samples with low magnitude differential and clustering with K-means on CQT transforms to identify undesirable non-birdsong audio.

We will add the augmentation scripts shortly.

The birdsong audio referenced here is available in this repository: https://github.com/SingingData/Birdsong
The Washington State ferry audio referenced here is available in this repository: https://github.com/SingingData/Vroom


