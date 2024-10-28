# Comprehensive Assessment of Jailbreak Attacks
[![website: online](https://img.shields.io/badge/website-online-blue.svg)](https://junjie-chu.github.io/Public_Comprehensive_Assessment_Jailbreak/)
[![dataset: released](https://img.shields.io/badge/dataset-released-green.svg)](https://github.com/TrustAIRLab/Comprehensive_Jailbreak_Assessment/tree/main/forbidden_questions)

This is the **official** public repository of the paper [*Comprehensive Assessment of Jailbreak Attacks Against LLMs*](https://arxiv.org/abs/2402.05668).  
*All the following updates will be released here first in the future.*  

*Be careful! This repository may contain harmful/offensive responses. Users need to use this repository responsibly.*

## How to use this repository?
### Install and set the ENV
1. Clone this repository.
2. Prepare the python ENV.
```
conda create -n CJA python=3.10
conda activate CJA
cd PATH_TO_THE_REPOSITORY
pip install -r requirements.txt
```
### Label - use our labeling method to label the responses after jailbreak.

**Option 1: label single file**  
1. Switch directory:  
```
cd ./scripts_label
```
2. Command to label single file:
```
python label.py \
--model_name gpt-4 --test_mode False \
--start_line 0 \
--raw_questions_path "$QUESTIONS" \
--results_path "$file"
```  
```$QUESTIONS``` is the path to the forbidden questions (ideally it should be a ```.csv``` file, refer to ./forbidden_questions/forbidden_questions.csv for example).  
```$file``` is the path to the LLM responses after jailbreak, it should be a ```.json``` file. The ```.json``` file could be generated by the following codes.
```
answers.append({'response': answer})
# Write into the output file
with open(output_file, 'w') as out_file:
    json.dump(answers, out_file, indent=4)
```
Note that ```answer``` is the response from the target LLM suffering jailbreak attacks. 

**Option 2: label files in a directory**  
You may also utilize label.sh to label files in a directory:  
```
bash label.sh PATH_TO_RESPONSES_DIRECTORY
```
***The files storing the labels will be saved to the same directory where you store the jailbreak responses.***   
***NOTE: We have omitted the harmful responses related to the project. For example, the few-shot examples in scripts_label/label.py. Feel free to use your own examples.***

### Defense - use our defense scripts to detect the jailbreak prompts (adv prompts).
1. Switch directory:  
```
cd ./scripts_defense
```
2. Execute the defense:
```
bash ./defense_execute.sh DEFENSE_METHOD PATH_TO_YOUR_ADV_PROMPTS_FOLDER
```
Currently, seven defense methods are supported (refer to ./scripts_defense/defense_execute.sh for details).

The adv prompts folder should follow such a structure:
```
examples_jailbreak_prompts
└─ adv_basic.json
```
The ```.json``` file could be obtained by the following codes:
```
adv_prompts = [prompt_1, prompt_2, ...] # a list of adv prompts
json_file = OUTPUT_PATH
with open(json_file, 'w') as outfile:
    json.dump(adv_prompts, outfile, indent=4)
```
Refer to folder ./example_adv_prompts for an example.  

## Add new results to the leaderboard.
Welcome to submit your own evaluation results (steps = 50) of jailbreak attacks to us.  
The submission instruction is available [here](https://github.com/TrustAIRLab/Comprehensive_Jailbreak_Assessment/edit/main/leaderboard_data/How_to_Submit.md).  
The leaderboard is available [here](https://junjie-chu.github.io/Public_Comprehensive_Assessment_Jailbreak/leaderboard).  

*Full codes will be released after the paper is accepted.* 

## TO DO

- [ ] Check the env file requirements.txt.
- [ ] Test the guide in the README.md.
- [ ] Clean the codes/comments.
