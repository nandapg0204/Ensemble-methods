<h1> Ensemble methods </h1>


<p> Ensemble refers to group of models working together. Ensemble methods are the techniques to build a hybrid model by combining multiple models together.The intuition behind this approach is capitalize on individual models strengths while mitigating their weaknesses.Each model captures slightly different aspect of data making an ensemble more robust. Ensemble methods often perform better compared to indivisual models. The results from all the models in the ensemble are aggregated to form the final result. In classification tasks class with highest voting is predicted as final result where as in regression tasks average of all the results is predicted as final result.
</p>
<p>Note : Models that are used to build a ensemble (strong classifier) are referred as base model or weak classifier.</p> 
<h3>Types of Ensemble methods are </h2>
<li><strong>    1. Bagging</strong></li>
<li><strong>    2. Boosting</strong></li>
<li><strong>    3. Stacking</strong></li>
<li><strong>    4. Voting</strong></li>
<h3>1. Bagging : </h3><p> Also reffered as bootstrap aggregating. In this ensemble approach, multiple instances of same base model are trained on different subsets of training data. This technique tries to capture diverse patterns from training data. For training each weak classifier,a subset of training data is randomly selected with replacement(also called as bootstrap sampling). Each of these subsets are unique and have same number of training samples as original training dataset. All these weak classifiers are trained independently.A common example is Random Forest, built by boostrapping multiple decision trees</p>


