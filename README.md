# FPGA-Congetion
## Congestion Prediction in FPGA Using Regression Based Learning Methods
## All about the project
Design closure in general VLSI physical design flows
and FPGA physical design flows is an important and timeconsuming
problem. Routing itself can consume as much as 70total
design time. Accurate congestion estimation during the early
stages of the design flow can help alleviate last-minute routingrelated
surprises. This work has described a methodology for
a post-placement, machine learning-based routing congestion
prediction model for FPGAs. Routing congestion is modeled
as a regression problem. We have described the methods for
generating training data, feature extractions, training, regression
models, validation, and deployment approaches. We have tested
our prediction model by using ISPD 2016 FPGA benchmarks.
Our prediction method reports a very accurate localized congestion
value in each channel around a configurable logic block
(CLB). The localized congestion is predicted in both vertical and
horizontal directions. We demonstrate the effectiveness of our
model on completely unseen designs that are not initially part
of the training data set. The generated results show significant
improvement in terms of accuracy measured as mean absolute
error.

# Introduction
Machine Learning (ML) has found its application in various
Electronic Design Automation (EDA) problems, and has been
used to make early prediction on various quality related parameters.
In EDA, ML finds its applications in yield prediction
, timing and power optimization, auto-tuning of CAD tool
parameters , and routing congestion estimation . Learning
from prior designs and predicting performance and closure
issues has immense value in the EDA community. A recent
announcement from Xilinx about its ML-suite strongly affirms
the idea that ML will play an important role in Electronic
Design Automation. In FPGA physical design flow, routing
is the most time-consuming task. It is prevalent for a router
to either fail or take a long time to complete the routing,
especially for very high logic utilization designs. Locally
congested regions can result in failed routing or sub-optimal
designs with problems in timing closure. Usually, a designer
must replace the design in order to obtain better closure after
a failed routing attempt. Routing Congestion is measured as
the ratio of the number of used routing tracks to the number of
available routing tracks. Routing congestion can be measured
accurately only after the detailed routing. Traditionally, in
ASIC design flows, congestion is estimated after the global
routing using statistical models. Since Global Routing-based
statistical and probabilistic prediction models do not work well
on smaller technology nodes and FPGAs, alternate approaches
are needed to predict the routing congestion before the router
attempts a complete routing task.

if you have good knowledge in machine learning field and you also have knowledge about FPGA ,not deep knowlwdge but atleast 
you know the basisc of FPGA chip .
for doing this project you can follow this steps:
# DAY-1 ( Basics of machine learning )
Machine learning is a subset of artificial intelligence that focuses on enabling computers to
learn from data and make predictions or decisions without being explicitly programmed.
One fundamental aspect of machine learning is regression, a technique used for predicting
continuous numerical values based on input data. Let's delve into the basics of machine
learning theory, highlighting regression and prediction.
1. Supervised Learning:
Supervised learning is a common approach in machine learning where the algorithm learns
from labeled training data. The data consists of input-output pairs, where the inputs are the
features, and the outputs are the corresponding target values. Regression falls under the
category of supervised learning.
2. Regression:
Regression is a type of supervised learning that deals with predicting continuous numerical
values. It's used when the output variable is quantitative, meaning it has a range of possible
values. The goal of regression is to find a mathematical relationship between the input
features and the output variable so that the algorithm can make accurate predictions on
new, unseen data.
3. Features and Target Variable:
In regression, the input data consists of features, also called independent variables or
predictors. These features influence the output variable, which is also known as the target
variable or dependent variable. The goal is to find the underlying pattern or relationship that
links the features to the target variable

4. Types of Regression:
There are various types of regression techniques, including:
Linear Regression: This is the simplest form of regression, where the goal is to find a linear
relationship between the features and the target variable.
Multiple Regression: An extension of linear regression where there are multiple features
influencing the target variable.
Polynomial Regression: It involves fitting a polynomial equation to the data to capture
more complex relationships.
Ridge and Lasso Regression: These are techniques that introduce regularization to
prevent overfitting and improve generalization.
Support Vector Regression (SVR): A regression technique that uses the concept of
support vector machines to find a hyperplane that best fits the data.
5. Training and Prediction:
The process of building a regression model involves two main steps:
Training: During training, the algorithm learns the relationship between the features and
the target variable from the labeled training data. It adjusts its internal parameters to
minimize the difference between predicted values and actual values.
Prediction: After the model is trained, it can be used to predict the target variable for new,
unseen data. The model applies the learned relationship to the input features to generate
predictions.

## Random Forest Regression: A Brief Overview
Random Forest Regression is a powerful machine learning technique that combines the
concepts of ensemble learning and decision trees to perform regression tasks. It is an
extension of the Random Forest algorithm, which is widely used for classification tasks.
Random Forest Regression excels at handling complex relationships in data, reducing
overfitting, and providing accurate predictions. Here's a brief overview of how Random
Forest Regression works:

### Ensemble Learning:
Ensemble learning involves combining the predictions of multiple individual models to
create a more robust and accurate final prediction. Random Forest Regression takes
advantage of ensemble learning by combining multiple decision trees to make better
predictions.
### Decision Trees:
A decision tree is a flowchart-like structure where each internal node represents a decision
or a test on a feature, each branch represents an outcome of the decision, and each leaf
node represents the predicted output. Decision trees split the data based on features and
create a hierarchy of decisions to predict the target variable.
### Random Forest Regression Process:
Data Selection: The training data is randomly sampled with replacement to create multiple
subsets, known as bootstrap samples.

Building Decision Trees: For each bootstrap sample, a decision tree is constructed using a
random subset of features. This randomness helps in reducing the correlation among the
individual trees and prevents overfitting.

diction Aggregation: Once all decision trees are built, they make predictions for the
target variable based on the input features. In regression tasks, the predictions from all
trees are aggregated to produce the final prediction. This aggregation can be done by
averaging the predictions (for continuous target variables) or using other techniques
depending on the problem.


## Advantages of Random Forest Regression:
Reduced Overfitting: By aggregating predictions from multiple trees and using random
subsets of features, Random Forest Regression mitigates overfitting and generalizes well
to new data.

Handles Non-Linearity: Random Forest Regression can capture complex nonlinear
relationships between features and the target variable, which is valuable in real-world
scenarios where data may not follow simple linear patterns.

Feature Importance: The algorithm provides a measure of feature importance, allowing you
to identify which features contribute the most to the predictions. This can help in feature
selection and understanding the underlying data dynamics.

Robustness: Random Forest Regression is robust to outliers and noisy data, as it considers
the consensus of multiple trees rather than relying heavily on any single decision.
Easy to Use: It requires minimal hyperparameter tuning compared to other complex
algorithms and can often provide good results with default settings.

# DAY-2 ( learning about FPGA )
## Basics of FPGA (Field-Programmable Gate Array) in Brief
FPGA, which stands for Field-Programmable Gate Array, is a type of integrated circuit (IC)
that offers immense flexibility and configurability for digital logic design and
implementation. Unlike traditional application-specific integrated circuits (ASICs) that are
fixed in functionality, FPGAs can be programmed and reconfigured to perform a wide variety
of tasks. Here's a brief overview of the basics of FPGA:

### 1. Digital Logic and Gates:
At the heart of an FPGA are programmable logic blocks that consist of configurable logic
gates, such as AND, OR, NOT, XOR, etc. These gates can be interconnected and configured
to create complex digital circuits, ranging from simple combinational logic to more intricate
sequential logic.
### 2. Configurability:
FPGAs offer a high degree of configurability, allowing designers to create custom digital
circuits by programming the interconnections between logic blocks. This programming is
typically done using hardware description languages (HDLs) like VHDL or Verilog.
### 3. Look-Up Tables (LUTs):
FPGAs commonly use look-up tables (LUTs) as a fundamental building block. A LUT stores
precomputed outputs for all possible input combinations, allowing it to function as a flexible
logic element. This feature enables FPGAs to implement a wide range of functions
efficiently.

### 4. Routing Resources:
The programmable logic elements in FPGAs are interconnected through a network of
configurable routing resources. These resources enable signals to flow between logic
blocks, allowing for the creation of complex interconnections.
### 5. Clock Management:
FPGAs often include dedicated resources for managing clock signals. These resources
ensure that the design's timing requirements are met, and they can provide functions such
as clock division, multiplication, and distribution.
### 6. I/O Interfaces:
FPGAs provide input/output interfaces to communicate with the external world. These
interfaces can be configured to support various communication protocols, such as GPIO,
UART, SPI, I2C, Ethernet, and more.
### 7. Reconfiguration:
One of the unique features of FPGAs is their ability to be reconfigured on-the-fly. This
means that the same FPGA hardware can be repurposed for different tasks simply by
loading a new configuration bitstream onto the device.
### 8. Applications:
FPGAs find applications in a wide range of fields, including:
Digital signal processing (DSP)
Embedded systems
Hardware acceleration for machine learning and cryptography
Real-time image and video processing
Network packet processing and routing
Aerospace and defense systems
Prototyping and testing of ASIC designs
## 9. Advantages:
Rapid prototyping and development of custom digital circuits.
Can accelerate specific algorithms and tasks for improved performance.
Lower development cost compared to designing custom ASICs.
Flexibility for implementing custom hardware solutions without manufacturing new chips.


# DAY-3 ( handson with python coding language )

# DAY-4 ( raed the attached refrence papers )

# DAY-5 ( write code for regression and play with the data at last check your result 




 


