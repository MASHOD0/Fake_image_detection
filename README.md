# Challenging Fake Image Detection using GAN Models
The task of challenging fake image detection is a vast feild of study in this project we focus our efforts on classifying Facial Images generated by GANs. 
In this Project We have:
- [x] Find the right dataset
    - [x] [140k real and fake faces](https://www.kaggle.com/datasets/xhlulu/140k-real-and-fake-faces)
    - [ ] [Artifact Dataset](https://www.kaggle.com/datasets/awsaf49/artifact-dataset)
    - [ ] [Real vs Fake Face Classification](https://www.kaggle.com/datasets/undersc0re/fake-vs-real-face-classification)
    - [ ] [Real and Fake Face Detection](https://www.kaggle.com/datasets/ciplab/real-and-fake-face-detection/)
- [x] Do the right EDA
- [x] Augment the dataset
    - [x] Geometric Transformations:
        - [x] Flip

- [x] Classification using transfer learning on Models like 
    - [x] Xception
    - [ ] MobileNetV2
    - [ ] InceptionV3
    - [ ] VGG 19
- [x] Study the results
    - [x] Classification accuracy
    - [x] Confusion matrix
    - [x] Precision
    - [x] Recall
    - [x] F1 score
    - [x] ROC curve
    - [x] AUC

## Dataset
The dataset consists of all 70k REAL faces from the Flickr dataset collected by Nvidia, as well as 70k fake faces sampled from the 1 Million FAKE faces (generated by StyleGAN) that was provided by Bojan.
Dataset link - [https://www.kaggle.com/datasets/xhlulu/140k-real-and-fake-faces](https://www.kaggle.com/datasets/xhlulu/140k-real-and-fake-faces)
## Results
### Abalation Studies
All these results have been observed after 10 epochs of training the model.

### Data Augmentation
#### Horizontal flip
| Horizontal_flip |        | Precision | Recall | f1-score |  
|-----------------|--------|-----------|--------|----------|
|`True`           |fake    |       0.97|    0.96|      0.97|
|                 |real    |       0.96|    0.97|      0.97|       
|                 |acuraccy|           |        |  **0.97**|
|`False`          |fake    |       0.94|    0.99|      0.97|
|                 |real    |       0.99|    0.94|      0.97|       
|                 |acuraccy|           |        |      0.97|
### 2. Optimizer
              

| Optimizer |        | Precision | Recall | f1-score |  
|-----------|--------|-----------|--------|----------|
|Adam       |fake    |       1.00|    0.75|      0.86|
|           |real    |       0.80|    1.00|      0.89|
|           |acuraccy|           |        |      0.88|
|SGD        |fake    |       0.97|    0.96|      0.97|
|           |real    |       0.96|    0.97|      0.97|       
|           |acuraccy|           |        |  **0.97**|

### 3. Activation Function of Output layer

| Optimizer |        | Precision | Recall | f1-score |  
|-----------|--------|-----------|--------|----------|
|softmax    |fake    |       0.00|    0.00|      0.00|
|           |real    |       0.50|    1.00|      0.67|
|           |acuraccy|           |        |      0.50|
|sigmoid    |fake    |       0.97|    0.96|      0.97|
|           |real    |       0.96|    0.97|      0.97|       
|           |acuraccy|           |        |  **0.97**|

### 4. Dropout
| Dropout |        | Precision | Recall | f1-score |  
|---------|--------|-----------|--------|----------|
|0.3      |fake    |       0.97|    0.96|      0.97|
|         |real    |       0.96|    0.97|      0.97|       
|         |acuraccy|           |        |      0.97|
|0.2      |fake    |       0.98|    0.96|      0.97|
|         |real    |       0.96|    0.98|      0.97|       
|         |acuraccy|           |        |  **0.97**|

### Models
| Pre-trained models |        | Precision | Recall | f1-score |  
|--------------------|--------|-----------|--------|----------|
|Xception            |fake    |       0.97|    0.96|      0.97|
|                    |real    |       0.96|    0.97|      0.97|       
|                    |acuraccy|           |        |  **0.97**|
|MobileNetV3         |fake    |       0.50|    1.00|      0.67|
|                    |real    |       0.00|    0.00|      0.00|       
|                    |acuraccy|           |        |      0.50|
* the experiment was conducted initially with different activation functions, the results may vary if conducted again
### Future Improvements
#### Add more data Augmentations
- [ ] Geometric Transformations:

    - [ ] Flip
    - [ ] Crop
    - [ ] Rotate
    - [ ] Stretch
    - [ ] Zoom

- [ ] Color Space Transformations:

    - [ ] Change RGB channels
    - [ ] Contrast 
    - [ ] Brightness

- [ ] Kernel filters:

    - [ ] Sharpness 
    - [ ] blurring

#### Explainability and Fairness
Make the model more transparent, interpretable and fair addressing issues related to bias and discrimination
this can be done using techniques like integrated gradients

Integrated Gradients is a technique for attributing a classification model's prediction to its input features. It is a model interpretability technique: you can use it to visualize the relationship between input features and model predictions.

Integrated Gradients is a variation on computing the gradient of the prediction output with regard to features of the input. To compute integrated gradients, we need to perform the following steps:

1. Identify the input and the output. In our case, the input is an image and the output is the last layer of our model (dense layer with softmax activation).

1. Compute which features are important to a neural network when making a prediction on a particular data point. To identify these features, we need to choose a baseline input. A baseline input can be a black image (all pixel values set to zero) or random noise. The shape of the baseline input needs to be the same as our input image, e.g. (299, 299, 3).

1. Interpolate the baseline for a given number of steps. The number of steps represents the steps we need in the gradient approximation for a given input image. The number of steps is a hyperparameter. The authors recommend using anywhere between 20 and 1000 steps.

1. Preprocess these interpolated images and do a forward pass.

1. Get the gradients for these interpolated images.
1. Approximate the gradients integral using the trapezoidal rule

#### Expand the domain 
The current model classifies only facial image data however this can be expanded to:
- [ ] Animals 
    - [ ] Cats
    - [ ] Dogs
- [ ] Plants
- [ ] Terrain and Landscapes

Larger datasets such as [Artifact](https://www.kaggle.com/datasets/awsaf49/artifact-dataset) Can be utilized for this.

### Contributor
- [Mashhood Alam](https://mashod0.github.io)