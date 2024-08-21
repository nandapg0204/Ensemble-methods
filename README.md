
   <style>
        .left-space-small {
            margin-left: 10px; 
        }
    </style>
<p> To get started with ensemble methods, clone the repository and follow the examples provided in the examples directory. Ensure you have the necessary dependencies installed, which can be done using pip install -r requirements.txt.</p>


<h1> Ensemble methods </h1>


<p class = "class="left-space-small">Ensemble refers to group of models working together. Ensemble methods are the techniques to build a hybrid model by combining multiple models together.The intuition behind this approach is capitalize on individual models strengths while mitigating their weaknesses.Each model captures slightly different aspect of data making an ensemble more robust. Ensemble methods often perform better compared to indivisual models. The results from all the models in the ensemble are aggregated to form the final result. In classification tasks class with highest voting is predicted as final result where as in regression tasks average of all the results is predicted as final result.
</p>
<p>Note : Models that are used to build a ensemble (strong classifier) are referred as base model or weak classifier.</p> 
<h3>Types of Ensemble methods are </h2>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. Bagging</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Boosting</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. Stacking</strong></p>
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4. Voting</strong></p>

<p> </p>
<p><strong>1. Bagging : </strong>Also referred as bootstrap aggregating. In this ensemble approach, multiple instances of same base model are trained on different subsets of training data. This method aims to capture various patterns from the data by creating diverse training sets. Each subset is randomly selected with replacement, a process known as bootstrap sampling, and each subset has the same number of samples as the original dataset.  These models are trained independently on their respective subsets. A well-known example of this technique is Random Forest, which combines multiple decision trees to improve overall performance</p>
<p> </p>
<p><strong>2. Boosting : </strong>In this ensemble approach, models are trained in sequence where each subsequent model focuses on errors made by previous models. The intuition behind this approach is to learn from the mistakes.  
</p> 
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Popular boosting methods are </p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>1. AdaBoosting : </strong> Short form of Adaptive Boosting. In this approach, classifiers are trained sequentially, giving more weight to data &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;points that are misclassified in previous rounds. </p>
<p><strong> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Training process :</strong></p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 1. At the start of training, every sample is given the same importance. If there are N samples, each one is assigned a  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;weight of 1 divided by N.The training data looks like the following </p>
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
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 2. A weak classifier is trained on weighted training data. After training, we calculate the error by evaluating the same weak &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; classifier on same training data. We use this error to increase the weights of the misclassified examples and decrease the weights &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  of the correctly classified ones.Let the α be the error, updated training data looks like the following. </p>
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
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 3. The second weak classifier is trained the weight adjusted data. Then evaluated and weights are adjusted accordingy. This &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; process is repeatly until desired number of weak classifiers are trained. </p> 
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-→ AdaBoost improves accuracy by focusing on mistakes. The loss function is designed to pay more attention for the samples with higher weights.</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-→ The Sklearn version of AdaBoost has two versions boosting algorithms , SAMME(original version) and SAMME.R(updated version). SAMME.R tends to perform better compared to SAMME </p>


