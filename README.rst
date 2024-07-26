.. -*- mode: rst -*-

This if a modified fork of **scikit-learn** v. 1.3.1 which is distributed under the 3-Clause BSD license.

Here, we propose a simple modification for decision trees, which increases the generalization of the models. A new parameter, min_groups_leaf, was added to the splitting rules of decision trees. It represents the number of groups required to be presented in both left and right child nodes when decision tree’s split happens. Such a behavior leads to a significant reduction of the overfitting, although, may suffer from the underfitting. To reduce the latter, if the parent node contains none or only one sample of some group (impossible to split into both child nodes), that group is considered as equally splitted when min_groups_leaf rule is checked.

Details and application are shown in the manuscript: doi:XXX. 

Website: https://scikit-learn.org

Installation
------------

Since this fork is outdated version of original scikit-learn package, we suggest to use a standalone virtualenv for installation.

pip3 install https://github.com/markmipt/scikit-learn/archive/refs/heads/min_groups_leaf.zip


Important links
~~~~~~~~~~~~~~~

- Original scikit-learn source code repo: https://github.com/scikit-learn/scikit-learn


Usage example
~~~~~~~~~~~~~

clf = ExtraTreesRegressor(min_groups_leaf = 2)

Citation
~~~~~~~~
If you use modified decision tree in a scientific publication, we would appreciate citations:  doi:XXX 
If you use scikit-learn in a scientific publication, we would appreciate citations: https://scikit-learn.org/stable/about.html#citing-scikit-learn
