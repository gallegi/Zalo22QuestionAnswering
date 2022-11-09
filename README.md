# 1. About the project:
- Basic solution for Zalo AI Challenge 2022, track "E2E Question Answering": https://challenge.zalo.ai/portal/e2e-question-answering
- Architecture
  - Document retrieval using Pyserini
  - Question classification using tf-idf and logistic regression
  - Vietnamese question answering using pretrained Huggingface model
- Main dependencies:
  - transformers
  - huggingface

# 3. How to run:
## 3.0. Data preparation
- Unzip Lyrice Alignment data inside data/ folder
- The structure should look like this
  - ----- data
  - --------|-- e2eqa-train+public_test-v1
## 3.1. Generate look-up database:
- Purpose: Create a look-up database for document retrieval. Each document is encoded into a sparse vector
- Run CreateIndex.ipynb. The notebook outputs folder: data/lookup_db
# 3.2. Train question classification model:
- Train a model to classify whether a question ask for an entity, a date or a number
- Run QuestClassify.ipynb, outputs pickle file: models/question_classifier.pkl
## 3.3. Evaluate on the whole train set:
- Run Predict On Train.ipynb. The notebooks output file: valid_predictions/baseline.json
- Run ComputeSocres.ipynb. The notebook output validation score
## 3.4. Predict:
- Run Predict On Test.ipynb. The notebooks output folder: submissions/baseline_for_sub.json
