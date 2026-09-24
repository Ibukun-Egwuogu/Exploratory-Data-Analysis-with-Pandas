# Exploratory-Data-Analysis-with-Pandas
A full replication of Student Resource 2 from Module 4 of the Vephla University Artificial Intelligence and Machine Learning programme, completed as Task 24
The resource introduces exploratory data analysis in Python by working through a single dataset of roller coasters from start to finish. Rather than treating EDA as a loose collection of pandas commands, it presents a repeatable five step process: understand the data, prepare it, examine each feature on its own, study how features relate to one another, and finally use the cleaned data to answer a defined question. This repository contains my replication of that process, along with detailed documentation of every topic covered.

Dataset

The analysis uses coaster_db.csv, a dataset of 1,087 roller coasters described across 56 columns. The raw file mixes clean numeric fields with text fields that contain embedded units, duplicate records, and columns that are largely empty, which makes it a realistic starting point for practising data preparation. After preparation the working dataset holds 990 unique rides across 13 columns.

Topics and Techniques

Data understanding shape, head, columns, dtypes and describe to establish the size, structure, data types and summary statistics of the dataset before changing anything.

Data preparation Column subsetting and the drop method for removing irrelevant fields, pd.to_datetime and pd.to_numeric for correcting data types, rename for standardising column names, isna().sum() for locating missing values, and duplicated with a column subset for identifying and removing duplicate records.

Feature understanding (univariate analysis) value_counts for categorical frequencies, bar charts for discrete categories, histograms for continuous distributions, and kernel density estimate plots for a smoothed view of the same distribution.

Feature relationships (bivariate and multivariate analysis) Pandas and Seaborn scatterplots, adding a third variable through the hue argument, pairplot for scanning many relationships at once, a correlation matrix with corr, and a Seaborn heatmap for reading that matrix visually.

Answering a question query for filtering, groupby with agg for grouped comparisons, and a horizontal bar chart to present the result. The final analysis asks which locations have the fastest coasters on average, limited to locations with at least ten rides.

Repository Structure
.
├── Exploratory_Data_Analysis_Ibukun_Egwuogu.ipynb   Full replication notebook, commented throughout
├── EDA_Documentation.docx                           Detailed written documentation of every topic
├── coaster_db.csv                                   Dataset used in the analysis
└── README.md                                        This file

The notebook is the place to start. It follows the same order as the resource, with a markdown heading opening each of the five steps and comments explaining what each block of code does and what output to expect. Every cell has been run, so the outputs and charts are visible without needing to execute anything.

The documentation is the companion reference. It explains what each concept is, why the technique is used, the decisions taken at each stage, how this resource builds on earlier modules, and the takeaways from working through it.

Running the Notebook
bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Exploratory_Data_Analysis_Ibukun_Egwuogu.ipynb

Keep coaster_db.csv in the same directory as the notebook, since the file is read with a relative path.

Key Takeaways

Defining a duplicate is an analytical decision rather than a mechanical one. Checking for rows identical across all columns found nothing at all, while checking on coaster name alone flagged far too much. Inspecting an example record showed that name, location and opening date together gave a defensible definition, which identified 97 duplicates.

Summary statistics reveal more than they first appear to. The count row returned by describe exposes missing values immediately, before any dedicated null check is run. In this dataset the height column held only 171 valid entries out of 1,087.

Visualisation and statistics are stronger together than apart. The scatterplot suggested a relationship between speed and height, and the correlation matrix confirmed its strength at 0.73. Either result on its own would have been weaker evidence.

Small analytical safeguards carry significant weight. Requiring at least ten rides per location in the final comparison prevents a park with one very fast coaster from topping a ranking built on a single record, which is exactly the kind of distortion that makes an average misleading.

Author

Ibukun Egwuogu, Vephla University, School of Artificial Intelligence and Machine Learning, Cohort 50B
