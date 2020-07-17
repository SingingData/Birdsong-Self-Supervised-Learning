# Birdsong Self-supervised Learning

This repository complements the paper 'Using Self-Supervised Learning of Birdsong for Downstream Industrial Audio Classification' presented at ICML 2020 Workshop on Self-supervision in Audio and Speech on July 17, 2020. https://openreview.net/forum?id=_P9LyJ5pMDb

In manufacturing settings, workers rely on their sense of hearing and their knowledge of what sounds correct to help them identify machine quality problems based on the sound pitch, rhythm, timbre and other characteristics of the sound of the machine in operation. Using machine learning to classify these sounds has broad applications for automating the manual quality recognition work currently being done, including automating machine operator training, automating quality control detection, and diagnostics across manufacturing and mechanical service industries. 

We demonstrate the efficacy of using self-supervision with a pitch-intensive birdsong model to allow downstream classification of pitch-intensive industrial motor audio. We apply the 'Shuffle and Learn' temporal sequence validation methodology on the Constant Q Transform for self-supervised training.  Our downstream task is classifying ferry motor audio, identifying whether the audio belongs to the Wenatchee or the Tacoma ferry.

We also demonstrate the impact of using various data augmentation techniques to the upstream birdsong dataset.  In this case you can see that pitch shifting and time stretching has the most impact boosting classification accuracy on the downstream task.

In the preprocessing scripts you can find two methods we used to filter out undesirable audio samples, finding and eliminating samples with low magnitude differential and clustering with K-means on CQT transforms to identify undesirable non-birdsong audio.

The birdsong audio referenced here is available in this repository: https://github.com/SingingData/Birdsong
The Washington State ferry audio referenced here is available in this repository: https://github.com/SingingData/Vroom


