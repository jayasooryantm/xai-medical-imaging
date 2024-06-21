# xai-medical-imaging

## Training

Dataset : Kaggle Dataset - [Chest X-Ray Images (Pneumonia)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia)
Model: Resnet50 (PyTorch In-Build Model)

Data Transforms:
 - Image Resize to 244 x 244
 - Random Horizondal Flip
 - Normalise (mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.224])

Sampler used in the dataset:
 - Weighted Random Sampler: Since the classes are not balanced in terms of number of images (Normal: 1341, Pneumonia: 3875) weighted random sampler is used to address the issue.

Training with Resnet50 aquired:
Training Accuracy: 100%
Training Loss: 0.000984

Testing With retrained Resnet50 aquired:
Accuracy: 0.3157
Precision: 0.4317
Recall: 0.3000
F1 Score: 0.3540

> The metrics indicate that Model is overfitted (high accuracy and low loss during training and low accuracy, precision and recall) model/data need revision.
