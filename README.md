# Automatic Prompt Optimisation

## Description
1. We have reproduced the algorithm of [AutoHint](https://arxiv.org/abs/2307.07415) for automatic prompt optimisation for BBII 2 tasks: Epistemic Reasoning and Hyperbaton
2. Improved the runtime of algorithm by sampling before hint generation( ~2.5x speedup)
3. Reproduced and evaluated on GPT3.5 and LLaMA2 in addition to GPT-4
4. Generalised the summarisation prompt to improve the quality as well as give more general enrichments
5. Proposed 2 sampling methods to improve the selection of hints in terms of diversity and specificity:
   - Confidence based sampling: Multi-turn CoT prompting to give confidence of prediction from LLMs, and then select top-k most wrong predicitons or samples for max information gain
   - Prediction based sampling: Random balanced sampling based on class(label) and type of prediction(incorrect and correct)
6. Improved candidate generation for few-shot demonstrations: Retrieve the K-nearest neighbour based on BERT embedding during few shot inference and provide them as input-output demonstrations

## Setup instructions

1. ```pip install -r requirements.txt```
2. For the BigBenchII dataset clone this repoistory [automatic_prompt_engineer](https://github.com/keirp/automatic_prompt_engineer/tree/main)
3. For LLaMA2 access, register on this [link](https://ai.meta.com/resources/models-and-libraries/llama-downloads/) and fill the form

## Code structure
```
- notebooks
    -llama
      |- llama-fewshot.ipynb (for improved and baseline fewshot inference)
      |- llama-confidence-sampling.ipynb (multi-turn CoT confidence based sampling)
      |- llama-baseline.ipynb (reproduction of baseline for LLaMA2)
- data: data splits to reproduce
    |- train_entail.json (entailment)
    |- val_entail.json
    |- test_entail.json
    |- train_hyper.json (hyperbaton)
    |- val_hyper.json
    |- test_hyper.json
- requirements.txt
```

## Results
