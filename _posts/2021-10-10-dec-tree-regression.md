# Starting out in Machine Learning - Decision Trees

As part of working towards an understanding of machine learning algorithms, decision trees are an ideal conceptual starting point. Starting with the data (root), they utilise a tree-like model of conditional statements (nodes) and decisions (branches) to produce outputs (leaves), forming the basis of a predictive model. This tree structure can be multi-layered and complex in order to deal with many possible outcomes given the data and required outcome. A simplified schematic is shown below:

![Decision tree schematic](/img/2021-10-10_dec_tree_reg_imgs/dec_tree_schem.png)

Decision trees can be used with both discrete data for classification, and continuous data for regression. Focusing on regression and using [scikit-learn](https://scikit-learn.org/stable/index.html), we can see how a simple decision tree regression works in practice. Starting with the example [here](https://scikit-learn.org/stable/auto_examples/tree/plot_tree_regression.html#sphx-glr-auto-examples-tree-plot-tree-regression-py), the purpose of the decision tree is to fit the output to the sine curve with the challenge of dealing with the additional noise added to it. From an astrophysics perspective, this noisy sine curve has parallels to a [lightcurve](https://en.wikipedia.org/wiki/Light_curve) from the observation of a star, with the peaks and dips representing the variable brightness, or the [transit](https://en.wikipedia.org/wiki/Methods_of_detecting_exoplanets#Transit_photometry) of an exoplanet across the host star.

To graphically illustrate how this works, using the code example from scikit-learn, we can plot the model fit to the data following these steps:

* Take the input data array - the noisy sine curve
* Fit a decision tree regression model from the input data array
* Use the model on a new generated array of data to produce a fit for plotting

The key parameter for adjusting how well the regression attempts to fit a model to the data is **max_depth**, shown in the legend for plots with regression applied. This is the number of levels for the decision tree regression to use. Starting with the data only, the sine curve and noise are obvious:

![The sine curve with no regression applied.](/img/2021-10-10_dec_tree_reg_imgs/data_only.png)

The first attempt at fitting the model deliberately sets max_depth low enough such that the peak of the sine curve is poorly approximated.

![Regression applied - underfitting](/img/2021-10-10_dec_tree_reg_imgs/data_fit_match_2.png)

A small change in the max_depth parameter from 2 to 3 makes a notable change to the fit, particularly at the peak.

![Regression applied - closer match](/img/2021-10-10_dec_tree_reg_imgs/data_fit_match_3.png)

With an increase to 4, there is a marked change with the decision tree regression overfitting and including specific points of noise.

![Regression applied - overfitting](/img/2021-10-10_dec_tree_reg_imgs/data_fit_match_4.png)

To see how the decision tree model works, we can plot it schematically using [plot_tree](https://scikit-learn.org/stable/modules/generated/sklearn.tree.plot_tree.html#sklearn.tree.plot_tree).

![Decision tree model max_depth = 3](/img/2021-10-10_dec_tree_reg_imgs/data_tree_3.png)

The conditional statements are shown in each node with **mse** referring to [mean squared error](https://en.wikipedia.org/wiki/Mean_squared_error), used as value to determine how good the split at the node is, and is the average of the data points of the data provided. The samples are the number of data points in the input data, and at each node the samples are split between each successive node flowing from top to bottom. This process continues at each node depending on the max_depth value set, giving the final model.
