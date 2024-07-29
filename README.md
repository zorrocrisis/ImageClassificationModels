## **Image Classification Model**
This project, originally an evaluation component for the Deep Learning course (2022/2023), talking place in Instituto Superior Técnico, University of Lisbon, aimed to **implement a linear classifier for a simple image classification problem**. More specifically, this poject utilises the KuzushijiMNIST dataset (KMNIST dataset), which contains handwritten cursive images of 10 characters from the Hiragana writing system (used for Japanese). Examples of images in this dataset are shown below.

<p align="center">
  <img src="https://github.com/user-attachments/assets/598e0554-0dff-4928-82bc-ea1ffdb41e92"/>
</p>

The following document indicates how to access and utilise the source code. It also contains a brief analysis of the implementation and results.

## **Quick Start**

In order to complete this exercise, you will need to download the Kuzushiji-MNIST dataset.
You can do this by running the following command in the homework directory:
python download_kuzushiji_mnist.py.

This project's source files can be downloaded from this repository. They are divided into the following main files:
- ***reviews.py*** - contains the best final classification model, training it on the training set (*train.txt*) to classify the test set (*test_just_reviews.txt*) and producing a list of labels/classifications (*results.txt*).
- ***train_multiple_models.py*** - trains and tests the implemented machine learning classification models.
- ***fine_tuning.py*** - fine-tunes the machine learning classification models.
- ***bert.py*** and ***tcn_models.py*** - contains the deep learning classification models.

To run this poject, follow these steps:
1. Install the necessary dependencies:
     - pip install pandas
     - pip install nltk
     - pip install scikit-learn
  
2. Simply run whatever file you would like utilising a terminal. As an example:
     - python reviews.py
  
Feel free to change the test and training sets, as well as any other parameters you see fit.

## **Perceptron**
Firstly, a **Perceptron** class was implemented (*python hw1-q1.py perceptron*) and subsequently **trained for 20 epochs** on the training set (KMNIST dataset). The verified resulting validation and test accuracies were the following:

<p align="center">
  <img src="https://github.com/user-attachments/assets/6460c8d3-3d0c-4a1e-964b-a83856f8cb9d"/>
</p>

<p align="center">
  <i>Graph 1 - Validation and test accuracies of multi-class Perceptron</i>
</p>

## **Logistic Regression**
The same exercise was applied to a **logistic regression** class (*python hw1-q1.py logistic_regression*), without regularisation and utilising **stochastic gradient descent as its training algorithm** (this algorithm was written by hand - no libraries or auxiliary modules were employed). A learning rate of η = 0.001 was defined. The verified resulting validation and test accuracies were the following:

<p align="center">
  <img src="https://github.com/user-attachments/assets/a496fcc1-88cf-4551-869c-296c899581f6"/>
</p>

<p align="center">
  <i>Graph 2 - Validation and test accuracies of multi-class Logistic Regression</i>
</p>

Comparing the accuracies from Graph 1 and 2, it was verified that **the overall accuracy of the logistic regression was better, also producing more consistent results than the multi-class Perceptron**.

## **Multi-layer Perceptron**
Seeking to further improve the overall performance and expressiveness, a **multi-layer perceptron** (or a feed-forward neural network) was additionally developed. The intermediate (or hidden) layers continuously alter the input and propagate this information forward, ensuring the underlying data results in better representations. In essence, the increase in expressiveness is translated into a more complex, non-linear classifier.

More specifically, a **single hidden layer with 200 units and a relu activation function** was implemented. The **gradient backpropagation algorithm with a learning rate of 0.001** was developed (manually, without employing any libraries or auxiliary modules) to train the model, alongside a **multinomial logistic loss (also called cross-entropy) in the output layer**. The **biases were intialised with zero vectors**, whereas the **values in the weight matrices were initialised with N (µ; σ2), where µ = 0.1 and σ2 = 0.12**.

This model can be run with *python hw1-q1.py mlp* and its results are graphically represented here:

<p align="center">
  <img src="https://github.com/user-attachments/assets/bb56b417-b0bf-4ffc-8bdf-d009720baf33"/>
</p>

<p align="center">
  <i>Graph 3 - Evolution of validation and test accuracies in a multi-layer Perceptron (learning rate of 0.001)</i>
</p>

In comparison with Graph 1 and Graph 2, the values above demonstrate a clear **overall improvement regarding the model’s accuracy**.

Starting from around a 75% accuracy, **the multi-layer Perceptron immediately begins to learn with a considerable rate of accuracy per epoch** (although this rate decreases over time, the improvement is constant), **achieving a final accuracy of around 94% and 84% in the validation and test stages, respectively**. 

These outcomes are quite remarkable, especially taking into account the previously obtained results for the image classification models. Though the single-layer Perceptron starts its training with the same accuracy, it does not manage to learn at a consistent and noteworthy rate. The logistic regression, on the other hand, does showcase a continuous enhancement over the 20 epochs, despite it being slow progress and only reaching a final accuracy of about 82% and 70% in the validation and test stages. That being said, the multi-layer Perceptron improved its initial accuracy by around 20%, demonstrating much better and quicker (in epochs) results than the former models.

However, **one must also consider the computational performance of this version of the Perceptron** - whereas the other models took a few minutes to train, **the multi-layer Perceptron does require a longer learning time** (around 20 minutes, in the same computer as the other tests), which might not be ideal for every application.


## **Logistic Regression with Autodiff Toolkit**
In the previous models, the gradient backpropagation algorithm had been written by hand. That being said, a new system **logistic regression classifier** was developed (*python hw1-q2.py logistic_regression*), this time **employing a deep learning framework with automatic differentiation**, namely Pytorch.

More specifically, this new model functioned with **stochastic gradient descent with a batch size of 1** and with a **training duration of 20 epochs**, producing the following results for distinct values of learning rates:

<p align="center">
  <i>Table 1 - Effect of learning rate parameter in logistic regression</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/400bccf5-5dc6-4f07-b6e4-3d0ff28711d0"/>
</p>

<p align="center">
  <img width= 500 src="https://github.com/user-attachments/assets/a3dd2bf8-dbb6-4547-89bc-b8faee78516b"/>
  <img width= 500 src="https://github.com/user-attachments/assets/5dd86603-f221-49f4-8670-c9bcd2883983"/>
  <img width= 500 src="https://github.com/user-attachments/assets/96650339-d148-419c-a351-4d80749a3db7"/>
</p>

<p align="center">
  <i>Graph Set 1 - The resulting validation accuracies with increasing learning rates: 0.001, 0.01 and 0.1</i>
</p>



<p align="center">
  <img width= 500 src="https://github.com/user-attachments/assets/538962c2-b947-4e28-98c1-23d8e09d2042"/>
  <img width= 500 src="[https://github.com/user-attachments/assets/356f27ea-140c-4864-961a-9809bbd3f256"/>
  <img width= 500 src="https://github.com/user-attachments/assets/b68f4dbb-03af-40bc-926a-9363a0eb9f16"/>
</p>

<p align="center">
  <i>Graph Set 2 - The resulting training loss with increasing learning rates: 0.001, 0.01 and 0.1</i>
</p>

From a brief analysis of the plotted data, we could report **the best configuration corresponded to the logistic regression classifier with a learning rate of 0.00**: not only does it have the best accuracies and final test loss, it seems to learn in a more consistent manner - the respective graphs have less sudden variations than the models with bigger learning rates. This can mean that bigger learning rates make the model “jump over” potential minima, thus explaining higher accuracies followed by considerable drops and an inconsistent evolution of these values.

## **Feed-Forward Neural Network with Single Hidden Layer (Autodiff Toolkit)**
Finally, multiple **feed-forward neural networks with single hidden layer** were implemented (*python hw1-q2.py ????*), once again employing Pytorch for **automatic differentiation**.

More specifically, **six single-layer neural networks** were developed and tested:
- **Default NN** - default hyperparameters from Table 1;
- **LR 0.001 NN** - learning rate of 0.001 and the remainder of the hyperparameters are default;
- **LR 0.1 NN** - learning rate of 0.1 and the remainder of the hyperparameters are default;
- **Hidden Size 200 NN** - hidden layer of 200 neurons and the remainder of the hyperparameters are default;
- **Dropout 0.5 NN** - dropout probability of 0.5 and the remainder of the hyperparameters are default;
- **Activation tanh NN** - activation function is tanh and the remainder of the hyperparameters are default;

The results from varying these hyperparameters are indicated below:

<p align="center">
  <i>Table 2 - Comparison of results from tuning of hyperparameters of single layer NNs</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/85c3a79c-6f8b-40f2-aeaa-a70bf592e828"/>
</p>

The NN with an **increased hidden layer size** (and the remainder of the hyperparameters with default values) had the best performance in terms of both validation and final test accuracy, thus representing the **best configuration**.

However, it was also the NN which **took the longest to compute the 20 training epochs**, which is quite understandable: an increase in the amount of neurons directly affects the network’s speed. Despite this, the time increase was not significant for such a small and simple network like this one - perhaps with multiple hidden layers the results would differ in this aspect…

<p align="center">
  <i>Table 3 - Best single layer feedforward neural network configuration (from the tests above)</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d17274ed-19bf-4c06-b043-8a6152e3d3c4"/>
</p>

## **Feed-Forward Neural Network with Multiple Hidden Layers (Autodiff Toolkit)**
Maintaining the hyperparameters for the best previous NN configuration, **the number of hidden layers was increased to 2 and 3** in order to verify how the accuracies evolved and what the new best configuration was. In other words, new tests were executed with **feed-forward neural networks with 2 and 3 hidden layers** (*python hw1-q2.py ????*), once again employing Pytorch for **automatic differentiation**.

The results can be analysed below:

<p align="center">
  <i>Table 4 - Comparison between best previous model, one additional hidden layer and two additional hidden layers</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/410ef20e-510c-4a6a-91e0-778bd7e39e98"/>
</p>

Unlike the results from the previous models, a not so direct conclusion is encountered: **although adding multiple hidden layers increases the overall accuracy of the NN, there is a point where it is superfluous and even less efficient, in terms of performance, to continue to increase the complexity of the network for such a simple task**.

For instance, in Table 4, the increase of the final test accuracy goes from 1.45% (between the single layer NN and the two layer NN) to actually decreasing 0.56% (between the two layer and three layer NN) - this might be due to a small numerical fluctuation but, either way, it is a sign of the **accuracy beginning to stabilise**.

The same goes for the validation accuracy: although there is an overall increase with the number of layers in the network, the increase percentage becomes almost insignificant, going from 0.61% to 0.05%.

Considering the first row of Table 4, which showcases a **constant increase in time taken to compute the 20 training epochs** (around 22 seconds for each layer added), we can state **the advantages of gaining a third layer are not worth the computational impact the program induces**. Therefore, the best configuration corresponds to the second column of the table, which translates in
the following set of hyperparameters:

<p align="center">
  <i>Table 5 - Best multi-layer feedforward neural network configuration (from the tests above)</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e29ba54b-e68d-4a24-b45c-a06ec3651dd7"/>
</p>


## **Authors and Acknowledgements**
This project was developed by **[Miguel Belbute (zorrocrisis)](https://github.com/zorrocrisis)** and [Guilherme Pereira](https://github.com/the-Kob).

The skeleton code was supplied by Francisco Melo (fmelo@inesc-id.pt).
