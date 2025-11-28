README --- Midterm Project : Multi-Track Data Report and Statistical Analysis

**Overview**

In this project, we designed and implemented a complete, modular, and
automated workflow for cleaning student datasets, computing performance
statistics, and generating visualizations. 

Throughout the process, we
worked carefully to ensure that the entire system could adapt to
heterogeneous Excel or CSV inputs, detect relevant columns even when
their names are inconsistent, generate reliable aggregated reports, and
produce clear visual outputs.

As a group, we made deliberate decisions to structure the code in a way
that reflects our understanding of data processing and our reasoning at
each step. We also organized the components so that the workflow remains
transparent, maintainable, and reusable. This project helped us refine
our approach to robust dataset handling, and we constructed tools that
we believe are both practical and pedagogically sound.

The suite includes:

-   A full data cleaning pipeline (StudentDataPipeline)
-   Automated track-level and cohort-level reports exported to Excel
-   Visualization modules for exploring academic performance, including:
    -   History score distribution per track
    -   Comparison between students receiving income support and those
        who do not
    -   Math performance comparison across tracks
-   Shared utility functions that we built to improve automation:
    -   find_column for flexible column detection
    -   get_metric_numeric_columns for automatic identification of
        academic metrics
    -   compute_pass_rate for consistent pass/fail normalization


**Instructions for Running the Scripts**

Phase 1:  Run the Cleaning Pipeline

We begin by cleaning, standardizing, and normalizing the raw dataset.
This step prepares the groundwork for all further analyses.

Command that we used: python pipeline.py

Phase 2 --- Generate Statistical Reports

Once the dataset is cleaned, we produce aggregated statistics that
summarize academic performance across tracks and cohorts.

Command that we used: python stats_report.py

Phase 3 --- Generate Visualizations

We can run the visualization scripts independently depending on the type
of analysis we want to explore.

History per track: python plot_history.py

Income comparison: python plot_income.py

Math average per track: python plot_math.py

**Description of Implemented Functionalities**

1.  Universal Column Finder\
    We designed the find_column function so that we could work with
    datasets containing inconsistent column names. It normalizes column
    labels and checks for keyword matches, enabling our scripts to adapt
    automatically.

2.  Automatic Metric Detection\
    We implemented get_metric_numeric_columns to detect academic
    performance metrics without requiring fixed naming conventions. We
    used keyword-based logic combined with numeric filtering to ensure
    that the selections remain meaningful.

3.  Full Cleaning Pipeline\
    In our StudentDataPipeline, we handled several essential tasks:

-   Standardizing column names to a consistent lowercase,
    underscore-free format
-   Cleaning and trimming textual values
-   Converting attendance values to percentages even when expressed
    inconsistently
-   Converting academic scores safely to numeric types
-   Imputing missing values using rolling means and rolling modes to
    retain dataset coherence over time
-   Normalizing categorical Yes/No fields for income or assistance data
-   Appending an overall summary row for clarity
-   Validating ranges and categories to detect remaining anomalies

Through these steps, we tried to make sure that the cleaned dataset
would be both coherent and ready for meaningful analysis.

4.  Statistical Reporting\
    We produced scripts that compute:

-   Student counts for each track and each cohort
-   Means for all automatically detected academic metrics
-   Pass rates built through categorical normalization
-   Correlations between key indicators such as attendance and project
    scores
-   Summary rows providing global aggregates

We export these results in a clear two-sheet Excel file, hoping to make
the data easy to interpret.

5.  Visualization Scripts\
    In each visualization script, we:

-   Automatically detect the necessary columns using our helper
    functions
-   Convert values to numeric formats safely
-   Filter the data before plotting
-   Generate PNG files that illustrate score distributions, comparisons,
    and track-level performance

**Assumptions and Limitations**

Assumptions: - Each row corresponds to a unique student. - The track
column represents a meaningful grouping such as class or section. -
Metric columns contain academic scores in numeric form. - Income or
support indicators can be normalized to Yes or No.

Limitations: - Fuzzy column detection may fail when column names are
extremely ambiguous. - Rolling-window imputation smooths data and may
reduce variability. - Plotting requires an environment capable of
rendering images. - Very inconsistent datasets may still require manual
inspection or override.

**Recommended Workflow**


Based on our experience building and using this suite, we recommend the
following order when running the project:

1.  Run pipeline.py to generate a cleaned dataset.
2.  Run stats_report.py to produce the aggregated summary statistics.
3.  Use any of the plot scripts to explore performance visually.

**How to Read the Project**

To understand the project as we designed it, we recommend reading it in
the following order:

1.  Begin with the cleaning pipeline to understand how raw inputs are
    transformed.
2.  Continue with the statistics script to observe how the cleaned data
    is summarized.
3.  Explore the visualization modules to see how insights are
    communicated graphically.
4.  Review the utility functions, which support flexibility and
    automation across the whole workflow.


**Conclusion**

We developed this project with the intention of producing a clear,
reliable, and adaptable framework for analyzing educational datasets.
Throughout the process, we reflected on how to make the system robust
and interpretable. The resulting codebase is designed to be both
practical for real use and pedagogically meaningful for understanding
data processing pipelines.
