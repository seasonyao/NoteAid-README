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

## README Dataset:

Hugging Face Link: https://huggingface.co/datasets/bio-nlp-umass/NoteAid-README  

The Datasets contains the jargon terms, lay definitions, general definitions for different stages in our REAME pipeline. To comply with fair use of law (https://www.copyright.gov/fair-use), We used GPT-3.5 to paraphrase the lay definitions as shown in synthetic_data_creation.ipynb. We used GPT-4o-mini to paraphrase the EHRs as shown in synthetic_EHR_creation.ipynb. We asked the LLM (gpt-4o-mimi) to edit the original sentence but make sure to keep the main terms unchanged. Check that every word in the main terms is in the edited EHR. The meaning of the EHR should remain the same. We also used LLM(gpt-4o-mimi) to verify that the jargon terms are still in the EHRs. Hence, we have a slightly modified EHR with all the jargon terms intact.  

**Datasets**  
The Datasets presented here have jargon terms, lay definitions, general definitions, and EHRs.  
readme_exp - The general definitions are produced from UMLS open-source data.  
readme_exp_good - The general definitions are good for training.  
readme_exp_bad - The general definitions are not good enough for training.  
readme_syn - We used LLMs to generate General definitions  
readme_syn_good - The general definitions are good for training.  
readme_syn_bad - The general definitions are not good for training.  
**Columns**  
ann_text column is the jargon term  
split_print(readme_exp, readme_exp_good, readme_exp_bad) and gen_def(readme_syn, readme_syn_good, readme_syn_bad) columns are the general definitions  
gpt_generated is the GPT3.5 generated lay definitions which are slight modifications of the original lay definitions used.  
gpt_text_to_annotate is the GPT4o-mini generated EHRs which are slight modifications of the original EHRs used.  

## Citation

```
@article{yao2023readme,
  title={README: Bridging Medical Jargon and Lay Understanding for Patient Education through Data-Centric NLP},
  author={Yao, Zonghai and Kantu, Nandyala Siddharth and Wei, Guanghao and Tran, Hieu and Duan, Zhangqi and Kwon, Sunjae and Yang, Zhichao and Yu, Hong and others},
  journal={arXiv preprint arXiv:2312.15561},
  year={2023}
}
```
