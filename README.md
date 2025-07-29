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

Image cropping, Thermal image and feature extraction and Fitting thermal and environmental tabular data in Processing notebook.

2. CNN+LSTM Models Code Folder:
- 🧠 All CNN+LSTM model configurations (model 1 to 6)
- 📈 Statistical analysis code for diffrence in field side predictions
- 🧠 Fuzzy labeling CNN+LSTM for Model-5 (best performing model) --> labels created in code notebook
- 🧠 Binary labeling CNN+LSTM for Model-5 (best performing model) --> labels created in code notebook

Data organization is primarily handled in the Model-1 notebook, and adjustments are also generally made in the CNN+LSTM models notebook.

<h4 align="center"> Data Collection: </h4>

<h4 align="center"> <img width="632" height="236" alt="zsa" src="https://github.com/user-attachments/assets/e7a0186c-9fd4-4405-9681-411197677c30" /> </h4>

Data was collected using the TOMMY system, which includes thermal and RGB sensors, between August and November 2024 in Tzara near Beit Shemesh, Israel. Images of the Wonderful pomegranate cultivar were captured under three conditions: at night with artificial lighting, at sunrise with dew on the fruits, and during the day under full sun. Around 4400 images were taken, typically twice per time point. For each tree on one side of the field, a corresponding tree from the opposite side (north and south side of the field) was also imaged to ensure full coverage. The system captured 40–60 images per tree side from different angles along the X-axis to cover the entire canopy. RGB images used autofocus with occasional manual lighting adjustments, while thermal images were manually focused for sharper temperature contrast. All images were visually inspected for quality. A meteorological station was also used to log environmental data every minute during each acquisition session.

<h4 align="center"> <img width="668" height="438" alt="image" src="https://github.com/user-attachments/assets/74c701d7-690a-44f9-8f89-0284929b254a" /> </h4>
 
<h4 align="center"> CNN+LSTM Model Configurations: </h4>

 ![zda](https://github.com/user-attachments/assets/c51fa4c7-8380-4a2f-a2a7-bb3e68698fe8) 

**Note:** The dataset used in this research can be requested via email (aradpls2@gmail.com).

<h4 align="center"> Algorithm Pipe Line: </h4>

![NY](https://github.com/user-attachments/assets/02332191-9e82-4a50-9ce6-f5d8158e9915)

This project presents a multimodal deep learning pipeline for predicting pomegranate fruit cracking severity using RGB and thermal images combined with meteorological data. An initial YOLOv8 object detection model, trained with manual annotations and external PG-YOLO data, was fine-tuned and used to detect fruit regions. These detections were then used to generate segmentation masks using the GrabCut algorithm, which refines object boundaries by iteratively separating foreground (fruit) from background (e.g., sky, ground). Segmented images were further processed using a U-Net model to isolate pomegranate regions, followed by image enhancements like CLAHE, Gaussian blurring, and Laplacian edge detection. Thermal and environmental features were extracted and aligned with the images based on timestamps, with feature engineering, multicollinearity checks, and normalization applied. All processed image and tabular inputs were fed into CNN+LSTM models, where CNN handled spatial features and LSTM captured temporal patterns. The final output predicts cracking severity levels for each fruit instance.

<h4 align="center"> YOLOv8 Architecture: </h4>

![arc2](https://github.com/user-attachments/assets/45935619-e667-4e1c-9347-050df503705e)

- PG YOLO traning set up: 

![ZDAPG](https://github.com/user-attachments/assets/98cbfb1f-f171-4e72-b9bf-8f592cb6aeb9)

- Selected transfer learning technique  for object Detection: 

<img width="565" height="107" alt="TL" src="https://github.com/user-attachments/assets/cb7825f6-4008-4bc2-af23-27a4fa872075" />

- Transfer learning traning set up:

![setups](https://github.com/user-attachments/assets/a619e7ed-b0b5-4e0a-9e73-f07c67d880db)

To detect pomegranates on trees, we used the YOLOv8s object detection model, chosen for its balance between speed and accuracy. We initially trained the model on an external dataset (PG-YOLO) containing over 13,000 annotated images of pomegranates. After this, we applied transfer learning by fine-tuning the model on a smaller set of 616 manually labeled images from our own orchard data. This allowed the model to adapt to our specific environmental conditions, such as lighting and background variation, while significantly reducing the need for extensive manual annotation. We tested several train-test splits to evaluate the model's robustness under different data conditions and found that the model maintained strong detection capabilities even with smaller training sets. This step provided accurate bounding boxes around fruits, which were then used in the later stages of the pipeline, such as cropping and segmentation.

- Sensitivity analysis split testing on transfer learning model: 

![SPLOT](https://github.com/user-attachments/assets/9ab27e2f-2587-47ed-b9dc-6f2e83f263df)


<h4 align="center"> YOLOv8 Pomegranate Detection Results : </h4>

YOLOv8 pomegranate detection transfer learning result:

![ZDAresutls](https://github.com/user-attachments/assets/1d71a923-cdef-47c0-b446-e138ff1a7823)

- Raw Transfer
<img width="875" height="318" alt="image" src="https://github.com/user-attachments/assets/40bf9516-3677-4c32-9eb6-c5a4342e2926" />

- Fine tuned model

<img width="857" height="312" alt="image" src="https://github.com/user-attachments/assets/2d674b70-c1f5-47a0-9a16-8f3cb5c2b85b" />

- Raw trnsfer Vs Fine tuned model precision recall curve

<img width="1015" height="347" alt="image" src="https://github.com/user-attachments/assets/d09da223-846b-4ddc-ba4a-c745123bba28" />

- Sensitivity analysis split testing on transfer learning reuslts: 

<img width="826" height="626" alt="image" src="https://github.com/user-attachments/assets/3562174c-84aa-4b99-8002-caa5e772ea2d" />

The object detection split tests showed minor differences across the four configurations. Test 1 achieved strong overall performance with mAP50 of 86.6%, mAP50-95 of 54.1%, and F1-score of 82.0%, reflecting high detection accuracy and good localization. Although Test 2 had slightly higher mAP50 (86.9%) and precision (87.1%), it showed a small drop in mAP50-95. Test 3 yielded similar results, while Test 4 had the weakest performance. In the end, Test 1 was selected for generating bounding boxes for Grab-Cut segmentation due to its consistent advantage in localization and recall, offering the best trade-off for precise mask generation.

<h4 align="center"> Grab Cut Algorithm: </h4>

- Exmaple mask creation

<img width="936" height="343" alt="image" src="https://github.com/user-attachments/assets/329035d0-40de-4273-bb09-4e45b60ced48" />

The mean SSIM  score between the YOLO-cropped RGB images and the corresponding Grab-Cut masks was 87.6%, indicating a high level of structural similarity. This suggests that the Grab-Cut algorithm (section  generally succeeded in preserving the shape and spatial structure of the objects identified by YOLO.

<h4 align="center"> U-Net Segmentation Architecture: </h4>

![arc3](https://github.com/user-attachments/assets/37ba06bb-3e30-4ee9-8abe-58870ffa8992)

We used the U-Net architecture for segmenting pomegranates from RGB images. U-Net is ideal for image segmentation, especially when working with small datasets, thanks to its encoder-decoder structure and skip connections. We tested different backbones: ResNet-50, which uses residual connections to support deep architectures, and EfficientNet-B7, which balances network scaling for higher accuracy. The segmentation masks were generated from manually cropped images (using bounding boxes from the detection model) and resized to 160×256 for compatibility with the network. We trained the model using CrossEntropyLoss and optimized it with the AdamW optimizer. Pretrained ImageNet weights were used in some experiments to improve convergence. A learning rate scheduler (ReduceLROnPlateau) was applied to dynamically adjust training progress. The final output of the model is a binary mask identifying pomegranate regions, which is later used for downstream prediction tasks.

- Segmentation models Sensitivity Analysis Testing 

![ZDAseef](https://github.com/user-attachments/assets/93436488-e4e8-4090-b3ec-df66e5737adb)

<h4 align="center"> Pomegranate Segmentation Results: </h4>

- Pomegranate Segmentation Results

  <img width="855" height="586" alt="image" src="https://github.com/user-attachments/assets/1b28859f-bf5d-4c08-90c6-d506cfd9b355" />

- Pomegranate Segmentation Example

<h4 align="center"> <img width="560" height="624" alt="image" src="https://github.com/user-attachments/assets/2b1b5297-08d4-4d02-9fc4-494a23151cab" /> </h4>

The segmentation tests evaluated three configurations using IoU, precision, recall, and F1-score. Test 1, which lacked data augmentation, produced the lowest results with an IoU of 82% and an F1-score of 80.3%, indicating poor generalization. Test 2 introduced data augmentation, leading to a 2.8% increase in IoU, a 7.7% rise in recall, and a 3.7% improvement in F1-score, showing better robustness. Test 3, which used EfficientNet-B7 as the backbone, achieved the highest precision at 89.1%, a slight IoU improvement, and maintained strong recall and F1-score. In the end, Test 3 was selected to segment the entire dataset due to its superior overall performance and more accurate pomegranate segmentation. Its predictions were used as input for the CNN+LSTM models.

<h4 align="center"> CNN + LSTM General Intermediate Fusion Architecture: </h4>

![ZDA2322223](https://github.com/user-attachments/assets/b3d88d0b-b5c5-4b02-bd23-9c497c3674a5)

<h4 align="center"> Pure LSTM Architecture (model-6): </h4>

![WEREBLUE](https://github.com/user-attachments/assets/133cba20-1e5d-4f95-91d9-52a7038d2011)

The core model CNN+LSTM architecture for prediction of cracking severity is based on intermediate fusion, where separate streams process each modality in parallel. A convolutional neural network (CNN) extracts spatial features from each of the three RGB image crops, which are then flattened to prepare for fusion. Flattening is necessary because fully connected layers require fixed-length input vectors. Meanwhile, a long short-term memory (LSTM) network processes the sequence of tabular features over the same three time points, producing a final hidden state that captures temporal dependencies. The flattened CNN features and the final LSTM hidden state are then concatenated into a single joint representation. This combined vector is passed through a series of fully connected layers with ReLU activations and dropout for regularization. These layers progressively reduce the dimensionality and enable the model to learn complex relationships between spatial and temporal information. The final output layer produces class logits, which are converted to class probabilities using a softmax function.

Six model configurations were developed to progressively incorporate different enhancements. Model 1 used a basic ResNet-50 backbone with no image processing or feature engineering and served as a baseline. Model 2 introduced a ConvNeXt backbone, custom penalty matrix loss, feature engineering, and label fusion for classes 2 and 3 due to limited sample size. Model 3 added Linear Discriminant Analysis (LDA) on the tabular data and switched to focal loss. Model 4 applied grayscale transformation and CLAHE to the images. Model 5 added Gaussian blur and Laplacian edge detection to the previous configuration. Model 6 applied LDA jointly to both tabular and CNN-extracted image features and used a pure LSTM architecture, differing from the intermediate fusion models used earlier. All models except Model 6 utilized CNN+LSTM intermediate fusion, where CNN and LSTM branches are trained in parallel, and their outputs are merged before the final decision layer.

Data splitting followed a standard 80-20 rule, with 80 percent used for training and 20 percent for testing. From the training set, 20 percent was further set aside for validation. In early experiments (Models 1 and 2), the dataset was split based on the tree row’s orientation (north or south) to determine whether location had an impact on cracking behavior. Later models combined data from both rows after statistical tests confirmed no significant differences in cracking behavior or prediction variance. When split by row, there were 980 training, 245 validation, and 321 test samples per side. When combined, the dataset included 1960 training, 490 validation, and 642 test samples. All models were trained with a batch size of 16 and an initial learning rate of 0.001. Early models were trained for 10 epochs, while all subsequent models were trained for 30. Model weights corresponding to the lowest validation loss were saved and used for final evaluation. Notably, the test set contained only class 0 and class 2 samples, comprising 334 and 298 three-time-point sequences, respectively. After identifying the best-performing model (model-5) that traind with clip limet 3 and grid size 8 in CLHAE, Gaussian Bluring with Kernel-size of 3 and Laplacian Edge detection with also kernal size of 3, a two-stage sensitivity analysis was conducted. The first stage focused on evaluating different learning rates and batch sizes to determine the optimal training configuration. The second stage analyzed the impact of various image processing parameters on model performance.

<h4 align="center"> Batch and Learning Rate Analysis: </h4>

![ZDa](https://github.com/user-attachments/assets/03bffc44-2692-46f0-be6b-e7c8a183c39f)

<h4 align="center"> Image Processing Parameter Analysis: </h4>

![ZDa2](https://github.com/user-attachments/assets/aa0e8578-f5fb-4b72-8b32-3281ece9d113)

After selecting the best-performing model, further evaluation was conducted under different labeling schemes to better reflect uncertainty and practical needs. Fuzzy labeling wirt fiting MSE loss function was introduced to account for the arbitrary nature of the original class boundaries, which were manually defined without an established reference. In this approach, continuous values between 0 and 1 were assigned to samples based on their distance from class medians. This method helps the model better understand samples that fall near the edges of category definitions. Binary labeling was also tested by collapsing all samples into two categories: cracked (1) and not cracked (0). This binary formulation provides a practical framework for early warning systems to flag high-risk trees. Both fuzzy and binary label experiments used the same training and test splits but with adjusted class distributions. The binary test set contained 128 sequences for class 0 and 514 for class 1. In both cases, the full CNN+LSTM sensitivity analysis was repeated to examine the impact of these alternative labeling strategies on model performance and generalizability.

<h4 align="center"> CNN + LSTM model Results: </h4>


<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a> </p>
