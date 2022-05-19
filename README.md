# Improving Consistency for Clinical Summaries by Constraining Beam Search

## Abstract
For medical records, abstractive summarization has been proposed as a means to alleviate clinical documentation burden. While research has been conducted with transformer models for summarizing clinical encounter notes, optimal methods have yet to be discovered. A current limitation of abstractive summarization is that while models can produce highly fluent narratives, they can often produce non-consistent statements that are not supported by the original source text; which is particularly problematic for a clinical summary. I present a new model that improves clinical consistency of an encoder-decoder transformer model by constraining beam search. I create a medical dictionary from SNOMED CT that sets which words are constrained. The model backtracks when presented with a banned word and offers a more consistent output.

## Acknowledgements
I would like to acknowledge the support and guidance from Alexander ’Sasha’ Rush and the permission to reuse some of the core code from Anton Abilov on Github at https://github.com/danton-nlp/factual-beam-search

## Setup
Setup (python 3.10)
Clone the repository and install requirements
```
git clone https://github.com/vincehartman38/clinical-consistency.git
pip install -r requirements.txt
```
Note: The code is designed to run offline on a firewalled/no-network environment due to the security requirements of an ongoing IRB with Weill Cornell (not for MIMIC dataset but this code is the starting project for a larger project). For example, when using resources from Hugging Face transformers library, the code takes into account the environment variable TRANSFORMERS_OFFLINE=1. And when loading NLTK, I separately download the language libraries and used an offline version

## Use of MIMIC-III Dataset
Please create a directory `/data` and load the following datasets for building the models by requesting permission for the MIMIC dataset. I am not permitted to shared the MIMIC dataset publicaly, so you must request approval and acquire yourself:

[MIMIC-III Clinical Database](https://physionet.org/content/mimiciii/1.4/) From this dataset, you need to create a directory `/data/mimic-III-datasey` and load the following CSV files into that directory: (1) ADMISSIONS.CSV, (2) CAREGIVERS.CSV, (3) NOTEVENTS.CSV, (4) PATIENTS.CSV

## Models
Please store models in a directory `/models`. I provide a script for how to generate a model with BART.
