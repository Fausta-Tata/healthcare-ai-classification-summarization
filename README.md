# AI-Powered Healthcare Transcription Analysis Using IBM Granite

## Project Overview

This project focuses on analyzing medical transcriptions using AI-powered models. The primary goals are:
- Summarization: Generating concise one-sentence descriptions of patient conditions from raw transcription text.
- Classification: Automatically determining the most relevant medical specialty for each transcription.

The project leverages Granite-13B-Instruct-v2, an instruction-based large language model optimized for classification and summarization tasks. By combining AI with medical transcription data, this project demonstrates how natural language processing can assist healthcare workflows, reduce manual effort, and improve consistency in documentation.

## Raw Dataset Link
Dataset used in this project:

Healthcare Documentation Database on Kaggle

URL: https://www.kaggle.com/datasets/harshitstark/healthcare-documentation-database?resource=download

## Insight & findings
Initial analysis showed a classification accuracy of around **40%**. However, a deeper analysis revealed that this low accuracy was **not due to model failure**, but rather to quality issues within the original dataset's labels.

The key findings are:
1.  **The AI is More Specific than the Dataset:** In many cases, the AI provided answers that were more detailed and contextually accurate than the original labels.
    * **Example:** The dataset labeled a vasectomy case as `Surgery` (general), while the AI correctly classified it as `Urology` (specific).

2.  **Poor Label Quality:** Several labels in the dataset do not describe a medical specialty but rather the document type (e.g., `Consult - History and Phy.`). The AI successfully ignored these irrelevant labels and identified the true specialty based on the transcription's content.
    * **Example:** The dataset labeled a pneumonia case as `Consult - History and Phy.`, while the AI correctly classified it as `Pulmonology`.

3.  **The Importance of Qualitative Analysis:** This project demonstrates that accuracy metrics alone are insufficient. A qualitative analysis of the model's "errors" revealed that the AI often outperformed the "ground truth" provided in the dataset.

## AI support explanation
AI support in this project was used for:
* **Text Classification:** The LLM was instructed to read the unstructured `transcription` text and classify it into one of the predefined `medical_specialty` categories. This process was optimized by providing the list of valid choices directly in the prompt.
* **Text Summarization:** The LLM was also used to generate a brief `description` (summary) of each `transcription`, with specific instructions to limit its length, ensuring a concise and relevant output.
