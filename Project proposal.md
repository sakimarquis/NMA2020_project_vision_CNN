## Contact
- Huadong Xiong (熊华东)
- sakimarquis@qq.com

## Group Members
- sakimarquis@qq.com; Huadong Xiong (熊华东)
- yuziang@sjtu.edu.cn; Ziang Yu (余子昂)
- mengdanting@m.scnu.edu.cn; Danting Meng (孟丹婷)
- lizhukaixing@gmail.com; Zhukaixing Li (李朱铠幸)

## Group Name
- UniversalApproximator

## Proposal

- Scientific question: What form does the brain encode top-down feedback in, and how can we characterize the complexity added by feedback in representation level? 
- Brief scientific background: Top-down feedback is a common mechanism in our brain. In a task-specific level, in order to implement this feedback, our brain should express the feedback in the representation form. So the feedback should increase the representational complexity in different brain area. We want to characterize this increased representational complexity.
- Proposed analyses: we have two possible approaches: 1) Train biologically plausible recurrent neural networks for cognitive tasks (HF Song et al. 2016, GR Yang et al. 2019, NY Masse et al. 2019, GR Yang & XJ Wang 2020). Then add top-down feedback to analyze the difference of connectivity, performance, representation dissimilarity matrix generated by feedback. 2) Given some tasks, compare neural network model with or without feedback and brain in terms of behavior and activity dynamics in representation level (Kriegeskorte 2015, Kriegeskorte & Diedrichsen 2016, Yamins & DiCarlo 2016, Paninski & Cunningham 2017).
- Predictions: Feedback should add some complexity in representational level, change representation dissimilarity matrix.
- Dataset: ImageNet, HCP.



## Description of project

1. Scientific question: How to understand the complex response pattern in high-level brain areas?
2. Brief scientific background: Neurons in high-level brain areas show complex responses pattern (Rigotti et al, 2013), which can’t be decoded by a linear combinations of Gabor filters like early visual areas (Kay et al. 2008).
3. Analyses: Map these spatial activity patterns to representational geometry (Kriegeskorte & Diedrichsen, 2019) to characterize these complex pattern by representation similarity analysis 	.
   And then we compare the representations and performance of neural network and brain to see how these stimuli are encoded respectively.
4. Conclusions or experiences: 1) The distances of stimuli between different semantic categories become longer from V1 to V4, implying that the stimuli are gradually decoupled. 2) The distances of stimuli within the semantic categories gradually become shorter and cluster together from V1 to V4. This may imply the stimuli in the same semantic category elicit a prototypical response pattern. 3) Pretrained resnet-18 achieve 78% top-1 accuracy on test set. Every layers of Resnet have the exactly same RDM, and the stimuli precisely clustered into the semantic categories. This may imply only 1 convolutional layer is enough to classify all stimuli. But with convolutional layer, only Resnet do this transfer learning task successfully.

