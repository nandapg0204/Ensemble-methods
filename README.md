<p> To get started with ensemble methods, clone the repository and follow the examples provided in the examples directory. Ensure you have the necessary dependencies installed, which can be done using pip install -r requirements.txt.</p>


<h1> Ensemble methods </h1>


<p> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ensemble refers to group of models working together. Ensemble methods are the techniques to build a hybrid model by combining multiple models together.The intuition behind this approach is capitalize on individual models strengths while mitigating their weaknesses.Each model captures slightly different aspect of data making an ensemble more robust. Ensemble methods often perform better compared to indivisual models. The results from all the models in the ensemble are aggregated to form the final result. In classification tasks class with highest voting is predicted as final result where as in regression tasks average of all the results is predicted as final result.
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
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. At the start of training, every sample is given the same importance. If there are N samples, each one is &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;assigned a weight of 1 divided by N.</p>
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
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. </p>
