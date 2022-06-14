# Brazilian-Coins-Classifier
Implementation of a "mini DenseNet" for classificating coins of the Brazilian Real currency (BRL)


# Problem preseintation
In this dataset there are five type of coins of the brazilian currency "Real".
 
The coins are classified as:
    
- 5 cents
- 10 cents
- 25 cents
- 50 cents
- 100 cents
    
There are 2190 samples for training and 544 samples for testing. The samples are RGB images 640x480
    
You can download the original dataset from [Kaggle Brazilian Conis Dataset](https://www.kaggle.com/datasets/volodymyrgavrysh/brazilian-coins-dataset-classification25k-images)
    
Ps:
    
Although the dataset is well organized i found some misclassified samples in the test folder and some images where the coin wasn't visible in both train and test folders.
    
For this notebook the outliers have been removed
    
# Mini Densenet
<pre>
    Layer         | Filters | block                |
    --------------|---------|----------------------|
    Convolution   | 32      | Conv7x7 stride=2     |
    --------------|---------|----------------------|
    Pooling       |         | MaxPool3x3 stride=2  |
    --------------|---------|----------------------|----|
    Dense Block 1 | 64      | Conv1x1              |    |
                  | 16      | Conv3x3              | X3 |
    --------------|---------|----------------------|----|
    Transition 1  | 32      | Conv1x1              |
                  |         | AvgPool2x2 stride=2  |
    --------------|---------|----------------------|----|
    Dense Block 2 | 64      | Conv1x1              |    |
                  | 16      | Conv3x3              | X6 |
    --------------|---------|----------------------|----|
    Transition 2  | 32      | Conv1x1              |
                  |         | AvgPool2x2 stride=2  |
    --------------|---------|----------------------|----|
    Dense Block 3 | 64      | Conv1x1              |    |
                  | 16      | Conv3x3              | X5 |
    --------------|---------|----------------------|----|
    Pooling       |         | GlobalAvgPool        |
    --------------|---------|----------------------|
    Output        |         | Softmax              |
    --------------|---------|----------------------|
    </pre>

[DenseNet paper](https://paperswithcode.com/method/densenet)
