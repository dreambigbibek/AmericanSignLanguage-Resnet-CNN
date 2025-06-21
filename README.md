# AmericanSignLanguage-Resnet-CNN
A MATLAB-based deep learning project for American Sign Language (ASL) alphabet recognition using transfer learning on ResNet-18. Includes preprocessing, training, and evaluation using imageDatastore and augmentedImageDatastore.

## 🚀 Features

- Transfer learning using **ResNet-18**
- Image resizing and preprocessing using `augmentedImageDatastore`
- ASL alphabet classification (A–Z, 26 classes)
- Training visualization via `training-progress` plot
- Uses `trainnet` and `imagePretrainedNetwork` (MATLAB R2023b+)

---

## 🛠️ Technologies

- MATLAB R2023b+
- Deep Learning Toolbox
- ResNet-18 (pretrained on ImageNet)

---

## 📊 Model Training

Images are resized to **224×224×3** and converted to RGB if needed.  
The model is trained with **cross-entropy loss** and the **Adam optimizer**:

```matlab
resnet18 = imagePretrainedNetwork("resnet18", "NumClasses", 24);

options = trainingOptions("adam", ...
    "ValidationData", augmented_imdsTest, ...
    "Shuffle", "every-epoch", ...
    "Plots", "training-progress", ...
    "MaxEpochs", 5, ...
    "MiniBatchSize", 32);

resnet18ASL = trainnet(augmented_imdsTrain, resnet18, "crossentropy", options);
