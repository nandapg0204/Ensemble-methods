    
<p> To get started with ensemble methods, clone the repository and follow the examples provided in the examples directory. Ensure you have the necessary dependencies installed, which can be done using pip install -r requirements.txt.</p>

<h1> Ensemble methods </h1>


<dl><dd> Ensemble refers to group of models working together. Ensemble methods are the techniques to build a hybrid model by combining multiple models together.The intuition behind this approach is capitalize on individual models strengths while mitigating their weaknesses.Each model captures slightly different aspect of data making an ensemble more robust. Ensemble methods often perform better compared to indivisual models. The results from all the models in the ensemble are aggregated to form the final result. In classification tasks class with highest voting is predicted as final result where as in regression tasks average of all the results is predicted as final result.</dd></dl>
<p>Note : Models that are used to build a ensemble (strong classifier) are referred as base model or weak classifier.</p> 
<h3>Types of Ensemble methods are </h2>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. Bagging</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Boosting</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. Stacking</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4. Voting</strong></p>

<p> </p>

<dl><dd> <dl><dd> <strong>1. Bagging : </strong>Also referred as bootstrap aggregating. In this ensemble approach, multiple instances of same base model are trained on different subsets of training data. This method aims to capture various patterns from the data by creating diverse training sets. Each subset is randomly selected with replacement, a process known as bootstrap sampling, and each subset has the same number of samples as the original dataset.  These models are trained independently on their respective subsets. A well-known example of this technique is Random Forest, which combines multiple decision trees to improve overall performance </dd></dl> </dd></dl>
<p> </p>
<dl><dd> <dl><dd> <strong>2. Boosting : </strong>In this ensemble approach, models are trained in sequence where each subsequent model focuses on errors made by previous models. The intuition behind this approach is to learn from the mistakes.  </dd></dl></dd></dl>

<dl><dd> <dl><dd>Popular boosting methods are</dd></dl></dd></dl>

<dl><dd> <dl><dd> <dl><dd>  <strong>1. AdaBoosting : </strong> Short form of Adaptive Boosting. In this approach, classifiers are trained sequentially, giving more weight to data points that are misclassified in previous rounds.</dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><strong> Training process :</strong></dd></dl></dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>Step 1. At the start of training, every sample is given the same importance. If there are N samples, each one is assigned a weight of 1 divided by N.The training data looks like the following </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<table border="1" align="center"> <thead>
            <tr>
                <th>Features</th>
                <th>Target</th>
                <th>Weights</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>feature A</td>
                <td>target X</td>
                <td>1 / N</td>
            </tr>
            <tr>
                <td>feature B</td>
                <td>target Y</td>
                <td>1 / N</td>
            </tr>
            <tr>
                <td>feature C</td>
                <td>target X</td>
                <td>1 / N</td>
            </tr>
            <tr>
                <td>feature D</td>
                <td>target Z</td>
                <td>1 / N</td>
            </tr>
        </tbody>
</table>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>
Step 2. A weak classifier is trained on weighted training data. After training, we calculate the error by evaluating the same weak  classifier on same training data. We use this error to increase the weights of the misclassified examples and decrease the weights of the correctly classified ones.Let the α be the error, updated training data looks like the following. </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<table border="1" align="center"> <thead>
            <tr>
                <th>Features</th>
                <th>Target</th>
                <th>Old Weights</th>
                <th>Correctly predicted</th>
                <th>New Weights</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>feature A</td>
                <td>target X</td>
                <td>1 / N</td>
                <td> Yes </td>
                <td>1 / N × exp(−α)</td> 
            </tr>
            <tr>
                <td>feature B</td>
                <td>target Y</td>
                <td>1 / N</td>
                <td> No </td>
                <td> 1 / N × exp(α) </td>
            </tr>
            <tr>
                <td>feature C</td>
                <td>target X</td>
                <td>1 / N</td>
                <td> No </td>
                <td>  1 / N × exp(α) </td>
            </tr>
            <tr>
                <td>feature D</td>
                <td>target Z</td>
                <td>1 / N</td>
                <td> Yes </td>
                <td>  1 / N × exp(-α)</td> 
            </tr>
        </tbody>
</table>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>Step 3. The second weak classifier is trained the weight adjusted data. Then evaluated and weights are adjusted accordingy. This process is repeatly until desired number of weak classifiers are trained. </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd> <dl><dd> <dl><dd> -→ AdaBoost improves accuracy by focusing on mistakes. The loss function is designed to pay more attention for the samples with higher weights.</dd></dl></dd></dl></dd></dl>
<dl><dd> <dl><dd> <dl><dd> -→ The Sklearn version of AdaBoost has two versions boosting algorithms , SAMME(original version) and SAMME.R(updated version). SAMME.R tends to perform better compared to SAMME </dd></dl></dd></dl></dd></dl>

<dl><dd> <dl><dd> <dl><dd>  <strong>1. Gradient Boosting Machines(GBM) : </strong> In GBM, models are trained in sequence, with each subsequent model focuses on residuals to improve ensemble accuracy.
</dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><strong> Training process :</strong></dd></dl></dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>Step 1. Initally a weak classifier is trained on entire training data and then evaluated to calcualte residuals</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<div align="center">
<table border="1" align="center">
    <caption><strong>For Regression (House Price Prediction):</strong></caption>
    <thead>
        <tr>
            <th>Median Income</th>
            <th>Number of Bedrooms</th>
            <th>Target Price</th>
            <th>Predicted Target Price</th>
            <th>Residual</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$60,000</td>
            <td>3</td>
            <td>$350,000</td>
            <td>$340,000</td>
            <td>$10,000</td>
        </tr>
        <tr>
            <td>$75,000</td>
            <td>4</td>
            <td>$450,000</td>
            <td>$460,000</td>
            <td>-$10,000</td>
        </tr>
        <tr>
            <td>$50,000</td>
            <td>2</td>
            <td>$250,000</td>
            <td>$255,000</td>
            <td>-$5,000</td>
        </tr>
        <tr>
            <td>$80,000</td>
            <td>5</td>
            <td>$500,000</td>
            <td>$490,000</td>
            <td>$10,000</td>
        </tr>
    </tbody>
</table>
</div>
<div align = "center">
<table border="1" align="center">
    <caption > <strong>Classification (Binary classification with 0.5 threshold ):</strong> </caption>
    <thead>
        <tr>
            <th>Feature 1</th>
            <th>Feature 2</th>
            <th>True Label</th>
            <th>Predicted probability</th>
            <th>Residual</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>321</td>
            <td>23</td>
            <td>1</td>
            <td>0.75</td>
            <td>0.25</td>
        </tr>
        <tr>
            <td>512</td>
            <td>21</td>
            <td>0</td>
            <td>0.65</td>
            <td>-0.65</td>
        </tr>
        <tr>
            <td>599</td>
            <td>312</td>
            <td>1</td>
            <td>0.85</td>
            <td>0.15</td>
        </tr>
        <tr>
            <td>621</td>
            <td>311</td>
            <td>0</td>
            <td>0.70</td>
            <td>-0.70</td>
        </tr>
    </tbody>
</table>
</div>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>Step 2. The next model is trained to predict these residuals. The training data for sub sequent model looks like the following.</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<div align="center">
<table border="1" align="center">
    <caption><strong>For Regression (House Price Prediction):</strong></caption>
    <thead>
        <tr>
            <th>Median Income</th>
            <th>Number of Bedrooms</th>
            <th>Residual</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$60,000</td>
            <td>3</td>
            <td>$10,000</td>
        </tr>
        <tr>
            <td>$75,000</td>
            <td>4</td>
            <td>-$10,000</td>
        </tr>
        <tr>
            <td>$50,000</td>
            <td>2</td>
            <td>-$5,000</td>
        </tr>
        <tr>
            <td>$80,000</td>
            <td>5</td>
            <td>$10,000</td>
        </tr>
    </tbody>
</table>
</div>
<div align = "center">
<table border="1" align="center">
    <caption > <strong>Classification (Binary classification with 0.5 threshold ):</strong> </caption>
    <thead>
        <tr>
            <th>Feature 1</th>
            <th>Feature 2</th>
            <th>Residual</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>321</td>
            <td>23</td>
            <td>0.25</td>
        </tr>
        <tr>
            <td>512</td>
            <td>21</td>
            <td>-0.65</td>
        </tr>
        <tr>
            <td>599</td>
            <td>312</td>
            <td>0.15</td>
        </tr>
        <tr>
            <td>621</td>
            <td>311</td>
            <td>-0.70</td>
        </tr>
    </tbody>
</table>
</div>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>Step 3. After training the second model, calculate the residuals for the entire ensemble (both the first and second weak classifiers). Use these residuals to train the next model. Repeat this process until you have the desired number of weak classifiers. </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><strong> Advanced Gradient Boosting Techniques :</strong></dd></dl></dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong>1. XGBoost (Extreme Gradient Boosting):</strong> This is an optimized version of GBM with additional features for better performance and efficiency
</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Features :</strong>
</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Regularization: </strong>Adds L1 and L2 regularization to reduce overfitting.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Tree Pruning: </strong> Uses depth-first search for tree growth and pruning.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
 <dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Missing Values Handling: </strong>Supports both CPU and GPU acceleration.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
 <dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Parallel Processing: </strong>Adds L1 and L2 regularization to reduce overfitting.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
  <dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Histogram-Based Splitting: </strong> Uses bins to split data, improving efficiency.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong>2. LightGBM (Light Gradient Boosting Machine):</strong>  Designed for faster training and lower memory usage with large datasets.</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Features :</strong>
</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Histogram-Based Algorithms: </strong> Efficiently handles large datasets by using histogram-based approaches.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
 <dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Speed and Efficiency: </strong>  Optimized for faster training and prediction.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>

<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong>3. CatBoost :</strong>  Handles categorical features automatically and is robust to various data distributions.</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Features :</strong>
</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Categorical Feature Handling: </strong> Directly processes categorical features.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
 <dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Regularization: </strong>   Uses advanced regularization techniques to reduce overfitting.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
 
 
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong>4. Lightning Boost :</strong>  An extension of XGBoost, focusing on faster training and scalability. </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Features :</strong>
</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong>  Improved Efficiency: </strong> Better optimization for large datasets compared to XGBoost.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
 <dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><dl><dd><strong> Accelerated Training: </strong>  Supports both CPU and GPU acceleration.
 </dd></dl></dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>


 <dl><dd> <dl><dd> <strong>3. Stacking ensemble : </strong> Stacking is an ensemble learning method where multiple models are trained together in layers. Several base models are trained, and they can be different types. Then, a meta-model is trained using the predictions from these base models. The idea is that the meta-model learns which base models to trust in different situations. But stacking is less popularly used compared to other ensemble methods. 
 </dd></dl> </dd></dl>
