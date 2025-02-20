.. -*- mode: rst -*-

This if a modified fork of **scikit-learn** v. 1.3.1 which is distributed under the 3-Clause BSD license. Supported versions of Python are 3.8, 3.9 and 3.10!

Here, we propose a simple modification for decision trees, which increases the generalization of the models. A new parameter, **min_groups_leaf**, was added to the splitting rules of decision trees. It represents the number of groups required to be presented in both left and right child nodes when decision tree’s split happens. Such a behavior leads to a significant reduction of the overfitting, although, may suffer from the underfitting. To reduce the latter, if the parent node contains none or only one sample of some group (impossible to split into both child nodes), that group is considered as equally splitted when min_groups_leaf rule is checked.

Details and application are shown in the manuscript: doi:10.1021/acs.jproteome.4c00677.

Installation
------------

Since this fork is outdated version of original scikit-learn package, we suggest to use a standalone virtualenv for installation.

pip3 install https://github.com/markmipt/scikit-learn/archive/refs/heads/min_groups_leaf_131.zip --upgrade --force


Important links
~~~~~~~~~~~~~~~

- Original scikit-learn source code repo: https://github.com/scikit-learn/scikit-learn


Usage example
~~~~~~~~~~~~~

.. code-block:: python

    from sklearn.datasets import load_diabetes
    from sklearn.model_selection import train_test_split
    from sklearn.ensemble import ExtraTreesRegressor
    import random
    X, y = load_diabetes(return_X_y=True)
    G = np.array([random.randint(1,3) for _ in range(len(y))])
    X_train, X_test, y_train, y_test, G_train, G_test = train_test_split(
        X, y, G, random_state=0)
    reg = ExtraTreesRegressor(n_estimators=100, random_state=0, min_groups_leaf=3).fit(
       X_train, y_train, groups=G_train.astype(np.int32))
    reg.score(X_test, y_test)



Citation
~~~~~~~~
If you use modified decision tree in a scientific publication, we would appreciate citations:  doi:XXX 
