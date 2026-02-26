# Summary of Weeks 3/4 Assignment

**Methodology**

1. Classical: Images were manually filtered and enhanced. Segmentation functions built into scikit-learn were then applied to obtain features of each NP.
2. Random Forest/SVM: Using the features obtained from the previous step, each NP was categorized based on how spherical vs. elliptical they were. Each NP had to be labeled prior to feeding the images into the supervised learning model.
3. K-Means: Data points from each image formed clusters that enabled unsupervised classification of NPs based on spherical vs. elliptical criterion set in the prior step. No prior labeling was necessary.
4. CNN: Segments were hand-selected and manually labeled from each image to develop a robust training set for the CNN. To artificially generate a larger volume of training and validation data, data augmentation was performed.
5. U-Net: Image filtering and enhancement from the classical step was first applied on the raw images. These images were then fed into the U-Net model to segment them.



**Quantitative comparisons**

The classical and ML pipelines performed well to the dataset (F1 scores of random forest and SVM were 0.97 and 1.00 respectively and the K-Means clustering had a silhouette score of 0.629 at k = 7). The runtimes of these pipelines were also reasonable, ranging from 0.15 s down to 0.005 s. The success of these models could be attributed to the quality and simplicity of the data, which made image processing and interpretation much more manageable. The U-Net model performed quite well, with a mean dice coefficient of 0.9451 and a mean IoU of 0.8965. While this model performed well, this was also a more computationally expensive operation with a runtime of 92.2 s. The CNN model did not perform well (F1 score = 0.521), which could be attributed to overfitting or simply human error during the labeling step.



**Recommendations**

ML pipelines offer great performance at low computational costs for this particular dataset. ML pipelines would thus work best for datasets that include much more interpretable information and aim to address classification problems. Deep learning pipelines would be more useful for information that may require deeper inquiries of the information (perhaps because the information might not be intuitive or interpretable at first glance), though these come at a high computational cost.

