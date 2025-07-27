<h1 align="center"> MSC Thesis - Multimodal-Ground-Sensing-for-Prediction-of-Cracking-Severity-in-Pomegranate-Fruit-Trees </h1>
<p align="left">
</p>

<h4 align="center"> Research By: Arad Peleg </h4>
<h4 align="center"> Supervised By: Prof. Yael Edan, Dr. Victor Alchanatis </h4>
<h4 align="center"> Research Collaboration: Yoav Yoktan, Guy Lidor, Roman Brikman, Michael Brener, Assaf Tzur, Idit Ginzberg, Christian Reagan and Manuela Zude </h4>
<h4 align="center"> Institute of Agricultural and Biosystems Engineering, Agricultural Research Organization, Volcani Institute </h4>
<h4 align="center"> Dept. of Industrial Engineering & Management, Ben-Gurion University of the Negev </h4>
<h4 align="center">  Leibniz-Institut für Agrartechnik und Bioökonomie e.V. (ATB), Potsdam, Germany </h4>

Hi 👋, This research investigates the prediction of pomegranate fruit cracking using multimodal deep learning approaches. The work integrates image-based features and temporal metadata extracted from meteorological station and thermal images within a CNN+LSTM architecture, incorporating attention mechanisms to enhance feature representation across time points. Additionally, fuzzy labeling techniques and binary labling are explored to better model uncertainty in cracking severity classification. This research is conducted under the CrackSense project, as a collaboration between Ben-Gurion University of the Negev (Department of Industrial Engineering and Management) and the Volcani Institute, combining expertise in AI, agriculture, and sensing technologies.

CrackSense (https://cracksense.eu/) is a Horizon Europe initiative running from January 2023 to December 2026. It brings together 14 partners from 7 countries to address the challenge of fruit cracking in crops such as citrus, pomegranate, table grapes, and sweet cherries. The project focuses on developing and scaling advanced sensing technologies, aiming to provide real-time sensor data through experimental field trials and pilot implementations. As part of this broader multidisciplinary effort, this thesis contributes to CrackSense’s goal of enhancing precision agriculture through intelligent monitoring and prediction systems.

<img width="246" height="125" alt="תמונה1" src="https://github.com/user-attachments/assets/495506a4-be14-4ea7-a601-0667fad7af31" /> 


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
- 🧠 Fuzzy CNN+LSTM for Model-5 (best performing model)
- 🧠 Binary CNN+LSTM for Model-5 (best performing model)

Data organization is primarily handled in the Model-1 notebook, and adjustments are also generally made in the CNN+LSTM models notebook.

<h4 align="center"> CNN+LSTM model configurations: </h4>

![zda](https://github.com/user-attachments/assets/c51fa4c7-8380-4a2f-a2a7-bb3e68698fe8)

**Note:** The dataset used in this research can be requested via email (aradpls2@gmail.com).

<h4 align="center"> Algorithm Pipe line: </h4>

![NY](https://github.com/user-attachments/assets/02332191-9e82-4a50-9ce6-f5d8158e9915)

This project presents a multimodal deep learning pipeline for predicting pomegranate fruit cracking severity using RGB and thermal images combined with meteorological data. An initial YOLOv8 object detection model, trained with manual annotations and external PG-YOLO data, was fine-tuned and used to detect fruit regions. These detections were then used to generate segmentation masks using the GrabCut algorithm, which refines object boundaries by iteratively separating foreground (fruit) from background (e.g., sky, ground). Segmented images were further processed using a U-Net model to isolate pomegranate regions, followed by image enhancements like CLAHE, Gaussian blurring, and Laplacian edge detection. Thermal and environmental features were extracted and aligned with the images based on timestamps, with feature engineering, multicollinearity checks, and normalization applied. All processed image and tabular inputs were fed into CNN+LSTM models, where CNN handled spatial features and LSTM captured temporal patterns. The final output predicts cracking severity levels for each fruit instance.

<h4 align="center"> YOLOv8 architecture: </h4>

![arc2](https://github.com/user-attachments/assets/45935619-e667-4e1c-9347-050df503705e)

<h4 align="center"> Selected transfer learning technique  for object Detection: </h4>

<img width="565" height="107" alt="TL" src="https://github.com/user-attachments/assets/cb7825f6-4008-4bc2-af23-27a4fa872075" />

To detect pomegranates on trees, we used the YOLOv8s object detection model, chosen for its balance between speed and accuracy. We initially trained the model on an external dataset (PG-YOLO) containing over 13,000 annotated images of pomegranates. After this, we applied transfer learning by fine-tuning the model on a smaller set of 616 manually labeled images from our own orchard data. This allowed the model to adapt to our specific environmental conditions, such as lighting and background variation, while significantly reducing the need for extensive manual annotation. We tested several train-test splits to evaluate the model's robustness under different data conditions and found that the model maintained strong detection capabilities even with smaller training sets. This step provided accurate bounding boxes around fruits, which were then used in the later stages of the pipeline, such as cropping and segmentation.

<h4 align="center"> U-Net architecture: </h4>

![arc3](https://github.com/user-attachments/assets/37ba06bb-3e30-4ee9-8abe-58870ffa8992)

<h4 align="center"> CNN + LSTM general intermediate fusion architecture: </h4>

![ZDA2322223](https://github.com/user-attachments/assets/b3d88d0b-b5c5-4b02-bd23-9c497c3674a5)

<h4 align="center"> Pure LSTM architecture (model-6): </h4>

![WEREBLUE](https://github.com/user-attachments/assets/133cba20-1e5d-4f95-91d9-52a7038d2011)


<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a> </p>
