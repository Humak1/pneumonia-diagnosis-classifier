# pneumonia-diagnosis-classifier

Can machine learning let non-medical staff triage pneumonia from simple chest x-ray measurements, without waiting for review by a clinician?

Twelve classification models benchmarked, tuned and ensembled on NHS pilot study data, written up for a mixed panel of stakeholders deciding whether to fund a larger follow-on study.

Python, scikit-learn, Jupyter.

The problem

Patients admitted with suspected pneumonia currently wait for a medically qualified member of staff to review their chest x-ray before treatment can be targeted. That wait costs time, and clinicians say outcomes improve when the right treatment starts sooner.

A pilot study produced a dataset with two parts: a set of simple numerical measurements taken from patients' chest x-rays by non-medical staff, and the pneumonia diagnoses later made by medically qualified staff for the same patients.

If a model can predict the clinical diagnosis from the simple measurements alone, non-medical staff could triage patients immediately. The question this project answers is whether that is possible, and whether it is reliable enough to justify funding a larger study.

Approach

Coverage. Twelve classification models were benchmarked rather than one, covering the range of approaches suitable for this kind of tabular binary classification problem, so that the comparison reflects what is achievable rather than what one arbitrary choice happens to produce.

Depth. Key hyperparameters were tuned systematically for each model, and their effects examined, rather than accepting library defaults.

Synthesis. The strongest individual models were combined into ensembles to test whether performance improves beyond any single classifier.

Robustness. Models were compared on held-out validation data using metrics appropriate to a clinical triage problem, where the cost of a missed case is not the same as the cost of a false alarm.

Focus. The analysis closes with a clear recommendation on whether the follow-on study should be funded, together with the caveats a funding panel needs in order to weigh that recommendation.

Results

[ Replace this section with your headline numbers. ]

Model	Key metric	Key metric
Best single model		
Best ensemble		
Baseline		

Recommendation: [ state your funding recommendation and the main reason for it ]

Main caveats: [ the limitations a panel should weigh — sample size, which measurements were available, how performance might change at larger scale ]

Writing for the audience

The report was written for a panel with very different priorities and levels of technical expertise: clinicians, hospital managers, IT managers, patients and funders. A clinician cares whether the model misses cases. A hospital manager cares whether it saves time. A funder cares whether the result will hold at larger scale.

Model performance is therefore presented in terms of what each outcome would mean in a hospital, rather than as metrics alone, and the recommendation is stated plainly enough to be acted on by a reader who does not read confusion matrices.

Repository contents
Machine Learning.ipynb    Full analysis: code, results and written report

Open in Colab using the badge at the top of the notebook.

Data

The notebook loads pneumonia_raw.csv directly from a public URL, so it runs without any local setup. The cleaned dataset it produces (pneumonia_cleaned.csv) is generated at runtime and excluded from the repository.

Features are the numerical chest x-ray measurements taken by non-medical staff, including consolidation width and height, with Pneumonia as the target and Patient_ID dropped. The classes are slightly imbalanced, with more pneumonia-positive than negative patients, which the evaluation takes into account.

Limitations

The pilot study covers a limited number of patients with a limited set of measurements per x-ray. Any model trained on it inherits those limits, and the purpose of the follow-on study would be to establish whether the findings hold with more patients and more measurements.
