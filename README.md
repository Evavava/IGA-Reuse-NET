---

---

# IGA-Reuse-NET: A deep-learning-based isogeometric analysis-reuse approach with topology-consistent parameterization

![](data\imgs\ISSA+UNet3+.png)

## Introduction

This is a Python implementation of IGA-Reuse-NET.  IGA-Reuse-NET is a deep learning model that predicts the numerical solution of poisson equations on topology-consistent geometries. We have made 6 sets of datasets with different topologies and different equations. We propose total loss according to the characteristics of the datasets and our task. We train the ISSA+UNet3+ network with total loss on the self-made datasets.

## Using the Codes

**View the results of our Reproducible Run:**

- Check the right panel for results from a Reproducible Run.

**Run user's own data on Code Ocean:**

- 'Capsule' -> 'Duplicate' to duplicate the capsule to user's own dashboard.

**Download the capsule to user's local machine:**

- 'Capsule' -> 'Export...' to download a zip file.
- 'Capsule' -> 'Clone via Git...' to git clone.

## Codes Details

The /code directory contains all major codes of IGA-Reuse-NET. Here are brief descriptions:

#### *Run.py*

Run different files according to different modes. If mode is train, run Train.py. If mode is test, run Test.py. If mode is plot, run Plot.py. In addition, there are many other parameters that need to be set according to different modes and different datasets.

#### *run/Train.py*

Train ISSA+UNet3+ on self-made datasets with our total loss.

*Inputs:*

+ Training dataset: data + “/” + args.data_select +  “/” + args.equation_select+ “/” + args.mode
+ Validation dataset: data + “/” + args.data_select +  “/” + args.equation_select+ “/” + args.mode

*Ouputs:*

+ Trained model: results + “/” + models + “/” + args.data_select + args.equation_select + “.pth”
+ Training error and validation error log: results + “/” + preds + “/” + args.data_select + args.equation_select

#### *run/Test.py*

Test the trained model on self-made datasets with our four testing indicators.

*Inputs:*

+ Testing dataset: data + “/” + args.data_select +  “/” + args.equation_select+ “/” + args.mode

*Ouputs:*

+ The values of testing indicators: results + “/” + preds + “/” + args.data_select + args.equation_select + “Test.txt”

#### *run/Plot.py*

Draw the statistical curves of the predicted solution and the IGA solution. Only one prediction result is counted at a time, and the index of the model to be predicted needs to be entered.

*Inputs:*

+ Testing dataset: data + “/” + args.data_select +  “/” + args.equation_select+ “/” + args.mode

*Ouputs:*

+ The figure: results + “/” + preds + “/” + args.data_select + args.equation_select + “/” +  “plot” + arg.test_index + “.png”
+ The figure: results + “/” + preds + “/” + args.data_select + args.equation_select + “/” +  “pred” + arg.test_index + “.txt”

#### *Loss/myLossFunc.py*

Here we implement the total loss function that combines the coefficients loss and the loss of the numerical solution for training, and implement the relative error of the numerical solution for testing. In addition, in order to plot the statistical curves, we need to calculate the numerical solution as well as the IGA numerical solution, so a plot loss function is implemented.

#### *Loss/PDEError.py*

Here we  implement the posterior error of poisson equation for testing.  We choose different right-side functions according to args.pde_type.

#### Flow Chart

![](data\imgs\FlowChart.png)

## Reference



## Contact Information

**Dandan Wang:** wangdandan@alu.hdu.edu.cn;**Gang Xu:**xugangzju@gmai.com