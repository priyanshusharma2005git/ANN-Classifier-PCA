<div align="center">

<h1>ANN Classification with PCA</h1>

<p>
  A Deep Learning classification project combining
  <b>Principal Component Analysis (PCA)</b> with an
  <b>Artificial Neural Network (ANN)</b> using PyTorch.
</p>

<p>
  <img src="https://img.shields.io/badge/Python-3.13-blue?style=for-the-badge&logo=python">
  <img src="https://img.shields.io/badge/PyTorch-Deep%20Learning-red?style=for-the-badge&logo=pytorch">
  <img src="https://img.shields.io/badge/PCA-Dimensionality%20Reduction-purple?style=for-the-badge">
  <img src="https://img.shields.io/badge/Scikit--Learn-ML-orange?style=for-the-badge&logo=scikit-learn">
</p>

</div>

<hr>

<h2>Overview</h2>

<p>
This project combines <b>Principal Component Analysis (PCA)</b> and an
<b>Artificial Neural Network (ANN)</b> to perform multi-class classification
on the Date Fruit dataset.
</p>

<p>
The main goal of using PCA is to reduce the dimensionality of the dataset
while retaining <b>95% of the variance</b>, and then use the reduced
features as input to the neural network.
</p>

<hr>

<h2>Dataset</h2>

<p>
The project uses the <b>DateFruit Dataset</b> containing
<b>898 samples</b> and 34 input features.
</p>

<p>
The target column is:
</p>

<pre><code>Class</code></pre>

<p>The dataset contains 7 classes:</p>

<table>
<tr>
<th>Class</th>
<th>Fruit Variety</th>
</tr>

<tr>
<td>1</td>
<td>BERHI</td>
</tr>

<tr>
<td>2</td>
<td>DEGLET</td>
</tr>

<tr>
<td>3</td>
<td>DOKOL</td>
</tr>

<tr>
<td>4</td>
<td>IRAQI</td>
</tr>

<tr>
<td>5</td>
<td>ROTANA</td>
</tr>

<tr>
<td>6</td>
<td>SAFAVI</td>
</tr>

<tr>
<td>7</td>
<td>SOGAY</td>
</tr>

</table>

<hr>

<h2>Why PCA?</h2>

<p>
The original dataset contains <b>34 numerical features</b>.
PCA was used to reduce the number of dimensions while preserving
<b>95% of the variance</b>.
</p>

<div align="center">

<pre>
Original Features
      │
      │
      ▼
  34 Features
      │
      ▼
StandardScaler
      │
      ▼
      PCA
  95% Variance
      │
      ▼
  9 Components
</pre>

</div>

<p>
After applying PCA, the training data was reduced from
<b>34 features to 9 principal components</b>.
</p>

<hr>

<h2>Data Preprocessing</h2>

<ul>
<li>Load the Date Fruit dataset using Pandas</li>
<li>Separate features and target</li>
<li>Encode the target classes using <b>LabelEncoder</b></li>
<li>Split the data into training and testing sets</li>
<li>Standardize features using <b>StandardScaler</b></li>
<li>Apply PCA while retaining 95% variance</li>
<li>Convert the reduced data into PyTorch tensors</li>
</ul>

<p>
The dataset is divided using an <b>80/20 train-test split</b>.
</p>

<hr>

<h2>ANN Architecture</h2>

<p>
The reduced PCA features are passed into a fully connected neural network.
The network contains two hidden layers.
</p>

<table>
<tr>
<th>Layer</th>
<th>Configuration</th>
</tr>

<tr>
<td>Input Layer</td>
<td>9 PCA Components</td>
</tr>

<tr>
<td>Hidden Layer 1</td>
<td>64 Neurons + ReLU</td>
</tr>

<tr>
<td>Hidden Layer 2</td>
<td>64 Neurons + ReLU</td>
</tr>

<tr>
<td>Output Layer</td>
<td>7 Classes</td>
</tr>

</table>

<h3>Architecture</h3>

<div align="center">

<pre>
        PCA Features
       9 Components
             │
             ▼
    ┌─────────────────┐
    │   Linear Layer  │
    │      9 → 64     │
    └────────┬────────┘
             │
           ReLU
             │
             ▼
    ┌─────────────────┐
    │   Linear Layer  │
    │     64 → 64     │
    └────────┬────────┘
             │
           ReLU
             │
             ▼
    ┌─────────────────┐
    │   Output Layer  │
    │      64 → 7     │
    └────────┬────────┘
             │
             ▼
       7 Classes
</pre>

</div>

<hr>

<h2>Training</h2>

<table>
<tr>
<th>Parameter</th>
<th>Value</th>
</tr>

<tr>
<td>Epochs</td>
<td>100</td>
</tr>

<tr>
<td>Batch Size</td>
<td>32</td>
</tr>

<tr>
<td>Optimizer</td>
<td>Adam</td>
</tr>

<tr>
<td>Loss Function</td>
<td>Cross Entropy Loss</td>
</tr>

<tr>
<td>Activation Function</td>
<td>ReLU</td>
</tr>

<tr>
<td>PCA Variance</td>
<td>95%</td>
</tr>

</table>

<p>
During training, the loss decreased from approximately
<b>1.66</b> in the first epoch to approximately
<b>0.07</b> by the 100th epoch.
</p>

<hr>

<h2>Results</h2>

<div align="center">

<h1>91.11%</h1>

<p><b>Test Accuracy</b></p>

</div>

<table>
<tr>
<th>Metric</th>
<th>Result</th>
</tr>

<tr>
<td>Total Test Samples</td>
<td>180</td>
</tr>

<tr>
<td>Correct Predictions</td>
<td>164</td>
</tr>

<tr>
<td>Accuracy</td>
<td><b>91.11%</b></td>
</tr>

</table>

<hr>

<h2>Project Workflow</h2>

<div align="center">

<pre>
Date Fruit Dataset
        ↓
Data Exploration
        ↓
Feature / Target Separation
        ↓
Label Encoding
        ↓
Train-Test Split
        ↓
StandardScaler
        ↓
PCA
        ↓
34 Features → 9 Components
        ↓
PyTorch Tensors
        ↓
DataLoader
        ↓
ANN Model
        ↓
Training
        ↓
Model Evaluation
        ↓
91.11% Accuracy
</pre>

</div>

<hr>

<h2>Technologies Used</h2>

<table>
<tr>
<th>Technology</th>
<th>Purpose</th>
</tr>

<tr>
<td>Python</td>
<td>Programming Language</td>
</tr>

<tr>
<td>Pandas</td>
<td>Data Loading and Analysis</td>
</tr>

<tr>
<td>NumPy</td>
<td>Numerical Operations</td>
</tr>

<tr>
<td>Scikit-learn</td>
<td>Preprocessing, Scaling, Encoding and PCA</td>
</tr>

<tr>
<td>PyTorch</td>
<td>ANN Development and Training</td>
</tr>

</table>

<hr>

<h2>Key Learning</h2>

<ul>
<li>Understanding Principal Component Analysis</li>
<li>Dimensionality Reduction using PCA</li>
<li>Preserving 95% of dataset variance</li>
<li>Combining PCA with Deep Learning</li>
<li>Building an ANN using PyTorch</li>
<li>Working with PyTorch Tensors</li>
<li>Using TensorDataset and DataLoader</li>
<li>Multi-Class Classification</li>
<li>Using Cross Entropy Loss</li>
<li>Using the Adam Optimizer</li>
<li>Evaluating a classification model</li>
</ul>

<hr>

<h2>Project Structure</h2>

<pre>
ANN-Classification-PCA/
│
├── ANN_Classification_pca.ipynb
├── DateFruit_Dataset.csv
└── README.md
</pre>

<hr>

<h2>Conclusion</h2>

<p>
This project demonstrates how <b>dimensionality reduction</b> can be
combined with <b>Deep Learning</b> for a classification task.
</p>

<p>
PCA reduced the original <b>34 features to 9 components</b> while
retaining 95% of the variance. These components were then used to train
an ANN classifier, which achieved a test accuracy of
<b>91.11%</b>.
</p>

<hr>

<div align="center">

<h3>ANN Classification with PCA</h3>

<p>
Built with Python, Scikit-learn & PyTorch
</p>

</div>
