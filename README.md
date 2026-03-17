<h1 align="center"> MSC Thesis - Multimodal-Ground-Sensing-for-Prediction-of-Cracking-Severity-in-Pomegranate-Fruit-Trees </h1>
<p align="left">
</p>

<h4 align="center"> Research By: Arad Peleg </h4>
<h4 align="center"> Supervised By: Prof. Yael Edan, Dr. Victor Alchanatis </h4>
<h4 align="center"> Research Collaboration: Yoav Yoktan, Guy Lidor, Roman Brikman, Michael Brener, Assaf Tzur, Idit Ginzberg, Christian Reagan and Manuela Zude </h4>
<h4 align="center"> Institute of Agricultural and Biosystems Engineering, Agricultural Research Organization, Volcani Institute </h4>
<h4 align="center"> Dept. of Industrial Engineering & Management, Ben-Gurion University of the Negev </h4>
<h4 align="center">  Leibniz-Institut für Agrartechnik und Bioökonomie e.V. (ATB), Potsdam, Germany </h4>

Hi 👋, This research investigates the prediction of on-tree pomegranate fruit cracking severity using multimodal deep learning approaches. The work integrates image-based features and temporal metadata extracted from meteorological station and thermal images within a CNN+LSTM architecture, incorporating attention mechanisms to enhance feature representation across time points. Additionally, fuzzy labeling techniques and binary labling are explored to better model uncertainty in cracking severity classification. This research is conducted under the CrackSense project, as a collaboration between Ben-Gurion University of the Negev (Department of Industrial Engineering and Management) and the Volcani Institute, combining expertise in AI, agriculture, and sensing technologies.

CrackSense (https://cracksense.eu/) is a Horizon Europe initiative running from January 2023 to December 2026. It brings together 14 partners from 7 countries to address the challenge of fruit cracking in crops such as citrus, pomegranate, table grapes, and sweet cherries. The project focuses on developing and scaling advanced sensing technologies, aiming to provide real-time sensor data through experimental field trials and pilot implementations. As part of this broader multidisciplinary effort, this thesis contributes to CrackSense’s goal of enhancing precision agriculture through intelligent monitoring and prediction systems.

<h4 align="center"> <img width="246" height="125" alt="תמונה1" src="https://github.com/user-attachments/assets/495506a4-be14-4ea7-a601-0667fad7af31" /> </h4>


<strong> 📁 In this repository You will have access to:</strong> 
1. Preprocessing Models Code Folder:
- 📦 Object detection model code (YOLOv8)
- 🧩 Segmentation model code (U-Net) --> including GrabCut and augmantion (in U-Net notebook) code
- ✂️ Image cropping code (RGB and Thermal sensors)
- 🌡️ Thermal image and feature extraction code
- 🔥🌍 Fitting thermal and environmental tabular data code
- 📄 Research publication paper link (full manuscript / preprint) - From Labeling Strategies to Cross-Season Generalization: A Multimodal Deep Learning Framework for Tree-Level Prediction of Pomegranate Fruit Cracking

  Link: https://docs.google.com/document/d/1nbl2_ewR_Hh5YZQVWZn2x5dm0kcjSyoq/edit?usp=drive_link&ouid=100602072493698229200&rtpof=true&sd=true

Image cropping, Thermal image and feature extraction and Fitting thermal and environmental tabular data in Processing notebook.

2. CNN+LSTM Models Code Folder:
- 🧠 All CNN+LSTM model configurations (model 1 to 6)
- 📈 Statistical analysis code for diffrence in field side predictions
- 🧠 Fuzzy labeling CNN+LSTM for Model-5 (best performing model) --> labels created in code notebook
- 🧠 Binary labeling CNN+LSTM for Model-5 (best performing model) --> labels created in code notebook

Data organization is primarily handled in the Model-1 notebook, and adjustments are also generally made in the CNN+LSTM models notebook.

3. Cross-Season Generalization CNN+LSTM Models Code Folder (For Diffrent labeling schemes):
- 🧠 Cross-season generalization (Optmized model-5 CNN+LSTM; train 2024 seson dataset  --> test 2025 season data set) across all labeling schemes

4. 📊 A detailed description of all datasets used for the different deep learning models in this research, including RGB images, thermal data, meteorological features, annotations, and dataset organization across the 2024 and 2025 seasons, is provided in the DataSets.pdf file (You need to download the file to get access to the links).

**Note:** The 2025 season dataset used in this research can be requested via email (aradpls2@gmail.com).

<h4 align="center"> Data Collection: </h4>

<h4 align="center"> <img width="632" height="236" alt="zsa" src="https://github.com/user-attachments/assets/e7a0186c-9fd4-4405-9681-411197677c30" /> </h4>

Data was collected using the TOMMY system, which includes thermal and RGB sensors, between August and November 2024 in Tzara near Beit Shemesh, Israel. Images of the Wonderful pomegranate cultivar were captured under three conditions: at night with artificial lighting, at sunrise with dew on the fruits, and during the day under full sun. Around 4400 images were taken, typically twice per time point. For each tree on one side of the field, a corresponding tree from the opposite side (north and south side of the field) was also imaged to ensure full coverage. The system captured 40–60 images per tree side from different angles along the X-axis to cover the entire canopy. RGB images used autofocus with occasional manual lighting adjustments, while thermal images were manually focused for sharper temperature contrast. All images were visually inspected for quality. A meteorological station was also used to log environmental data every minute during each acquisition session.

<h4 align="center"> <img width="668" height="438" alt="image" src="https://github.com/user-attachments/assets/74c701d7-690a-44f9-8f89-0284929b254a" /> </h4>

- Data Collection Dates and Time

 <h4 align="center"> <img width="668" height="438" alt="image" src="https://github.com/user-attachments/assets/018282e4-d40d-42ba-875f-7ad060f3e1d1" /> </h4>

The full dataset was organized so that images of each tree taken on a particular date are matched with images of the same tree from the next data collection session (the next time point). It is important to note that the images of different rows in the field were captured one day apart, ensuring that both sides of the same tree are captured for full coverage. For analysis, this setup will be considered as data collected over the span of one time point. This organization ensures consistency and allows for better temporal comparisons within the dataset. All data in both 2024 and 2025 collection sessions occurred between 4:30 AM and 9:30 AM which allowed us to capture images of the pomegranate trees under different conditions.

- Dataset Arrangement

 <h4 align="center"> <img width="668" height="438" alt="image" src="https://github.com/user-attachments/assets/a373afb0-220b-4d6c-8508-f7c49f3fbe99" /> </h4>

To ensure consistency across the dataset, two artificial time points were created to replace missing data, and time point 0 was excluded due to inconsistencies in image collection. Each RGB image was paired with a corresponding thermal image and aligned meteorological data based on timestamps. Because spatial alignment between RGB and thermal cameras was unreliable, thermal data was used in tabular form rather than as raw images. Each data sequence represents one tree and consists of three time points, stored in a folder containing three CSV files with aligned thermal, meteorological, and image path information. After filtering out incomplete sequences, the final dataset included 9,276 entries organized into 3,092 full three-time-point sequences used for model training. The same preprocessing procedure was applied to the 2025 dataset. In 2025, a total of 7481 RGB images were collected across the corresponding imaging sessions and were paired with their thermal and environmental data in the same manner as in 2024. After removing incomplete or unmatched cases and forming consistent three-time-point sequences, the 2025 dataset resulted in 3024 RGB images organized into 1008 complete three-time-point sequences, which served as the independent dataset for evaluating seasonal generalization.

- Ground Truth Labels

Three labeling strategies were used to define the cracking status of pomegranate trees. First, multi-class severity labels were assigned by manually counting the number of cracked fruits per tree at the final time point: label 0 (0–2 cracked fruits), label 1 (3–5), label 2 (6–8), and label 3 (more than 8). These served as the ground truth for severity-based prediction tasks. Second, a fuzzy labeling approach was applied to account for uncertainty near class boundaries. This method assigned partial membership values to each severity class based on proximity to the class medians (1, 4, and 8 cracked fruits). Fuzzy labels enabled smoother transitions between classes and better modeled borderline cases. Finally, a binary labeling scheme was developed, where trees were labeled as 0 (no cracking) or 1 (any cracking present), regardless of severity. This simplified the prediction task and proved to be the most robust and practical strategy, especially for early warning purposes. All three labeling strategies were evaluated using the same CNN+LSTM architecture, with sensitivity analyses conducted to compare their effects on model performance.

<h4 align="center"> Model performance evaluation measures </h4>
<h4 align="center">  <img width="672" height="238" alt="image" src="https://github.com/user-attachments/assets/0bd4cef4-9fc2-4d60-bfc4-1cb295cd3009" /> </h4>

- Object detection model evaluation
<h4 align="center">  <img width="668" height="153" alt="image" src="https://github.com/user-attachments/assets/37679db7-dfc4-45f6-a96d-17363a491726" /> </h4>

- Segmentation model evaluation
<h4 align="center">  <img width="680" height="134" alt="image" src="https://github.com/user-attachments/assets/b8265a71-8a2f-4172-aded-a9edd51edc1a" /> </h4>

- CNN+LSTM for prediction of cracking severity evaluation
<h4 align="center"> <img width="826" height="310" alt="image" src="https://github.com/user-attachments/assets/bb208a0d-e119-4971-aed7-7d6402d62d94" /> </h4>

- Fuzzy labeling evaluation metrics

To evaluate the performance and consistency of the fuzzy label predictions, three complementary metrics were used. Mean Squared Error (MSE) and Cosine Similarity assess the accuracy of the model’s predicted fuzzy vectors relative to the expected soft labels. Additionally, two custom evaluation metrics were introduced. The first is the inter-side MSE, which quantifies differences in predictions between the north and south sides of the field for the same test instances. Since both sides observe the same tree from different viewpoints, their predictions are expected to be similar. This metric therefore evaluates cross-view consistency and helps assess the model’s ability to produce stable predictions from different viewing angles. The second metric is a composite accuracy (CA) score, defined to enable numerical comparison between fuzzy-label and hard-label strategies. The CA combines fuzzy-label agreement, computed as one minus the normalized mean squared error, with its hard-label classification accuracy using a weighted-sum formulation with equal weighting (α = 0.5). Together, these metrics assess fuzzy prediction accuracy, cross-view consistency, and agreement with hard-label performance.
<h4 align="center"> <img width="731" height="650" alt="image" src="https://github.com/user-attachments/assets/6aa977b3-3b0d-4bb8-ae39-512c9998e001" /> </h4>

<h4 align="center"> Algorithm Pipe Line: </h4>

![NY](https://github.com/user-attachments/assets/02332191-9e82-4a50-9ce6-f5d8158e9915)

This project presents a multimodal deep learning pipeline for predicting pomegranate fruit cracking severity using RGB and thermal images combined with meteorological data. An initial YOLOv8 object detection model, trained with manual annotations and external PG-YOLO data (https://github.com/LforikC/PG-YOLO-Dataset), was fine-tuned and used to detect fruit regions. These detections were then used to generate segmentation masks using the GrabCut algorithm, which refines object boundaries by iteratively separating foreground (fruit) from background (e.g., sky, ground). Segmented images were further processed using a U-Net model to isolate pomegranate regions, followed by image enhancements like CLAHE, Gaussian blurring, and Laplacian edge detection. Thermal and environmental features were extracted and aligned with the images based on timestamps, with feature engineering, multicollinearity checks, and normalization applied. All processed image and tabular inputs were fed into CNN+LSTM models, where CNN handled spatial features and LSTM captured temporal patterns. The final output predicts cracking severity levels for each fruit instance.

<h4 align="center"> YOLOv8 Architecture: </h4>

![arc2](https://github.com/user-attachments/assets/45935619-e667-4e1c-9347-050df503705e)

- PG YOLO traning set up: 

![ZDAPG](https://github.com/user-attachments/assets/98cbfb1f-f171-4e72-b9bf-8f592cb6aeb9)

- Selected transfer learning technique  for object Detection: 

<h4 align="center"> <img width="565" height="107" alt="TL" src="https://github.com/user-attachments/assets/cb7825f6-4008-4bc2-af23-27a4fa872075" /> </h4>

- Transfer learning traning set up:

![setups](https://github.com/user-attachments/assets/a619e7ed-b0b5-4e0a-9e73-f07c67d880db)

To detect pomegranates on trees, we used the YOLOv8s object detection model, chosen for its balance between speed and accuracy. We initially trained the model on an external dataset (PG-YOLO) containing over 13,000 annotated images of pomegranates. After this, we applied transfer learning by fine-tuning the model on a smaller set of 616 manually labeled images from our own orchard data. This allowed the model to adapt to our specific environmental conditions, such as lighting and background variation, while significantly reducing the need for extensive manual annotation. We tested several train-test splits to evaluate the model's robustness under different data conditions and found that the model maintained strong detection capabilities even with smaller training sets. This step provided accurate bounding boxes around fruits, which were then used in the later stages of the pipeline, such as cropping and segmentation.

- Sensitivity analysis split testing on transfer learning model: 

![SPLOT](https://github.com/user-attachments/assets/9ab27e2f-2587-47ed-b9dc-6f2e83f263df)


<h4 align="center"> YOLOv8 Pomegranate Detection Results : </h4>

- YOLOv8 pomegranate detection transfer learning result:

![ZDAresutls](https://github.com/user-attachments/assets/1d71a923-cdef-47c0-b446-e138ff1a7823)

- Raw Transfer
  
<h4 align="center"> <img width="875" height="318" alt="image" src="https://github.com/user-attachments/assets/40bf9516-3677-4c32-9eb6-c5a4342e2926" /> </h4>

- Fine tuned model

<h4 align="center"> <img width="857" height="312" alt="image" src="https://github.com/user-attachments/assets/2d674b70-c1f5-47a0-9a16-8f3cb5c2b85b" /> </h4>

- Raw trnsfer Vs Fine tuned model precision recall curve

<h4 align="center"> <img width="1015" height="347" alt="image" src="https://github.com/user-attachments/assets/d09da223-846b-4ddc-ba4a-c745123bba28" /> </h4>

- Sensitivity analysis split testing on transfer learning reuslts: 

<h4 align="center"> <img width="803" height="480" alt="image" src="https://github.com/user-attachments/assets/053fe0ad-f629-4c67-b323-4e831795bf94" /> </h4>

The object detection split tests showed minor differences across the four configurations. Test 1 achieved strong overall performance with mAP50 of 86.6%, mAP50-95 of 54.1%, and F1-score of 82.0%, reflecting high detection accuracy and good localization. Although Test 2 had slightly higher mAP50 (86.9%) and precision (87.1%), it showed a small drop in mAP50-95. Test 3 yielded similar results, while Test 4 had the weakest performance. In the end, Test 1 was selected for generating bounding boxes for Grab-Cut segmentation due to its consistent advantage in localization and recall, offering the best trade-off for precise mask generation.

<h4 align="center"> Grab Cut Algorithm: </h4>

- Exmaple mask creation

<h4 align="center"> <img width="936" height="343" alt="image" src="https://github.com/user-attachments/assets/329035d0-40de-4273-bb09-4e45b60ced48" /> </h4>

The mean SSIM  score between the YOLO-cropped RGB images and the corresponding Grab-Cut masks was 87.6%, indicating a high level of structural similarity. This suggests that the Grab-Cut algorithm (section  generally succeeded in preserving the shape and spatial structure of the objects identified by YOLO.

<h4 align="center"> U-Net Segmentation Architecture: </h4>

![arc3](https://github.com/user-attachments/assets/37ba06bb-3e30-4ee9-8abe-58870ffa8992)

We used the U-Net architecture for segmenting pomegranates from RGB images. U-Net is ideal for image segmentation, especially when working with small datasets, thanks to its encoder-decoder structure and skip connections. We tested different backbones: ResNet-50, which uses residual connections to support deep architectures, and EfficientNet-B7, which balances network scaling for higher accuracy. The segmentation masks were generated from manually cropped images (using bounding boxes from the detection model) and resized to 160×256 for compatibility with the network. We trained the model using CrossEntropyLoss and optimized it with the AdamW optimizer. Pretrained ImageNet weights were used in some experiments to improve convergence. A learning rate scheduler (ReduceLROnPlateau) was applied to dynamically adjust training progress. The final output of the model is a binary mask identifying pomegranate regions, which is later used for downstream prediction tasks.

- Segmentation models Sensitivity Analysis Testing 

![ZDAseef](https://github.com/user-attachments/assets/93436488-e4e8-4090-b3ec-df66e5737adb)

<h4 align="center"> Pomegranate Segmentation Results: </h4>

- Pomegranate Segmentation Results

<h4 align="center"> <img width="745" height="445" alt="image" src="https://github.com/user-attachments/assets/2826425f-ecd9-4fa8-858b-5c2ef0f01601" /> </h4>

- Pomegranate Segmentation Example

<h4 align="center"> <img width="1012" height="565" alt="image" src="https://github.com/user-attachments/assets/40244905-2695-4930-be35-2b5f58de292c" /> </h4>

The segmentation tests evaluated three configurations using IoU, precision, recall, and F1-score. Test 1, which lacked data augmentation, produced the lowest results with an IoU of 82% and an F1-score of 80.3%, indicating poor generalization. Test 2 introduced data augmentation, leading to a 2.8% increase in IoU, a 7.7% rise in recall, and a 3.7% improvement in F1-score, showing better robustness. Test 3, which used EfficientNet-B7 as the backbone, achieved the highest precision at 89.1%, a slight IoU improvement, and maintained strong recall and F1-score. In the end, Test 3 was selected to segment the entire dataset due to its superior overall performance and more accurate pomegranate segmentation. Its predictions were used as input for the CNN+LSTM models.

<h4 align="center"> CNN + LSTM General Intermediate Fusion Architecture: </h4>

![FACDD2](https://github.com/user-attachments/assets/1bb29b70-5435-47b4-94b2-fa61c1543abc)

<h4 align="center"> Pure LSTM Architecture (model-6): </h4>

![FACDD1](https://github.com/user-attachments/assets/387826f4-654e-40e1-8820-a4634689d81e)

<h4 align="center"> CNN+LSTM Model Configurations: </h4>

 ![zda](https://github.com/user-attachments/assets/c51fa4c7-8380-4a2f-a2a7-bb3e68698fe8) 

 ![or34](https://github.com/user-attachments/assets/2147487e-90ed-4938-8327-a1f62c68a887)

The core model CNN+LSTM architecture for prediction of cracking severity is based on intermediate fusion, where separate streams process each modality in parallel. A convolutional neural network (CNN) extracts spatial features from each of the three RGB image crops, which are then flattened to prepare for fusion. Flattening is necessary because fully connected layers require fixed-length input vectors. Meanwhile, a long short-term memory (LSTM) network processes the sequence of tabular features over the same three time points, producing a final hidden state that captures temporal dependencies. The flattened CNN features and the final LSTM hidden state are then concatenated into a single joint representation. This combined vector is passed through a series of fully connected layers with ReLU activations and dropout for regularization. These layers progressively reduce the dimensionality and enable the model to learn complex relationships between spatial and temporal information. The final output layer produces class logits, which are converted to class probabilities using a softmax function.

Six model configurations were developed to progressively incorporate different enhancements. Model 1 used a basic ResNet-50 backbone with no image processing or feature engineering and served as a baseline. Model 2 introduced a ConvNeXt backbone, custom penalty matrix loss, feature engineering, and label fusion for classes 2 and 3 due to limited sample size. Model 3 added Linear Discriminant Analysis (LDA) on the tabular data and switched to focal loss. Model 4 applied grayscale transformation and CLAHE to the images. Model 5 added Gaussian blur and Laplacian edge detection to the previous configuration. Model 6 applied LDA jointly to both tabular and CNN-extracted image features and used a pure LSTM architecture, differing from the intermediate fusion models used earlier. All models except Model 6 utilized CNN+LSTM intermediate fusion, where CNN and LSTM branches are trained in parallel, and their outputs are merged before the final decision layer.

Data splitting followed a standard 80-20 rule, with 80 percent used for training and 20 percent for testing. From the training set, 20 percent was further set aside for validation. In early experiments (Models 1 and 2), the dataset was split based on the tree row’s orientation (north or south) to determine whether location had an impact on cracking behavior. Later models combined data from both rows after statistical tests confirmed no significant differences in cracking behavior or prediction variance. When split by row, there were 980 training, 245 validation, and 321 test samples per side. When combined, the dataset included 1960 training, 490 validation, and 642 test samples. All models were trained with a batch size of 16 and an initial learning rate of 0.001. Early models were trained for 10 epochs, while all subsequent models were trained for 30. Model weights corresponding to the lowest validation loss were saved and used for final evaluation. Notably, the test set contained only class 0 and class 2 samples, comprising 334 and 298 three-time-point sequences, respectively. After identifying the best-performing model (model-5) that traind with clip limet 3 and grid size 8 in CLHAE, Gaussian Bluring with Kernel-size of 3 and Laplacian Edge detection with also kernal size of 3, a two-stage sensitivity analysis was conducted. The first stage focused on evaluating different learning rates and batch sizes to determine the optimal training configuration. The second stage analyzed the impact of various image processing parameters on model performance.

After selecting the optimized model configuration for each labeling scheme on the sensitivity analysis, the training process and model evolution were repeated 5 times. The final test results are reported as the mean and standard deviation (Std) of the evaluation metrics across repeated model training instances, to mitigate the effects of random weight initialization and training variability.

<h4 align="center"> Batch and Learning Rate Analysis: </h4>

![ZDa](https://github.com/user-attachments/assets/03bffc44-2692-46f0-be6b-e7c8a183c39f)

<h4 align="center"> Image Processing Parameter Analysis: </h4>

![ZDa2](https://github.com/user-attachments/assets/aa0e8578-f5fb-4b72-8b32-3281ece9d113)

After selecting the best-performing model, further evaluation was conducted under different labeling schemes to better reflect uncertainty and practical needs. Fuzzy labeling wirt fiting MSE loss function was introduced to account for the arbitrary nature of the original class boundaries, which were manually defined without an established reference. In this approach, continuous values between 0 and 1 were assigned to samples based on their distance from class medians. This method helps the model better understand samples that fall near the edges of category definitions. Binary labeling was also tested by collapsing all samples into two categories: cracked (1) and not cracked (0). This binary formulation provides a practical framework for early warning systems to flag high-risk trees. Both fuzzy and binary label experiments used the same training and test splits but with adjusted class distributions. The binary test set contained 128 sequences for class 0 and 514 for class 1. In both cases, the full CNN+LSTM sensitivity analysis was repeated to examine the impact of these alternative labeling strategies on model performance and generalizability.

<h4 align="center"> CNN + LSTM model Results: </h4>

- CNN+LSTM Model Results

<h4 align="center"> <img width="879" height="524" alt="image" src="https://github.com/user-attachments/assets/96465649-0f67-473a-855e-4144ad9a688a" /> </h4>

Overall, the progression from AModel-1 (A = avrage, model one and two trains speratly on north side and south sude of the dield) to Model-5 demonstrated mostly consistent and substantial improvements across all metrics, while model-6 showed high decreases in performance, confirming that Model-5 provided the most balanced and effective configuration. In the end, Model-5 was selected to perform the full sensitivity analysis, as it demonstrated the best overall performance by achieving the highest accuracy, AA, F1-score, precision and recall. This configuration showed stronger generalization and better predictions compared to the other tested models. Therefore, Model-5  was chosen as the reference model for analysis of parameter sensitivity  and fuzzy and binary class labeling .

- Model-5 CNN + LSTM intermediate fusion architecture

h4 align="center"> <img width="909" height="511" alt="image" src="https://github.com/user-attachments/assets/98ca4a84-c50c-4699-911d-4e85b4dedfdb" /> </h4>

- Batch and Learning Rate Sensitivity Analysis Results

<h4 align="center"> <img width="926" height="552" alt="image" src="https://github.com/user-attachments/assets/248b1d5d-cefa-455e-945a-d82336693f20" /> </h4>

Combo-3 (batch size = 8 , learning rate = 0.0001) was selected as the reference configuration for the image processing parameter sensitivity analysis. Although Combo-4 achieved a slightly higher AA score (47.5% vs. 46.7%), the overall performance difference was minimal, and Combo-3 offered a more favorable trade-off across all evaluation metrics. Specifically, it achieved the highest F1-score (47.4%) and maintained strong accuracy (64.5%) and recall (41.2%), indicating balanced and robust predictive power. Given its consistently strong results and stable behavior across key metrics, Combo-3 was chosen as the base configuration for evaluating the effect of image enhancement parameters. 

- Image Processing Parameter Sensitivity Analysis Results

<h4 align="center"> <img width="893" height="533" alt="image" src="https://github.com/user-attachments/assets/7560e363-169c-4394-a4da-4bb4e89328b9" /> </h4>

Among all tested configurations, Combo-1 (clip Limit = 2, grid size = 8, blur kernel = 5 and edge kernel = 1) demonstrated the strongest overall performance across all five metrics. It achieved the highest accuracy (68.8%) and AA (55.7%), with consistent gains in precision (56.3%), recall (45.9%), and F1-score (50.4%). While Combo-0 also performed well, Combo-1 outperformed it by 4.3% in accuracy and 9.0% in AA, offering a more balanced and robust configuration. Given these improvements, Combo-1 was selected as the final setup for image preprocessing parameter sensitivity analysis.

-2024 Data Optimized Mean + Std  Multi-Class Labeling Model Results 

The optimal model-5  configuration integrates the best-performing components identified in both sensitivity analyses. The final training setup uses a batch size of 8 and a learning rate of 0.0001. For image preprocessing, the selected parameters include a CLAHE clip limit of 2, grid size of 8, Gaussian blur kernel size of 5, and Laplacian edge detection kernel size of 1. The table 31 summarizes the average result and Std obtained after training and evaluating this labeling configuration 5 times on the 2024 season dataset. 

<h4 align="center"> <img width="1019" height="330" alt="image" src="https://github.com/user-attachments/assets/cc51c053-0b22-4313-bcd4-c2589fa3a56b" /> </h4>

- Multi-Class Cracking Severity Labels Generalization Result

Using the optimized model-5 , which was first trained and tested on the 2024 season dataset using the multi-class labels, the model was then tested on the 2025 season dataset and demonstrated limited predictive stability. Compared to the same optimized model trained and tested only on the 2024 season, performance degraded substantially . This configuration achieved 35% accuracy, 11.3% AA, 32% precision, 31.6% recall and 31.6% F1-score indicating reduced robustness of predictions under the new seasonal conditions for this labeling scheme.

<h4 align="center"> <img width="777" height="440" alt="image" src="https://github.com/user-attachments/assets/076d0480-e5ba-41d0-bb00-16acb207cbde" /> </h4>

<h4 align="center"> CNN + LSTM model Fuzzy Labeling Results : </h4>

- CNN+LSTM Fuzzy Labling Model Results 

<h4 align="center"> <img width="898" height="445" alt="image" src="https://github.com/user-attachments/assets/cbbf9229-e8f8-4c6d-8736-4e85da669fca" /> </h4>

The results  compare three fuzzy  membership strategies on best preforming model model-5 configuration in original cracking severity labels: Inverse Distance, Triangle, and Gaussian , evaluated using MSE, cosine similarity, and inter-side MSE (section 3.3.7.5). Inverse Distance fuzzy showed moderate performance with MSE at 0.085, cosine similarity at 0.785, and the lowest inter-side MSE at 0.009. Triangle fuzzy delivered the weakest performance, with the highest MSE (0.100, +0.015 vs. Inverse Distance), the lowest cosine similarity (0.750, –0.035), and the worst inter-side MSE (0.017, +0.008). In contrast, Gaussian fuzzy achieved the best overall performance with the lowest MSE (0.066, –0.034 vs. Triangle and –0.019 vs. Inverse Distance), the highest cosine similarity (0.809, +0.059 from Triangle), and competitive inter-side MSE (0.012, –0.005 vs. Triangle and +0.003 vs. Inverse Distance). Based on these results, Gaussian fuzzy was selected as the preferred strategy for the sensitivity analysis, as it provided the best overall predictive quality, even though Inverse Distance had slightly better consistency between the north and south sides but the difference is not significant.

- Batch and Learning Rate Sensitivity Analysis Fuzzy Labels Results

<h4 align="center"> <img width="937" height="464" alt="image" src="https://github.com/user-attachments/assets/3f2ff927-40ef-4491-aa37-abddf6566f4c" /> </h4>

Combo-3 (batch size = 8, learning rate = 0.0001) was selected as the base configuration for the image processing parameter sensitivity analysis. It achieved the highest Cosine Similarity (0.815), a low MSE (0.065), and a competitive Inter Side MSE (0.008). While Combo-12 had the lowest Inter Side MSE (0.005), Combo-3 offered the most balanced performance across all three metrics, making it the suitable choice for the next stage of analysis.

- Image Processing Parameter Sensitivity Analysis Fuzzy Labels Results

<h4 align="center"> <img width="904" height="448" alt="image" src="https://github.com/user-attachments/assets/9ab1d1cf-6120-4596-9438-22eee18a3773" /> </h4>

Among all tested configurations, Combo-4 (clip limit = 9, grid size = 8, blur kernel = 1, and edge kernel = 1) demonstrated the strongest overall performance across all three metrics. It achieved the lowest MSE (0.060), highest Cosine Similarity (0.829), and a low Inter Side MSE (0.007). Although Combo-1 showed a slightly lower Inter Side MSE (0.006, –0.001), it performed worse in both MSE and Cosine Similarity. Given Combo-4’s consistently better results in the majority of evaluation metrics, it was selected as the final setup for fuzzy label image preprocessing parameter sensitivity analysis.

- Optimal Fuzzy Labels model Results Summarized
  
The optimized fuzzy label  Model-5  configuration integrates the best-performing setups identified in both sensitivity analyses. The final training setup uses a batch size of 8 and a learning rate of 0.0001. For image preprocessing, the selected parameters include a CLAHE clip limit of 9, grid size of 8, Gaussian blur kernel size of 1, and Laplacian edge detection kernel size of 1. This combined configuration achieved the best overall performance for fuzzy prediction, with the lowest MSE (0.060), highest Cosine Similarity (0.829), and a low Inter Side MSE (0.007). While one alternative setup reached a slightly lower Inter Side MSE (0.006), it showed weaker results in the other metrics, making this configuration the most reliable and balanced for predicting fuzzy cracking likelihood. CA of 76.6% was calculated using a corresponding hard-label accuracy of 62.3%.

<h4 align="center"> CNN + LSTM model Binary Labeling Results : </h4>

- CNN+LSTM Binary Labling Model Results
Binary labeling  was used to assess whether a tree would develop cracked fruit (1) or not (0). In this section, Model-5 , the best-performing model   under the original cracking severity labels, was converted into a binary classification model, and the CNN+LSTM sensitivity analysis process  was restarted from the beginning accordingly. This binary setup can serve as an initial stage, helping to identify at-risk trees before applying models that predict the specific severity of fruit cracking  and also reflects the best real-world field conditions as there is no human intervention in terms of creation of labels. In binary labeling the evaluation metrics from the original cracking severity labels were used.

- Batch and Learning Rate Sensitivity Analysis Binary Labels Results

<h4 align="center"> <img width="840" height="501" alt="image" src="https://github.com/user-attachments/assets/fe77798a-b29d-4f2f-be17-6a1baa40dd4b" /> </h4>

Combo-7 (batch size = 32, learning rate = 0.001) was chosen as the base configuration for the image processing sensitivity analysis. It showed the best performance across all five evaluation metrics, with the highest accuracy (84.1%), AA (70.4%), precision (75.3%), recall (78.3%), and F1-score (76.6%). Since it clearly performed better than all other combinations, it was selected to continue with the next stage of the analysis.

- Image Processing Parameter Sensitivity Analysis Binary Labels Results

<h4 align="center"> <img width="871" height="519" alt="image" src="https://github.com/user-attachments/assets/dc326dad-bbec-4201-8afd-c0fd8715af5b" /> </h4>

Among all tested configurations, Combo-0 (clip Limit = 3, grid size = 8, blur kernel = 3 and edge kernel = 3) demonstrated the strongest overall performance across all five metrics. It achieved the highest accuracy (84.1%), precision (75.3%), recall (78.3%), and F1-score (76.6%), with an AA of 70.4%. Although Combo-1 showed a slightly higher AA (70.7%, +0.3%), it fell behind in all other metrics, including a 2.8% lower accuracy. Given Combo-0's consistently better results in the majority of evaluation metrics, it was selected as the final setup for image preprocessing parameter sensitivity analysis.

- Optimal Binary Labels model Results Summarized

The optimized binary label  Model-5  configuration integrates the best-performing setups identified in both sensitivity analyses . The final training setup uses a batch size of 32 and a learning rate of 0.001. For image preprocessing, the selected parameters include a CLAHE clip limit of 3, grid size of 8, Gaussian blur kernel size of 3, and Laplacian edge detection kernel size of 3. This combined configuration achieved the highest overall performance, with 84.1% accuracy, 70.4% AA, 75.3% precision, 78.3% recall, and a 76.6% F1-score. Although a slightly higher AA was observed in one alternative setup (+0.3%), it performed worse in all other metrics, making this configuration the most balanced and effective for binary cracking prediction. 

<h4 align="center"> 2025 dataset generalization tests : </h4>
Model generalization across seasons was evaluated for each labeling scheme by examining performance degradation, that is, how much the metrics  increased or decreased when applied to the 2025 dataset. All optimized labeling schemes were first trained and evaluated on the 2024 dataset, and these same optimized models were then applied directly to the independent 2025 dataset for generalization testing. Since the 2024 dataset contains 3,092 three-time-point sequences and the 2025 dataset contains 1,008 sequences, the 2024 data were used as the training/validation source with same validation precent split as before  and the 2025 data were used as the external test set. Generalization was therefore evaluated only in the forward direction (train/validation 2024, test 2025).

-CNN+LSTM tree cracking severity labeling model generalization test results 
Compared to the same optimized model trained and tested only on the 2024 season, performance declined substantially across all evaluation metrics, with accuracy decreasing by -33.8%, AA by -44.4%, precision by -24.3%, recall by -14.3%, and the F1-score by -18.8%, indicating difficulty in maintaining robust performance under new seasonal conditions for this labeling scheme.

<h4 align="center">  <img width="861" height="157" alt="image" src="https://github.com/user-attachments/assets/976a32b1-38d3-4bdf-8ca2-7d6da1b2999c" /> </h4>

-CNN+LSTM tree fuzzy cracking severity labeling model generalization test results
Compared to the same optimized configuration trained and evaluated solely on the 2024 season, all fuzzy-based evaluation metrics exhibited changes across seasons. MSE increased by +0.008, Cosine similarity increased by -0.038, inter-side MSE increased by +0.01 and CA decreased to 68.0% (–8.7%), with the calculation incorporating a hard-label accuracy of 46.0%  indicating that the fuzzy labeling scheme maintained relatively stable performance under the new seasonal conditions.

<h4 align="center"> <img width="772" height="131" alt="image" src="https://github.com/user-attachments/assets/963d2941-e4c1-4b6c-b24e-231bedf42cb2" /> </h4>

-CNN+LSTM tree binary cracking labeling model generalization test results 
Compared to its performance when trained and tested solely on the 2024 season, the binary formulation exhibited clear reductions across all evaluation metrics, with accuracy decreasing by -19.1%, AA by -33.5%, precision by -29.8%, recall by -43.6%, and the F1-score by -37.2%, indicating limited generalization capability under the new seasonal conditions.

<h4 align="center"> <img width="860" height="151" alt="image" src="https://github.com/user-attachments/assets/516aae49-cec9-4afa-8498-d3b4ac6d6787" /></h4>

Cross-season evaluation (train-2024 / test-2025) showed clear differences in how well each labeling scheme retained performance when applied to new seasonal conditions. Generalization was evaluated by examining the deviation of each model’s 2025 results from the expected behavior of its optimized configuration. The three-class model showed the largest degradation. In 2025 it achieved 35.0% accuracy, 11.3% AA, 32.0% precision, 31.6% recall, and an F1-score of 31.6%, indicating that the original hard labeling scheme did not transfer reliably across seasons, suggesting that the model struggled to capture stable patterns in cracking severity under varying environmental and visual conditions. The sharp reductions across all evaluation metrics show that this label structure was not robust for year-to-year prediction, limiting the model’s ability to generalize beyond the conditions present in the training season. The binary model maintained performance more effectively. On the 2025 dataset it reached 65.0% accuracy, 36.9% AA, 61.4% precision, 66.2% recall, and an F1-score of 39.4%, demonstrating that the binary labeling scheme showed limited generalization capability, with accuracy remaining only moderately stable while AA and the other evaluation metrics dropped sharply. The much larger reduction in AA relative to accuracy suggests that cross-side consistency deteriorated considerably under the 2025 conditions, highlighting that the model struggled to maintain reliable and aligned predictions between the two sides of the field when transferred to a new season. The gaussian fuzzy-label model demonstrated the strongest generalization performance, reaching 0.068 MSE, 0.017 inter-side MSE and 68.0% CA on the 2025 dataset, reflecting the smallest performance degradation across seasons and the highest CA relative to the accuracies achieved by the other two labeling schemes, suggesting that the fuzzy label structure supports improved generalization and more stable prediction behavior under new seasonal conditions.

<h4 align="center"> Short Summary: </h4>

In summary, this work demonstrates a complete end-to-end pipeline for predicting pomegranate fruit cracking using multimodal data. By combining RGB and thermal imagery with meteorological features and integrating object detection, segmentation,Tabular data anlaysis, image enhancement, CNN+LSTN sequence modeling and Cross-season generalization evaluation the system achieved strong results under real orchard conditions. The comparative evaluation of labeling strategies further highlights the benefits of binary classification for stable and practical deployment. This repository provides the full implementation and serves as a foundation for future research in agricultural AI applications.

Note: LDA was performed on the original multi-class labels to reduce dimensionality and improve class separation. For the binary and fuzzy setups, the same LDA-transformed features were used, but with updated label definitions. While this allowed for consistent feature representation across tasks, it may have slightly reduced the discriminative power of the projection under the new labeling schemes.


<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a> </p>
