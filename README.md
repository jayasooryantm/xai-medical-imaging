# xai-medical-imaging

## Training - Experiment 1

Dataset : Kaggle Dataset - [Chest X-Ray Images (Pneumonia)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia)
Model: Resnet50 (PyTorch In-Build Model)

Data Transforms:

- Image Resize to 244 x 244
- Random Horizondal Flip
- Normalise (mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.224])

Sampler used in the dataset:

- Weighted Random Sampler: Since the classes are not balanced in terms of number of images (Normal: 1341, Pneumonia: 3875) weighted random sampler is used to address the issue.

Training with Resnet50 aquired:

- Training Accuracy: 100%
- Training Loss: 0.000984

Testing With retrained Resnet50 aquired:

- Accuracy: 0.3157
- Precision: 0.4317
- Recall: 0.3000
- F1 Score: 0.3540

> The metrics indicate that Model is overfitted (high accuracy and low loss during training and low accuracy, precision and recall) model/data need revision.

## Training - Experiment 2

> During the output cross verification with actual target variable, more normal cases are predicted. even though the image is from a Pneumonia patient, model predicted it as normal (no bacterial infection) xray image. Maybe the reason for this is `WeightedRandomSampler` where the sampler impose weightage to minor class which is normal. Sampler is removed and model is re-trained with same dataset (No other changes in the code)

Training with Resnet50 aquired:

- Train Accuracy: 95.25%
- Train Loss: 0.1274

Testing With retrained Resnet50 aquired:

- Accuracy: 0.8173
- Precision: 0.7828
- Recall: 0.9795
- F1 Score: 0.8702

<img src="Assets/XAIM-16 Training Accuracy.png" width="500px" height="300px"/>
<img src="Assets/XAIM-16 Training Epoch Loss.png" width="500px" height="300px"/>


> It is evident that sampler was influencing the accuracy of the model. without the sampler train accuracy is 95% and test accuracy is almost 82% which is a great leap from 31% accuracy. now model is performing better. let's make it even better
