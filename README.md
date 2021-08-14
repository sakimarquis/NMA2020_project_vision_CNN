# NMA2020_project_vision_CNN
This project was done in June 2020 at Neuromatch Academy. This work won’t proceed due to limited computational power and storage. 

## Question

Our initial question: what feedback or top-down control do under task demand? 

The neural activity in human and monkey resemble with HCNN in representational geometry. So we try to model possible feedback or top-down control mechanisms with deep neural networks. And these mechanisms may adapt to the task structure and improve the performance. So adding complexity to the task representations. Then we can compare the representations with neuroimaging data in the same tasks with RSA. And manipulate neural network and build computational model to characterize the computational mechanism of feedback or top-down control components.

![image-20210814121839262](D:\Study\Projects\NMA2020_project_vision_CNN\fig\RSA)





## Data

We use Kay/Gallant Dataset as a practice because this dataset is clean, avoiding a lot of preprocessing work of neuroimaging data. I want to first focus on the pipeline and models, then change the dataset. In this dataset, subjects passively watch the stimuli in fMRI scanner.

We labeled the stimuli into 4 categories by hand: animate-animals, animate-human, inanimate-artificial, inanimate-natural (Khaligh-Razavi & Kriegeskorte 2014). We assume all stimuli in the same category elicit a prototypical response pattern, which implies small dissimilarities between within-category representations. Stimuli is clustered in according the their categories.

![image-20210814122001985](D:\Study\Projects\NMA2020_project_vision_CNN\fig\kay_data1)



## Results

### Representation dissimilarity matrix of the fMRI data

- A stimuli (1750) x stimuli matrix, stimuli are sorted by 4 categories.

- The stimuli have an almost equally long distance from each other, suggesting the encoding is high-dimensional. 

- The result seems plausible in V1. But there should be some clusters by categories in V4.

![image-20210814125104582](D:\Study\Projects\NMA2020_project_vision_CNN\fig\result1)

### Why?

- We only have data in early visual cortex. 

- Stimuli are unclear and hard to identify, thus the process may be purely perceptual. No smooth transformation can be done by neurons.

- The spatial activity of fMRI evoked by the stimuli in early visual cortex can’t be clustered by non-linear method.

### RDMs after averaging within categories

- fMRI data be too noisy, so we average across stimuli within each categories and get categories x categories matrices.

- Between-categories distances become longer from V1 to V4, implying that the representations of categories are gradually decoupled.

- The distances within the two categories, “animate” and “inanimate”, gradually become shorter and cluster together from V1 to V4. This may imply the stimuli in the same category elicit a prototypical response pattern, which is what we expect.

![image-20210814125245252](D:\Study\Projects\NMA2020_project_vision_CNN\fig\RDM_average)

### Compare neural network and brain in representational level

#### Methods

1. Trained neural network to perform the same task as in neuroimaging data.

2. Compare behavior and representation in different layers.

3. Add feedback and top-down control components to neural network

   - Feedback: Lateral and top-down connections (Spoerer et al. 2017, Kubilius et al. 2019)
   - Attention (Vaswani 2017, Lindsay & Miller, 2018): rating functions by learning

   - Recurrent computation: CNN only looks at the whole image once. Human seems to use attention like zoom lens, looks at different parts of image at each timesteps.

   - Poisson noise or penalize time consuming: trade off between the noise/time and information got.

4. Compare again.

![image-20210814125442515](D:\Study\Projects\NMA2020_project_vision_CNN\fig\compareNNwithfMRI)

- Resnet-18 (He et al. 2016), brain-like recurrent ANNs CORnet (Kubilius et al. 2018), self-implement RCNN with biologically-plausible lateral and top-down connections (Spoerer et al. 2017), and Residual Attention Network (Wang et al. 2017).

- Resnet-18 achieve 78% top-1 accuracy on test set, the accuracy of the other two models are **chance-level**. Thus we only compare the hidden activity between Resnet-18 and brain. 

- **Every layers of Resnet have the exactly same RDM**, and the stimuli(1750) clustered into these 4 categories precisely. 

- It seems only the first convolutional layer is working to classify stimuli.
