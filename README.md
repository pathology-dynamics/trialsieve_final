# TrialSieve
NER on clinical cohort studies for automated meta-analysis of clinical literature.  

This repository will be updated on a rolling basis as new annoatations are processed.

![TrialSieve](trialsieve.png)

# Data
All data for `TrialSieve` can be found in the `data` subdirectory.  The data files contained are as follows:
* `pmid_title_abstract.csv`: File containing PubMedID, title, and abstract of each document in TrialSieve.  Note that both title and abstract were annotated.
* `final_schema_data.csv`: Annotations made using the most up-to-date schema as described in our paper.
* `old_schema_data.csv`: Annotations made using previous versions of the schema
* `all_data.csv`: All annotations merged together, regardless of schema
* `preprocessed_for_modeling.json` Preprocessed data from final schema to be used with NER models


# Reproducing Experiments
## Environment setup
Create and activate the conda environment by running:
```bash
conda create -n trialsieve python=3.11
conda activate trialsieve
pip install -r requirements.txt
pip install --upgrade --force-reinstall thinc spacy
```

## Running Models
To run the models, run the following from the main directory:
```bash
python models/train.py
```

## LLMs
The results using GPT-4o are located in the `llm` folder.

Use `gpt_run.ipynb` to run your own experiments (requires your own OpenAI API key).

Use `eval_gpt_res.ipynb` to evaluate the existing results.

## Entity Definitions

| Entity                          | Definition                                                           |
|---------------------------------|----------------------------------------------------------------------|
| Disease/Condition of Interest   | The specific ailment or condition under investigation.               |
| Dosage                          | Amount of drug to be administered.                                   |
| Drug Intervention               | Specific drug being used to treat or study a condition.              |
| Follow-up period                | The length of time participants are observed after intervention.     |
| Group Characteristic            | Characteristics or traits of the study group (e.g., age, gender).    |
| Group Name                      | Name assigned to a study group (e.g., "control" or "treatment").     |
| Group Population / Sample Size  | Number of individuals in a study group.                              |
| Intervention Administration     | How the intervention is given (e.g., oral, intravenous).             |
| Intervention Duration           | Length of time the intervention lasts.                               |
| Intervention Frequency          | How often the intervention is administered.                          |
| Non-Pharmaceutical Intervention | Non-drug treatments like therapy or lifestyle changes.               |
| Non-Study Drug                  | A drug not being studied but used in the study (e.g., for control).  |
| Outcome (Study Endpoint)        | The main result being studied (e.g., reduction in symptom severity). |
| Qualitative Side Effects        | Subjective side effects reported by participants.                    |
| Quantitative Measurement        | Objective measurements or values.                                    |
| Statistical Significance        | P-values or other metrics showing the significance of results.       |
| Study Duration                  | Total length of the study.                                           |
| Study Years                     | The years during which the study was conducted.                      |
| Type of Quant. Measure          | Kind of quantitative metric used (e.g., mean, median).               |
| Units                           | Measurement units for various metrics.                               |
