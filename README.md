# Horse Medical Condition Prediction

## Overview

This repository contains a dataset and code for predicting the outcome of horses' medical conditions based on various attributes. The goal is to determine whether a horse will survive or not based on past medical information.

## Dataset

The dataset consists of the following attributes:

1. **surgery:** Indicates whether the horse had surgery (1 = Yes, it had surgery; 2 = It was treated without surgery).
2. **Age:** Indicates whether the horse is an adult (1 = Adult horse) or young (< 6 months) (2 = Young horse).
3. **Hospital Number:** A numeric ID representing the case number assigned to the horse (may not be unique if the horse is treated more than once).
4. **Rectal Temperature:** The horse's rectal temperature in degrees Celsius. Elevated temperature may be a sign of infection.
5. **Pulse:** The heart rate in beats per minute. Reflects the horse's heart condition.
6. **Respiratory Rate:** The horse's respiratory rate, which is normally between 8 to 10.
7. **Temperature of Extremities:** A subjective indication of peripheral circulation (1 = Normal, 2 = Warm, 3 = Cool, 4 = Cold).
8. **Peripheral Pulse:** A subjective measurement of peripheral pulse (1 = Normal, 2 = Increased, 3 = Reduced, 4 = Absent).
9. **Mucous Membranes:** A subjective measurement of mucous membrane color (1 = Normal pink, 2 = Bright pink, 3 = Pale pink, 4 = Pale cyanotic, 5 = Bright red / injected, 6 = Dark cyanotic).
10. **Capillary Refill Time:** A clinical judgment of capillary refill time (1 = < 3 seconds, 2 = >= 3 seconds).
11. **Pain:** A subjective judgment of the horse's pain level (1 = Alert, no pain, 2 = Depressed, 3 = Intermittent mild pain, 4 = Intermittent severe pain, 5 = Continuous severe pain).
12. **Peristalsis:** An indication of the activity in the horse's gut (1 = Hypermotile, 2 = Normal, 3 = Hypomotile, 4 = Absent).
13. **Abdominal Distension:** An important parameter indicating the level of abdominal distension (1 = None, 2 = Slight, 3 = Moderate, 4 = Severe).
14. **Nasogastric Tube:** Presence and amount of gas coming out of the nasogastric tube (1 = None, 2 = Slight, 3 = Significant).
15. **Nasogastric Reflux:** The amount of nasogastric reflux (1 = None, 2 = > 1 liter, 3 = < 1 liter).
16. **Nasogastric Reflux PH:** The pH level of nasogastric reflux.
17. **Rectal Examination - Feces:** Indicates the presence and condition of feces (1 = Normal, 2 = Increased, 3 = Decreased, 4 = Absent).
18. **Abdomen:** Describes the condition of the abdomen (1 = Normal, 2 = Other, 3 = Firm feces in the large intestine, 4 = Distended small intestine, 5 = Distended large intestine).
19. **Packed Cell Volume:** The number of red cells by volume in the blood. Normal range is 30 to 50.
20. **Total Protein:** The total protein level in the blood.
21. **Abdominocentesis Appearance:** Describes the appearance of fluid obtained from the abdominal cavity (1 = Clear, 2 = Cloudy, 3 = Serosanguinous).
22. **Abdominocentesis Total Protein:** The level of protein in the abdominal fluid.
23. **Outcome:** Indicates what eventually happened to the horse (1 = Lived, 2 = Died, 3 = Was euthanized).
24. **Surgical Lesion:** Indicates retrospectively whether the problem (lesion) was surgical (1 = Yes, 2 = No).
25-27. **Type of Lesion:** Describes the site, type, and subtype of lesion.
28. **cp_data:** Indicates whether pathology data is present for this case (1 = Yes, 2 = No).

## Repository Structure

- **data** The dataset containing the original as well as syntheically generated horse medical condition information.
- **horse_medical_condition.ipynb:** Jupyter Notebook containing the code for data exploration, preprocessing, and model training.
- **README.md:** This README file providing an overview of the dataset and repository.

## Model Accuracy before hypertunning

| Model                        | Accuracy | Balanced Accuracy | ROC AUC | F1 Score | Time Taken (s) |
|------------------------------|----------|--------------------|---------|----------|-----------------|
| RandomForestClassifier       | 0.73     | 0.72               | None    | 0.73     | 0.60            |
| BaggingClassifier            | 0.68     | 0.68               | None    | 0.68     | 0.23            |
| NearestCentroid              | 0.68     | 0.68               | None    | 0.69     | 0.02            |
| LinearDiscriminantAnalysis   | 0.70     | 0.67               | None    | 0.70     | 0.03            |
| GaussianNB                   | 0.68     | 0.67               | None    | 0.69     | 0.03            |
| BernoulliNB                  | 0.68     | 0.67               | None    | 0.68     | 0.02            |
| LinearSVC                    | 0.70     | 0.67               | None    | 0.70     | 0.45            |
| KNeighborsClassifier         | 0.69     | 0.67               | None    | 0.69     | 0.04            |
| ExtraTreesClassifier         | 0.70     | 0.67               | None    | 0.69     | 0.49            |
| AdaBoostClassifier           | 0.68     | 0.66               | None    | 0.68     | 0.25            |
| RidgeClassifier              | 0.70     | 0.66               | None    | 0.70     | 0.03            |
| CalibratedClassifierCV       | 0.70     | 0.66               | None    | 0.69     | 0.19            |
| XGBClassifier                | 0.68     | 0.66               | None    | 0.68     | 0.55            |
| QuadraticDiscriminantAnalysis| 0.67     | 0.66               | None    | 0.67     | 0.05            |
| LogisticRegression           | 0.69     | 0.66               | None    | 0.68     | 0.06            |
| RidgeClassifierCV            | 0.69     | 0.65               | None    | 0.69     | 0.03            |
| LGBMClassifier               | 0.68     | 0.65               | None    | 0.68     | 0.48            |
| SVC                          | 0.69     | 0.65               | None    | 0.68     | 0.13            |
| SGDClassifier                | 0.67     | 0.65               | None    | 0.67     | 0.07            |
| NuSVC                        | 0.68     | 0.64               | None    | 0.68     | 0.15            |
| DecisionTreeClassifier       | 0.65     | 0.64               | None    | 0.65     | 0.05            |
| LabelPropagation             | 0.64     | 0.62               | None    | 0.64     | 0.14            |
| LabelSpreading               | 0.64     | 0.62               | None    | 0.64     | 0.13            |
| PassiveAggressiveClassifier  | 0.64     | 0.62               | None    | 0.64     | 0.03            |
| Perceptron                   | 0.63     | 0.60               | None    | 0.63     | 0.02            |
| ExtraTreeClassifier          | 0.58     | 0.55               | None    | 0.58     | 0.03            |
| DummyClassifier              | 0.47     | 0.33               | None    | 0.30     | 0.02            |

## Model accuracy after hypertunning

     * CatboostClassifier - 73%
     * LgbmClassifier - 73%
     * XBGClassifier - 75%
     * EnsembleLearning
          1. Voting - 73%
          2. Stacking - 72%

## Final Result:

Ranked in Top 20% in the competition 


## Note

This dataset is for educational and research purposes and should be used responsibly. The goal is to predict horse outcomes based on medical conditions, which can be a valuable task for veterinarians and researchers in the field of animal health.
