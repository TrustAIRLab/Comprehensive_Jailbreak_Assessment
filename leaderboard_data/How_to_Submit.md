# How to submit the measurement results to the leaderboard?

## Settings
We aim to provide a UNIFIED assessment, thus we hope you could use the same dataset/optimization steps/evaluation method.  
The number of optimization steps MUST be set to 50 or 500 (refer to our paper for the description).  
For example, if your method is similar to GCG, you can use 500. Or if your method is like PAIR, you can use 50.  
For the dataset/evaluation method, you could use your own. We will add notes to show your settings.  

## Data details 
To add the data to the leaderboard, please include the following information (details of each information could be found in our paper):  
1. Jailbreak Taxonomy
2. Jailbreak Method
3. Modify the Questions?: ✓ or ✗?
4. Access: while or black box?
5. Models: the models you have tested, such as GPT-4
6. Average: the average ASR on all the models you test

If you are not sure something, for example the Jailbreak Taxonomy, you could fill it with your guess (if you could provide your reasons, it is better). 
We will review it.

Please organize them in a ```md``` table format, name it with ```data_unreviewed.md```.

Then request a PR with the following position structure:  
```
Comprehensive_Jailbreak_Assessment  
└─ leaderboard_data  
    └─ Your_Method_Name_FOLDER  
        └─ data_unreviewed.md
```
After we review it, we will add it to the leaderboard.  





