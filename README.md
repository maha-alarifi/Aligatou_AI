# AIigatou_AI
> Team #15 in #AI_Artathon 2020

In this project I'll explaine our pipeline from the preprocessing of our datasets, training CycleGAN model, till we finaly upscaled the output and discared the noise. 

## Table of Contents

>`Preprocessing`
- [Dataset Segmentation](#segmentation)
- [Dataset Outlines](#outlines)
- [Dataset Augmentation](#augmentation)

>`Model Training`
- [CycleGAN](#training)

>`Postprocessing`
- [Upscale](#upscale)
- [Noise Reduction](#noise)


>`Website`
- [Try it Out](#features)

>`Info`
- [Team](#team)
- [FAQ](#faq)

## Datasets Preprocessing
In the cycleGAN archetucture, there are two GAN models. Each GAN model need to be trained on distinguished dataset inorder to come with something new. Since my team and I want to work with our own dataset, we came up with a way to have differnet representation of our dataset. We took our dataset, applay segmentation to it, then took the segmented dataset, then took the outlines of it. This may look similar to the pix2pix method `but we did not paire the images`. Simply we augmented the two datasetes after we took the outlines of the outlies of the segmented data.

### Segmentation
In order to get our segmented dataset, we used unsupervised algorithm `K-mean` to cluster the colors in an image.  For expermintal purposes we tried to to cluster 2 colors in an image and 3 colors. Then we notice that some of the images looks abslotly different with the different clusters number. So for some cases we took the both clustering results.
| Original | Segmententation 3 | Segmentation 2 |
| ------------- | ------------- | ------------- |
|![](O_I_01.png "Original Image")| ![](S_2C_I_01.png "Segmented to 3 colors")| ![](S_1C_I_01.png "Segmented to 2 colors")|

### Outlines 
We tried to use the Segmented dataset as the Dataset B with the Original dataset as Dataset A, but we were not pleased with the outcomes. Therefore, we thought about a way to increase the varaity between our A/B datasets, and this is how we get to extract the outlines of our drawings as the second dataset. `Please notice that this is NOT paired images approach`.
We extracted the outlines of our segmented drawings.
| 3 Colors Segment | Outline | 2 Colors Segment | Outline |
| ------------- | ------------- | ------------- |------------- |
| ![](S_2C_I_01.png "Segmented to 3 colors")|  ![](L_S_2C_I_01.png "Outline from 3 Colors Segment")| ![](S_1C_I_01.png "Segmented to 2 colors")| ![](L_S_1C_I_01.png "Outline from 2 Colors Segment")|


### Augmentation 
Finally the last step in preprocessing, we used augmentor in order increase the number of examples in out dataset.  We have initially 121 original drawings from our artist, we segmented these images and then took the outlines to have a second dataset. Then we augmented these two datasets differently to gaine 500 examples each to trian our cycleGAN. We applied (random flip, random 90˚ rotate, random 15˚ rotate) for 70% of each dataset and resize all of them to (256px * 256px). and these are our final two datasets.
| Datasets | The | Joy Of | Augmentation |
| ------------- | ------------- | ------------- | ------------- |
| *Dataset A*     | ![](O_A_01.png)|  ![](O_A_02.png)| ![](O_A_03.png)|
| *Dataset B*     | ![](L_A_01.png)|  ![](L_A_02.png)| ![](L_A_03.png)|

## Model Training

### Training

## Postprocessing

### Upscale
### Noise
