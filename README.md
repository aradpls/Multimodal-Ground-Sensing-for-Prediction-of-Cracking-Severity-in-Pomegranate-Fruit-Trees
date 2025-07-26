<h1 align="center"> MSC Thesis - Multimodal-Ground-Sensing-for-Prediction-of-Cracking-Severity-in-Pomegranate-Fruit-Trees </h1>
<p align="left">
</p>

<h4 align="center">Thesis By: Arad Peleg </h4>

Hi 👋, This thesis investigates the prediction of pomegranate fruit cracking using multimodal deep learning approaches. The work integrates image-based features and temporal metadata extracted from meteorological station and thermal images within a CNN+LSTM architecture, incorporating attention mechanisms to enhance feature representation across time points. Additionally, fuzzy labeling techniques and binary labling are explored to better model uncertainty in cracking severity classification.

<strong> 📁 In this repository You will have access to:</strong> 
1. Preprocessing Models Code Folder:
- 📦 Object detection model code (YOLOv8)
- 🧩 Segmentation model code (including GrabCut and augmantion code)
- ✂️ Image cropping code (RGB and Thermal sensors)
- 🌡️ Thermal feature extraction code

2. CNN+LSTM Models Code Folder
- 🧠 All CNN+LSTM model configurations (model 1 to 6)
- 📈 Statistical analysis code
- 🧠 Fuzzy CNN+LSTM for Model-5 (best performing model)
- 🧠 Binary CNN+LSTM for Model-5 (best performing model)

<h4 align="center"> CNN+LSTM model configurations: </h4>



**Note:** The dataset used in this research can be requested via email (aradpls2@gmail.com).

<h4 align="center"> Algorithm Pipe line: </h4>

![NY](https://github.com/user-attachments/assets/02332191-9e82-4a50-9ce6-f5d8158e9915)

<h4 align="center"> YOLOv8 architecture: </h4>

![arc2](https://github.com/user-attachments/assets/45935619-e667-4e1c-9347-050df503705e)

<h4 align="center"> Selected transfer learning technique  for object Detection: </h4>

<img width="565" height="107" alt="TL" src="https://github.com/user-attachments/assets/cb7825f6-4008-4bc2-af23-27a4fa872075" />

<h4 align="center"> U-Net architecture: </h4>

![arc3](https://github.com/user-attachments/assets/37ba06bb-3e30-4ee9-8abe-58870ffa8992)

<h4 align="center"> CNN + LSTM general intermediate fusion architecture: </h4>

![ZDA2322223](https://github.com/user-attachments/assets/b3d88d0b-b5c5-4b02-bd23-9c497c3674a5)

<h4 align="center"> Pure LSTM architecture: </h4>

![WEREBLUE](https://github.com/user-attachments/assets/133cba20-1e5d-4f95-91d9-52a7038d2011)


<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a> </p>
