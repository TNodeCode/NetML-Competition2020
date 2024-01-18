# NetML Challenge Solution

This repository contains a solution for the NetML Challenge presented in this paper: https://arxiv.org/pdf/2004.13006.pdf

## How to use this repository

You first need to download all the training data from this site: https://github.com/ACANETS/NetML-Competition2020/tree/master/data/non-vpn2016

Place the following files in the root directory of this project:

- 2_training_set.json
- 2_training_anno_top.json
- 2_training_anno_mid.json
- 2_training_anno_fine.json

Next you need to run the notebook ***Data Analysis***. This will transform the JSON dfiles into a single Pandas dataframe which is stored in the file `data.pkl.gz` which will be created by this notebook.

After running the Data Analysis notebook you need to run the ***Data Preprocessing*** notebook. This notebook will read the `data.pkl.gz` file and perform feature engineering on all the features in that file. This means all the non-numeric features are turned into numeric features and techniques like scaling or one-hot-encoding are applied to them, so that the data can be handled by machine learning algorithms.

This notebook will create the file `features_final.pkl.gz` which contains a Pandas dataframe with the engineered features ready for used with machine learning algorithms. Also one-hot-encoded label dataframes are created for the top, mid and fine labels. These labels are also stored as Pandas dataframes in the files `label_top_ohe.pkl.gz`, `label_mid_ohe.pkl.gz` and `label_fine_ohe.pkl.gz`.

After running those notebooks you can run the training notebooks. There are two different kinds of training notebooks. The notebooks ***Model Training Top/Mod/Fine*** train three different classifiers on the dataset: RandomForestClassifier, AdaBoostClassifier and GradientBoostingClassifier. The notebooks ***Neural Network Training Top/Mid/Fine*** train a neural network on the dataset. There is a notebook for each of the three labels (top/mid/fine) which are identical besides the label they use for training.

## Results

For the ***top*** label an accuracy of 70% is reached. For the ***mid** label the models reach an accuracy of 40% and for the ***fine*** label the models reach an accuracy of 30%.