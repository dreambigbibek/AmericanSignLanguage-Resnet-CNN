# AmericanSignLanguage-Resnet-CNN
A MATLAB-based deep learning project for American Sign Language (ASL) alphabet recognition using transfer learning on ResNet-18. Includes preprocessing, training, and evaluation using imageDatastore and augmentedImageDatastore.

🚀 Features
Transfer learning using ResNet-18

Image preprocessing using augmentedImageDatastore

Trained to classify 26 ASL alphabet hand gestures (A–Z)

Visualizes training progress using built-in training plots

Utilizes MATLAB's new high-level APIs (trainnet, imagePretrainedNetwork)

🛠️ Tools & Technologies
MATLAB R2023b+

Deep Learning Toolbox

ResNet-18 (pretrained on ImageNet)

📊 Model Training
Images are resized to 224×224×3 and converted to RGB if grayscale.
The classifier is trained using cross-entropy loss and the Adam optimizer:

matlab
Copy
Edit
resnet18 = imagePretrainedNetwork("resnet18", "NumClasses", 26);
options = trainingOptions("adam", ...
    "ValidationData", augmented_imdsTest, ...
    "Shuffle", "every-epoch", ...
    "Plots", "training-progress");

resnet18ASL = trainnet(augmented_imdsTrain, resnet18, "crossentropy", options);
🔍 How to Use
Clone this repository:

bash
Copy
Edit
git clone https://github.com/your-username/asl-resnet-transfer-learning.git
cd asl-resnet-transfer-learning
Open MATLAB, and set the current folder to the repo.

Add the folder to the path:

matlab
Copy
Edit
addpath(genpath(pwd));
Run the model (if P-code and model files are provided):

matlab
Copy
Edit
testASLmodel
⚠️ Note: Ensure supporting files like trainedResNet18ASL.mat and the test image folder are in place.

📁 Dataset
The dataset should contain 26 folders (A–Z), each with corresponding ASL images.
It should be loaded using imageDatastore with labels from folder names.

📈 Results
Metric	Value
Accuracy	~90–95%
Input Size	224x224x3
Classes	26 (A–Z)
Epochs	5 (customizable)

You can increase MaxEpochs or fine-tune more layers for higher accuracy.

📌 TODOs
 Add custom evaluation script

 Add confusion matrix

 Deploy as a MATLAB App or web service

📜 License
This project is for educational purposes. If dataset or pretrained weights are included, check their respective licenses before public use.

