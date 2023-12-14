# NoteAid-README

The `Code` folder contains all python notebooks used for this project.

- `Examiner-Augmenter-Examiner.ipynb` is pipeline used to process the input data. We will start with some initial data (jargon term, context, lay definition, UMLS general definition). This is passed through GPT3 to clean the data to find reliable data points. The unreliable data is sent through ChatGPT to find good general definitions. This new dataset is again sent for examination. For further information, you can go through the paper we are writing.
- `All_definitions.ipynb` is used to get the general definition for all the jargon terms using Scispacy UMLS's dictionary.
- `Annotation_processing.ipynb` is used to get the general definition for all the jargon terms using Scispacy UMLS's dictionary.
- `Data_cleaning.ipynb` is the examiner-1 part if the `Examiner-Augmenter-Examiner.ipynb`, used initially during the project.
- `error analysis.ipynb` is used to split the data into multiple cases, based on the number of words in a jargon terms. we analyze the case where there is only a single jargon term and see how many of these jargon terms do not have a general definition.
- `Multiword-jargon-GenDef` shows how the cases where there are many words in jargon and few words might be non medical terms or do not contain UMLS definitions
- `Rouge.ipynb` is used to see scores like Rouge score, readability scores of lay definitions and general definitions to analyze the data we have.
- `sentence_bert.ipynb` is used pick the best general definition from the many available definitions in UMLS for a jargon term. We use the sentenceBERT score between the lay definitions and the available UMLS definitions to pick the best general definition.
 
