# Assignment 1: Data discovery and simple modelling
Due February 2, 2023 at 5 pm

You may work individually or in pairs, but please let me know if you intend to work in pairs and make sure both names are on the assignment.

## Overview
Your task is to find a dataset that interests you, explore it using pandas and matplotlib, then build a simple model to answer a question about the data.

## Deliverables
Your submission should take the form of a Jupyter notebook including your code, results, and analysis. You may submit the files directly to D2L, or submit a link to a separately hosted (e.g. GitHub/GitLab) repository. A template notebook is provided as a starting point.

Your notebook should include:
- A general description of the dataset, including a **reference to its associated paper** (if possible). If you are using a dataset from a government repository or other source that does not have a paper, please include a link to the source.
- A description of the question you are trying to answer with your model.
- Exploratory data analysis, such as:
    - A description of the data (e.g. number of rows, columns, data types, etc)
    - A visualization of the numeric features (e.g. histograms, scatter plots, etc)
    - A visualization of the categorical features (e.g. bar charts)


## Datasets
Finding a good dataset can be hard! To constrain your search, please adhere to the following:
- The dataset should be suitable for a regression or classification task
- It should be tabular format (not images, pure text, time series, etc)
- It should be less than 20 MB, OR if larger, a subset of the data should be used (this is simply to keep the grading process manageable!)

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