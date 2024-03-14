# Assignment 3: Classification of Text Data
Due March 22, 2024 at 5 pm

Grace period until March 25 at 11:30 AM (start of class)

You may work individually or in pairs, but please let me know if you intend to work in pairs and make sure both names are on the assignment.

## Table of Contents <!-- omit in toc -->
- [Overview](#overview)
- [Dataset](#dataset)
- [Deliverables](#deliverables)
    - [Your report](#your-report)
    - [Your code](#your-code)
- [Marking Scheme](#marking-scheme)

## Overview
The purpose of this assignment is to further your hands-on experience in neural networks with a new type of data: text! 

## Dataset
The dataset for this assignment is the [Stack Overflow dataset](https://console.cloud.google.com/marketplace/product/stack-exchange/stack-overflow), an archive of all Stack Overflow questions, answers, and metadata since 2009, updated on a quarterly basis. This is a massive dataset that is impractical to load all at once; you will be using Google's [BigQuery API](https://cloud.google.com/bigquery/docs/reference/rest) to query the database and select a sample of the data.

In order to access BigQuery data, you must create a project at https://console.cloud.google.com/. You will also need to enable the BigQuery API through the cloud console, which should pop up as soon as you create a project.

The free tier of Google Cloud provides up to 1 TB per month of data access, which should be plenty for this assignment. However, if you need more, you can request a Google Cloud coupon. You will be asked to provide your school email address and name. An email will be sent to you to confirm these details before a coupon is sent to you.

## Deliverables
Your submission should take the form of either a Jupyter notebook including your code, results, and analysis, **or** a notebook with your code and an accompanying PDF report. You may submit the file(s) directly to D2L, or submit a link to a separately hosted (e.g. GitHub/GitLab) repository. A [template notebook](a3_template.ipynb) is provided as a starting point, along with some helper functions to load and preprocess the data. The template notebook also includes more details on how to access the BigQuery API.

### Your report
1. Dataset Description
    A description of the dataset, including:
    1. Biases and limitations of the dataset
    2. Class (im)balance
    3. A summary of your impressions of the dataset

2. Documentation of Experiments
    A description of the various things you tried, including:
    1. Changes to the vectorization/tokenization/other preprocessing
    2. Changes to the model architecture
    3. Changes to hyperparameters, loss functions, and optimizers
    4. A brief summary of things you learned in the process

    Some of this might be best presented in a table or list format.

3. Your Final Model
    A description of the final "best" model you built, including:
    1. The preprocessing pipeline
    2. The architecture and model hyperparameters
    3. A brief discussion/your best guess as to why this model outperformed the others

4. Discussion/Conclusion
    A discussion/conclusion section describing:
    1. Challenges, advantages, and limitations of the process or model
    2. Your key takeaways from the process
    3. What you would do if you had more time
    4. Any other thoughts or observations you have about NLP and classification
   
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

Note that I am not marking you on the performance of your model, but rather your process and description of training and evaluating models.