# NoteAid-README: Bridging Medical Jargon and Lay Understanding for Patient Education through Data-Centric NLP

![Human-ai-loop](https://github.com/seasonyao/NoteAid-README/blob/main/Images/human-ai-loop.png?raw=true)

## Introduction

The Electronic Health Records (EHRs) disseminated to patients during routine health examinations and following surgical procedures encompass a plethora of technical terminology. The intricate medical lexicon employed by healthcare professionals often proves challenging for the general populace to comprehend. In response to this challenge, we devised a methodology to instruct prevailing Natural Language Processing (NLP) models utilizing an extensive dataset of medical records. Employing an innovative strategy, we formulated comprehensive definitions suitable for training purposes. Additionally, we curated layperson-friendly explanations for the technical terminology found in EHRs through consultation with subject matter experts.

## Files

The `Code` folder contains all python notebooks used for this project.

- `Examiner-Augmenter-Examiner.ipynb` is pipeline used to process the input data. We will start with some initial data (jargon term, context, lay definition, UMLS general definition). This is passed through GPT3 to clean the data to find reliable data points. The unreliable data is sent through ChatGPT to find good general definitions. This new dataset is again sent for examination. For further information, you can go through the paper we are writing.
- `All_definitions.ipynb` is used to get the general definition for all the jargon terms using Scispacy UMLS's dictionary.
- `Annotation_processing.ipynb` is used to get the general definition for all the jargon terms using Scispacy UMLS's dictionary.
- `Data_cleaning.ipynb` is the examiner-1 part if the `Examiner-Augmenter-Examiner.ipynb`, used initially during the project.
- `error analysis.ipynb` is used to split the data into multiple cases, based on the number of words in a jargon terms. we analyze the case where there is only a single jargon term and see how many of these jargon terms do not have a general definition.
- `Multiword-jargon-GenDef` shows how the cases where there are many words in jargon and few words might be non medical terms or do not contain UMLS definitions
- `Rouge.ipynb` is used to see scores like Rouge score, readability scores of lay definitions and general definitions to analyze the data we have.
- `sentence_bert.ipynb` is used pick the best general definition from the many available definitions in UMLS for a jargon term. We use the sentenceBERT score between the lay definitions and the available UMLS definitions to pick the best general definition.
- `synthetic_data_creation` is used to create synthetic data for lay definitions as we do not have the licence to show the data we used. We used GPT3.5 to generate the sythetic lay definition using the jargon term and licenced lay definition.

## Datsets Links:

https://drive.google.com/file/d/1CyaxqtZMFAx0yk9pobFhaFTJ9EPLpi4S/view?usp=sharing

The Datasets presented here have the jargon terms, lay definitions, general definitions and some other meta data. The Lay definitions presented here are not the ones used in this paper. We have created synthetic lay definitions using GPT-3.5, as the lay definitions use in the paper are proprietary and we do not have license to release it. You can look at synthetic_data_creation.ipynb to see how the new lay definitions are generated. Because of licensing we are currently unable to provide the EHRs used as context. We will be releasing the EHRs after changing them slightly using GPT4-mini soon and post the link here.

- ann_text column is the jargon term
- split_print(readme_exp, readme_exp_good, readme_exp_bad) and gen_def(readme_syn, readme_syn_good, readme_syn_bad) columns are the general definitions
- gpt_generated is the GPT3.5 generated lay definitions.

## Citation

```
@article{yao2023readme,
  title={README: Bridging Medical Jargon and Lay Understanding for Patient Education through Data-Centric NLP},
  author={Yao, Zonghai and Kantu, Nandyala Siddharth and Wei, Guanghao and Tran, Hieu and Duan, Zhangqi and Kwon, Sunjae and Yang, Zhichao and Yu, Hong and others},
  journal={arXiv preprint arXiv:2312.15561},
  year={2023}
}
```
