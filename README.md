**CAMPUS SERVICE QUEUE PRIORITIZATION**

**OVERVIEW**

This project develops a decision-support system for organizing a campus service queue. It recommends the order in which students should be served using arrival time, service information, urgency, student type, document completeness, special assistance needs, and estimated service duration.

The system recommends the order in which students should be served. It considers the following information:
- Arrival time
- Service type
- Urgency
- Student type
- Document completeness
- Special assistance needs
- Estimated service duration

The project uses a priority-scoring method and compares its results with a First-In, First-Out (FIFO) queue.


**PROJECT OBJECTIVES**

- Rank student service requests clearly and fairly.
- Compare priority scoring with FIFO ordering.
- Validate the dataset.
- Handle incomplete records.
- Implement the process using KNIME and Python in Google Colab.
- Provide explainable queue recommendations.


**ALGORITHMS USED**

_1. PRIORITY SCORING_
Each record receives points based on urgency and service-related factors. Records are sorted from the highest score to the lowest score. Arrival time is used as the tie-breaker when two records have the same score.

_2. FIRST-IN, FIRST-OUT (FIFO)_
Records are arranged according to arrival time. The student who arrived first is placed first in the queue.


**PRIORITY-SCORING RULES**

_Urgency:_
- High urgency: 40 points
- Medium urgency: 25 points
- Low urgency: 10 points

_Student type:_
- Graduating student: 25 points
- Non-graduating student: 10 points

_Other factors:_
- Special assistance is needed: Add 20 points
- Documents are incomplete: Subtract 10 points
- Estimated duration is 15 minutes or less: Add 5 points

These scoring weights are _scenario-based assumptions_ created for this project. They are not produced by a trained machine-learning model.


**DATASET**

The dataset contains student service priority records.

The fields in the dataset are:
- record_id - Unique record identifier
- arrival_time - Time when the student joined the queue
- service_type - Type of campus service requested
- urgency - Level of urgency
- estimated_duration - Expected service duration in minutes
- student_type - Graduating or Non-Graduating
- document_complete - Indicates whether the documents are complete
- special_assistance - Indicates whether special assistance is needed


**DATASET FILES**

The complete dataset is:
_student_service_priority.csv_
- This dataset is used for the official results because it does not contain missing values.

The incomplete dataset is:
_student_service_priority_copy.csv_
- This dataset is used only for testing how the program handles missing values.


**MISSING-VALUE HANDLING**

The program handles missing values using the following rules:
- Missing urgency is replaced with Low.
- Missing service type is replaced with General Inquiry.
- Missing student type is replaced with Non-Graduating.
- Missing estimated duration is replaced with the median duration.
- Missing document status is replaced with No.
- Missing special assistance status is replaced with No.
- Missing arrival time is kept as missing and placed after records with known arrival times.

The incomplete dataset is only used for testing. It does not replace the complete dataset used for the main results.


**TOOLS AND TECHNOLOGIES**

- Python
- pandas
- NumPy
- Matplotlib
- Google Colab
- KNIME
- Streamlit


**KNIME WORKFLOW**

The KNIME workflow follows this process:

CSV Reader -> Missing Value -> Rule Engine -> Math Formula -> Sorter -> Top k -> Column Filter

The workflow reads the dataset, validates the data, handles missing values, calculates the priority score, sorts the records, and produces the recommended service order.


**HOW TO RUN THE PYTHON IMPLEMENTATION**

1. Open the Python notebook in Google Colab.
2. Upload student_service_priority.csv.
3. Upload student_service_priority_copy.csv.
4. Run the notebook cells in order.
5. Review the priority-scoring results.
6. Review the FIFO results.
7. Review the comparison table and chart.
8. Test missing-value handling.
9. Download the generated result files if needed.


**EXPECTED OUTPUTS**

The project produces the following outputs:
- Recommended priority-scored service order
- FIFO service order
- Comparison between priority scoring and FIFO
- Missing-value test results
- Boundary test results
- Comparison table or chart


**REPOSITORY CONTENTS**

The repository contains the following files:
- Documentation_Questions-and-Interpretations.pdf
- GROUP8_Data_Dictionary.pdf
- Priorityscoringdemo.mp4
- student_service_priority.csv
- student_service_priority_copy.csv
- StudentServicePriority.knwf
- CampusServiceQueuePrioritization.ipynb
- StreamlitCampusServiceQueuePrioritization.ipynb
- README.md


**LIMITATIONS**

- The scoring weights are manually selected project assumptions.
- The results depend on the quality of the input data.
- The system does not replace staff judgment.
- Additional factors may be needed before using the system in an actual campus office.
- The priority score is designed for transparency.

===============================================================================

**CONTRIBUTORS**

**GROUP 8**

<Añonuevo, Kassandra Margarette F.> 

_20231000026_

<Cuesta, Gabriel A.>

_20231000483_

<Hernaez, Angelee Louise R.>  

_20231000306_


BSCSSE - AN43
