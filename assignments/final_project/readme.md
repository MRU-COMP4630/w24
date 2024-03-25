# Final Project: Doing something with some data
Presentations: Tuesday, April 16, 2024

Report Due: Friday, April 19, 2024 at 5 pm
> This is the last day of the exam period, so there isn't the usual deadline flexibility this time, sorry!

You may work individually or in pairs, but please let me know if you intend to work in pairs and make sure both names are on the assignment.

## Table of Contents <!-- omit in toc -->
- [Overview](#overview)
- [Presentation: 15% of final grade](#presentation-15-of-final-grade)
    - [Marking Scheme](#marking-scheme)
- [Report: 20% of final grade](#report-20-of-final-grade)
    - [Abstract](#abstract)
    - [Introduction](#introduction)
    - [Dataset and Preprocessing](#dataset-and-preprocessing)
    - [Model Architecture and Training](#model-architecture-and-training)
    - [Discussion and Conclusion](#discussion-and-conclusion)
    - [Your code](#your-code)
    - [Marking Scheme](#marking-scheme-1)
- [4-Point Scale](#4-point-scale)

## Overview
The goal of this assignment is to showcase the skills you've learned in this course by applying them to a new dataset and task. You are free to choose anything you like - for example, [Kaggle competitions](https://www.kaggle.com/competitions) may provide some interesting ideas. You can also use the dataset that you explored back in Assignment 1.

1. Choose a task, such as classification, regression, time-series forecasting, etc.
2. Find an appropriate dataset for that task. The dataset should be definitely more complex than [Titanic](https://www.kaggle.com/competitions/titanic) dataset, but not so complex that you can't load the data into memory (though sampling a BigQuery or similar dataset is a good workaround).
3. Explore the data and preprocess as necessary to handle missing values, feature scaling, etc.
4. Implement a model to try to accomplish your task. Make sure to document your process and results! You should try at least a few different models and hyperparameters, and explain why you chose them.
5. Prepare a presentation to share your project with the class.
6. Write a formal report describing your project.

> Tip: Often when you are writing a report and describing your methodology, you realize there is an error in that methodology and end up having to go back and fix something. Don't leave the writeup to the very end - it's a good idea to write as you go along.

## Presentation: 15% of final grade
Based on the poll, it looks like Tuesday, April 16th is the most acceptable day for the presentations.

For your presentation, please aim for about **10 minutes**,  with an additional 5 for questions (with some wiggle room as long as it falls within an overall 15 minute window). Your audience is your classmates, who are familiar with the material of the course, but not your project specifically. You should aim to explain:

1. A description of the task and dataset
2. Why you chose these, and any others you considered
3. Your preprocessing pipeline
4. Your chosen model architecture and hyperparameters, along with a brief discussion of other things you tried
5. Your results and any lessons learned from the process
6. Where you would take this project if you had more time

I recommend no more than 1 slide per 1-2 minutes.

### Marking Scheme
Using the usual [4 point scale](4-point-scale), I will be assessing the following components:
- Preparation and organization
- Evidence of experimentation and learning
- Overall coherence and clarity
- Answering questions

For a total of 16 points.

## Report: 20% of final grade
This time, I'd like you to format according to the [NeurIPS 2015 style guide](https://neurips.cc/Conferences/2015/PaperInformation/StyleFiles). This was the last year that Word documents were accepted, so I decided to use this one instead of making you all use LaTeX (though of course, LaTeX is always an option if you prefer).

Instead of a maximum of 8 pages, I would like a **maximum of 4 pages** (a common "short paper" length for conferences). This includes figures, so make the most of your space! You can include additional figures in an appendix if you like, but the main content should be in the main body of the report.

The exact sections and titles are up to you, but the report should include the following:

### Abstract
This should be as short as possible (one paragraph) and should provide an "at a glance" summary of the task, dataset, and final results.

### Introduction
Describe both the task and dataset, along with relevant citations and a brief discussion of prior work. Don't go too crazy down the research rabbit hole, but do try to find at least 2-3 papers that are relevant to your task.

### Dataset and Preprocessing
Describe the dataset you used, including the number of samples, features, and classes (if applicable). Discuss any preprocessing steps you took, such as normalization, feature engineering, or handling missing values.

### Model Architecture and Training
Describe the model architecture you used and the training parameters. Describe any variations you tried but were not successful, and what contributed to the success of your final model.

### Discussion and Conclusion
Discuss your results, including any lessons learned from the process. What limitations did you encounter, and what further work would you do if you were to continue this project?

For each of the above sections, consider using figures and tables instead of dense paragraphs listing parameters or results. For example, a table of hyperparameters and results for each model you tried would be a good way to summarize your experimentation.

Model performance will not be directly assessed, as long as I see evidence that you made some efforts to experiment and improve your model.

### Your code
This time, please include your notebook or scripts as a **separate document**.

As usual, you are not required to use Tensorflow and Keras, but if you use different packages, please include a `requirements.txt` file. You can generate this from a `venv` using the following command:

```bash
pip freeze > requirements.txt
```

> Note: if you run this command from your global Python environment it will include *all* packages installed on your system, not just the necessary ones for this project. Make sure to run it from within your virtual environment.

For that matter, you're not required to use Python at all, but please ensure to include all the information necessary to reproduce your results.

### Marking Scheme
Each of the following will be marked on a 4-point scale:
- Abstract (yes, a succinct summary is important, often this is the only part that gets read!)
- Discussion of prior work, including citations and relevant references
- Appropriate use of visuals and tables
- Description of dataset and preprocessing steps
- Description of model architecture and training process
- Discussion of lessons learned and future work
- Overall clarity and coherence

Resulting in the somewhat weird but arbitrary total of 28 points.

## 4-Point Scale

| Score | Description                                                            |
| ----- | ---------------------------------------------------------------------- |
| 4     | Excellent - thoughtful and creative without any errors or omissions    |
| 3     | Pretty good, but with minor errors or omissions                        |
| 2     | Mostly complete, but with major errors or omissions, lacking in detail |
| 1     | A minimal effort was made, incomplete or incorrect                     |
| 0     | No effort was made, or the submission is plagiarized                   |

Note that I am not marking you on the performance of your model, but rather your process and description of training and evaluating models.