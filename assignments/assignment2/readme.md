# Assignment 2: CNNs and Transfer Learning
Due March 8, 2024 at 5 pm

Grace period until March 11 at 11:30 AM (start of class)

You may work individually or in pairs, but please let me know if you intend to work in pairs and make sure both names are on the assignment.

## Table of Contents <!-- omit in toc -->
- [Overview](#overview)
- [Dataset](#dataset)
- [Deliverables](#deliverables)
    - [Your report](#your-report)
    - [Your code](#your-code)
- [Marking Scheme](#marking-scheme)

## Overview
The purpose of this assignment is to apply your theoretical knowledge of neural networks (particularly convolutional neural networks) to a real application. You will **build and train a model** from "scratch" (using Keras, not really from scratch), and then apply **transfer learning** in order to compare both approaches.

## Dataset
This time, I'm choosing the dataset: [celeb_a](https://www.tensorflow.org/datasets/catalog/celeb_a), a large set of images of various celebrity faces. Each sample is labelled with 40 boolean attributes, such as "Bald", "Eyeglasses", "Heavy_Makeup", etc. You will choose one of these attributes to predict.

While the classes for each attribute are unbalanced, the dataset is large enough that we can get away with subsampling the data to obtain a balanced representation. Several functions have been provided in the [template notebook](a2_template.ipynb) to help with:
- Data preprocessing
- File management
- Subsampling with unbalanced and balanced classes
- Evaluating test data

## Deliverables
Your submission should take the form of either a Jupyter notebook including your code, results, and analysis, **or** a notebook with your code and an accompanying PDF report. You may submit the file(s) directly to D2L, or submit a link to a separately hosted (e.g. GitHub/GitLab) repository. A [template notebook](a1_template.ipynb) is provided as a starting point, along with some helper functions to load and preprocess the data.

### Your report
Your notebook or separate report should include:
1. A description of the dataset and the class you chose to predict, including:
    1. Biases and limitations of the dataset
    2. Class imbalance
    3. A summary of your impressions of the dataset
2. A description of the model you built from scratch, including:
    1. The architecture of the model
    2. The loss function and optimizer you used
    3. The metrics you used to evaluate the model
    4. A discussion of how you approached building, training, and refining the model
3. A description of the transfer learning model, including:
    1. A reference to the pre-trained model you used
    2. Why you chose that model
    3. A discussion of how you approached adding and training the new layers
4. A discussion/conclusion section describing:
    1. How the two models compared in terms of performance and ease of creation
    2. Challenges, advantages, and limitations of each approach
    3. Which you would choose if you were deploying this model in a production environment
    4. Any other thoughts or observations you have about the process
   
Each of the above sections should be no more than 1-2 paragraphs. Tabular or point-form summaries are encouraged where appropriate - consider using [Markdown syntax](https://www.markdownguide.org/basic-syntax/) to format your report, though you will not be graded on your formatting.

### Your code
You are not required to use Tensorflow and Keras, but if you use different packages, please include a `requirements.txt` file. You can generate this from a `venv` using the following command:

```bash
pip freeze > requirements.txt
```

> Note: if you run this command from your global Python environment it will include *all* packages installed on your system, not just the necessary ones for this project. Make sure to run it from within your virtual environment.

For that matter, you're not required to use Python at all, but please ensure to include all the information necessary to reproduce your results.

## Marking Scheme

Each of the four report sections is marked on a scale of 0 to 4, with an additional 4 points for overall clarity, quality, and creativity, for a total of 20 points. The marking scheme is as follows:

| Score | Description                                                            |
| ----- | ---------------------------------------------------------------------- |
| 4     | Excellent - thoughtful and creative without any errors or omissions    |
| 3     | Pretty good, but with minor errors or omissions                        |
| 2     | Mostly complete, but with major errors or omissions, lacking in detail |
| 1     | A minimal effort was made, incomplete or incorrect                     |
| 0     | No effort was made, or the submission is plagiarized                   |

Note that I am not marking you on the performance of your model, but rather your process and description of training and comparing models.