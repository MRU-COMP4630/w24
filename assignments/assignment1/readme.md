# Assignment 1: Data discovery and visualization
Due February 2, 2023 at 5 pm

You may work individually or in pairs, but please let me know if you intend to work in pairs and make sure both names are on the assignment.

## Table of Contents <!-- omit in toc -->
- [Overview](#overview)
- [Deliverables](#deliverables)
    - [Your report](#your-report)
    - [Your code](#your-code)
    - [How much detail is required?](#how-much-detail-is-required)
    - [Tips](#tips)
- [Finding Datasets](#finding-datasets)
- [Marking Scheme](#marking-scheme)

## Overview
Your task is to find a dataset and question that interests you, explore it, and apply any appropriate data transformations.

The focus of this assignment is understanding data quality and the role of preprocessing. You are not expected to train a model, but you should think about what kind of model might be appropriate for your question.

## Deliverables
Your submission should take the form of either a Jupyter notebook including your code, results, and analysis, **or** a notebook with your code and an accompanying PDF report. You may submit the file(s) directly to D2L, or submit a link to a separately hosted (e.g. GitHub/GitLab) repository. A template notebook is provided as a starting point.

### Your report
Your notebook or separate report should include:
1. An introduction describing the dataset, including:
    -  A **reference to its associated paper** (if possible), or a link to its source if not published as part of a paper (e.g. government data)
    -  A description of how the data was collected
    -  A description of the dataset's original purpose
    -  A brief discussion of the possible biases and limitations of the data
    -  If applicable, a description of alternative similar datasets
2. A concise statement of the problem or question you are trying to answer with the data
3. Exploratory data analysis, including:
    - A description of the data (e.g. number of rows, columns, data types, etc)
    - One or more visualizations of the numeric features (e.g. histograms, scatter plots, etc)
    - One or more visualization of the categorical features (e.g. bar charts)
    - A summary of your overall impression of the data quality, including any issues you identified (e.g. missing values, outliers, etc)
4. Your preprocessing pipeline (data transformations), along with a justification for each choice of data transformation.
5. A visualization or other summary of the transformed data, with commentary on the effectiveness of the transformations.
6. A conclusion and future work section, including:
   - Speculation on the model you might use to answer your question
   - What metrics you would use to measure its performance
   - Your overall impression of the dataset and any remaining limitations or biases

### Your code
You are not required to use scikit-learn and pandas, but if you use different packages, please include a `requirements.txt` file. You can generate this from a `venv` using the following command:

```bash
pip freeze > requirements.txt
```

> Note: if you run this command from your global Python environment it will include *all* packages installed on your system, not just the necessary ones for this project. Make sure to run it from within your virtual environment.

For that matter, you're not required to use Python at all, but please ensure to include all the information necessary to reproduce your results.

### How much detail is required?
Each of the numbered sections above should be no more than 2-3 paragraphs, and may be considerably shorter (such as the problem statement). The goal in science writing is typically to be as concise as possible while still conveying the necessary information. Your introduction and conclusion are likely to be the longest.

There is no limit on the number of visualizations, but you should only include those that provide useful information. You may find that you end up creating many more visualizations than are included in your final report, and that's okay! If you choose to visualize a subset of the features, make a note to explain why others were excluded.

### Tips
1. You do not need to write your report in order. I recommend you start with the data exploration (step 3) and then go back and write the introduction and question. In fact, it is common to write your introduction **last**.
2. You may get partway through data exploration and realize that the dataset is actually not suitable for your question. If you choose to abandon a dataset and find a new one, you can mention this in your introduction as part of your discussion of alternative datasets.
3. The end-to-end ML pipeline provides examples of *some* data transformation and visualization techniques, but these do not cover all scenarios. You may need to do some additional research to find the right technique for your dataset - in this case, make sure to **cite your sources**.
4. The dataset that you explore during this assignment may be used for your final project, but this is not a requirement. 

## Finding Datasets
Ultimately, machine learning is about answering questions using data. It's okay if you find a dataset first and then come up with a question, but brainstorming some question ideas can help narrow your dataset search. Feel free to use AI tools like ChatGPT to help you brainstorm, but make sure to cite any sources you use.

Finding a good dataset can be hard! To constrain your search, please adhere to the following:
- The dataset should be suitable for a regression or classification task
- It should be tabular format (not images, pure text, time series, etc)
- It should be less than ~100 MB, OR if larger, a subset of the data should be used (this is simply to keep the grading process manageable!)

Some good places to look for datasets:
- [Kaggle](https://www.kaggle.com/datasets) - a website for machine learning competitions with a huge number of datasets. You can filter by file size, topic and more
- [Papers with Code](https://paperswithcode.com/datasets) - pretty much what it says on the tin.
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/datasets) - a well-curated collection of datasets for learning purposes.
- [Google Dataset Search](https://datasetsearch.research.google.com/) - of course Google does datasets as well.
- [Wikipedia](https://en.wikipedia.org/wiki/List_of_datasets_for_machine-learning_research) - a giant list of datasets for machine learning research.
> Note: the UCI repository datasets have an "import in Python" button, feel free to use this instead of manually downloading the data.

There's also some sources closer to home, but they're more challenging to navigate:
- [City of Calgary Open data](https://data.calgary.ca/)
- [Alberta Open Data](https://open.alberta.ca/opendata)
- [Government of Canada Open Data](https://open.canada.ca/en/open-data)

Finally, if you have no idea where to start, here are a few you could try:
- [Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality) - a dataset of wine quality ratings and chemical properties
- [Jobs and salaries in Data Science](https://www.kaggle.com/datasets/hummaamqaasim/jobs-in-data/data) - a dataset of jobs, salaries, countries, experience level, etc in data science related roles
- [Average rent in Alberta](https://open.alberta.ca/opendata/average-rents-by-municipality) - average rent by year, type of rental unit, and municipality in Alberta
- [Rice type](https://archive.ics.uci.edu/dataset/545/rice+cammeo+and+osmancik) - a dataset of rice measurements taken from images of rice grains from two different varieties

If you're unsure whether a dataset is suitable, feel free to ask.

## Marking Scheme

Each of the numbered sections above is marked on a scale of 0 to 4 for a total of 24 points. An additional 4 points are allocated for overall clarity, quality, and creativity, for a total of 28 points. The marking scheme is as follows:

| Score | Description                                                            |
| ----- | ---------------------------------------------------------------------- |
| 4     | Excellent - thoughtful and creative without any errors or omissions    |
| 3     | Pretty good, but with minor errors or omissions                        |
| 2     | Mostly complete, but with major errors or omissions, lacking in detail |
| 1     | A minimal effort was made, incomplete or incorrect                     |
| 0     | No effort was made, or the submission is plagiarized                   |
