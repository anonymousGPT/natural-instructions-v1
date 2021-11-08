# Natural Instructions  

This is an anonymized version of Natural-Instructions for ARR reviews. 
This dataset contains various NLP tasks and their language instructions. 
We have built this data using existing NLP datasets and the instructions that were used to crowdsource them. 

## Dataset 
The data is included in the `tasks` directory.

## Model predictions 
We have the model predictions for the following models: 
```
predictions/gpt3_outputs
```

We will add the BART predictions at a later time. 
The BART predictions, in particular, correspond to a model that was trained on a random subset of tasks and evaluated on the remaining ones.

## Evaluation script 
The script that we used in our evaluation is included in `src/evaluation.py`. 

### How to Evaluate
It requires dataset file path and the prediction file path
E.g. 
```
python3 evaluation.py --predictions ../predictions/gpt3_outputs/subtask002_quoref_answer_generation@_Definition_Prompt@0_100.json --dataset ../Dataset_Jsons/subtask002_quoref_answer_generation.json
```
Filenames in `predictions/gpt3_outputs` are of the format `[taskname]'@'[instruction encoding]'@'[number of examples]'_'[number of instances].json` 

## Encoding the instructions 
The [`encoding function`](src/utils/encodeinstruction.py) is provided to generate encoded instruction inputs.
E.g.
```
encodeinstruction('subtask003_mctaco_question_generation_event_duration', instruction_structure =['Definition','Prompt'])
```
## Baselines 
We have two baselines used in this work:

- GPT-3: we have included the predictions made by our GPT-3 baselines in [`gpt3_output`](gpt3_output). 
If you want to try GPT-3 yourself, you can ask for API access in [this link](https://openai.com/blog/openai-api/). 

- BART: To reproduce our BART predictions, use our [`encoding function`](src/utils/encodeinstruction.py) and train [`a BART model`](https://github.com/huggingface/transformers/tree/master/examples/legacy/seq2seq) on them. 

