# Stress-Testing LLMs: Evaluating Sarcasm Detection Failures in Finance

This repository contains the Python scripts and notebooks used to stress-test Large Language Models (LLMs) against sarcastic financial text. The project maps out exactly where AI fails when reading subtle human social cues on social media.

##  Problem Statement
Many financial companies are letting large language models (LLMs) read online discussions to predict market trends. They do this because regular retail investors talk about markets online all the time, and their posts can actually move stock prices and trading volumes [1][2]. But there is a huge catch: recent studies show that these LLMs take everything literally and completely struggle to understand sarcasm [3].

If a company leaves the AI to read these comments without any human monitoring, it will totally misinterpret the sarcasm. This messes up the sentiment data and feeds wrong information straight into automated trading bots, which can cause massive financial losses [1][2]. Research already shows that AI has major issues handling social ambiguity, consistency, and prompt sensitivity [1].

This project uses community upvote data to stress-test ChatGPT and find out exactly where it goes wrong on these three specific points. Mapping out these errors will show why we still need humans in the workplace. Ultimately, it proves that when AI gets socially blind, human workers are necessary to act as risk auditors and logic gatekeepers.

##  Motivation
Companies are rapidly replacing human employees with automated AI tools. However, AI still has massive limitations, especially in the financial sector, where online peer reviews, stock portfolios, and crypto discussions are used to forecast economic trends and spot scams. If institutions use automated LLMs to monitor these areas, the AI will completely misread social feelings. This can lead to invalid decisions that cause serious financial losses for both institutions and customers.

Both financial companies and retail investors care about this problem and will benefit from a solution that prevents dangerous data errors. The problem is incredibly difficult due to a major technical challenge: LLMs rely on literal keyword-matching algorithms rather than human social intuition. This causes the AI to completely fail when sarcastic text uses positive words to mean negative things.

This problem is highly interesting because it analyses the level of sarcasm an LLM can detect, and whether its decisions flip when tested multiple times with slightly changed prompts. Since AI is taking over workplaces everywhere, now is the right time to prove that AI cannot be trusted alone and that human risk managers are still vital.


##  Research Questions, Objectives and Evaluation

### Research Questions
The core aim of this project is to prove that LLMs like ChatGPT cannot understand sarcasm in a financial context. To find out where these models fail, this practical study will answer three specific research questions:
* **RQ1:** Analyse LLM's ability to understand sarcasm in situations where community upvotes are low?
* **RQ2:** Are LLMs consistent when evaluating the same text under the same prompting conditions?
* **RQ3:** How much does the LLM labelling of sarcasm vary under different rephrasing of the same prompt?

### Project Objectives
To find answers for the research questions, the project will achieve the following seven objectives in order:
* **O1:** Extract the dataset from the sarcasm on Reddit [Finance Data, which is generated from the actual train-balanced-sarcasm.csv data].
* **O2:** Create a Python script for making ChatGPT label the dataset by giving the comments column and the parent comment columns.
* **O3:** Evaluate the accuracy of the overall ChatGPT prediction.
* **O4:** From the finance dataset, extract a target sample with the help of Python, splitting rows into clear sarcastic [ups > 5] and ambiguous [ups < 5] text, then compare the labelling accuracy in those two subsets.
* **O5:** Make a Python script to stress-test ChatGPT by labelling sarcasm on every row 3 times consecutively, under different rephrasings of the same prompt to check for consistency and sensitivity.
* **O6:** Calculate the final accuracy rates and create confusion matrices based on the data from the above objectives.
* **O7:** Make use of this entire research and the final metrics to prove that AI cannot be trusted alone with sarcastic financial data.

### Evaluation Methods
The success of the claim that the project is trying to prove and the performance of LLMs will be evaluated using different statistical methods:

#### 1. Simple Classification Accuracy
To establish a baseline performance score, simple accuracy will be calculated using the following formula:
`Accuracy = [ Number of Correct AI Guesses / Total Number of Comments Tested ] * 100`

This final percentage directly shows how accurately the AI can understand sarcasm compared to the human ground truth. To evaluate the AI's ability to handle ambiguity, this score will be calculated separately for popular comments and low-upvote comments (ups < 5). A significantly lower accuracy score on the ups < 5 subset will mathematically prove that the AI cannot handle subtle, ambiguous text.

#### 2. Confusion Matrix Analysis
To look closely at the exact types of mistakes the AI makes, a 2 X 2 Confusion Matrix will be built based on the human label and the AI label combinations:
* **True Positive [TP] [1,1]:** The human labelled the text as sarcastic, and the AI correctly identified it as sarcastic.
* **True Negative [TN] [0,0]:** The human labelled the text as non-sarcastic, and the AI correctly identified it as non-sarcastic.
* **False Positive [FP] [0,1]:** The human labelled the text as non-sarcastic, but the AI wrongly flagged it as sarcastic (False Alarm).
* **False Negative [FN] [1,0]:** The human labelled the text as sarcastic, but the AI missed it and labelled it as non-sarcastic (Blind Spot).

In a financial context, analysing False Negatives is critical because it counts how many dangerous, sarcastic market warnings the automated system completely missed.

#### 3. Consistency Equation
To check if AI is consistent when labelling the same comment multiple times under the same prompt, a consistency score will be calculated across the different runs: 
`Consistency Score = Total number of Matching Outputs / Total Runs`

A low score here indicates that the AI's processing engine is unstable, giving different answers to the same problem without any changes to the instructions.

#### 4. Prompt Sensitivity Flip Rate
To measure how fragile the AI is when the wording of the instruction is slightly changed (such as swapping the keyword "sarcastic" for "ironic"), the Flip Rate will be calculated:
`Flip Rate = [Total Number of Comments Where AI Changed its Answer / Total Number of Comments Tested] * 100`

A high Flip Rate proves that the AI is just reacting to the specific words in our instructions instead of actually understanding the text. If changing one simple word makes the AI flip-flop its answer, it proves the system is too fragile to trust with financial risk decisions. 

## 5. Technologies and Data Source

### Dataset
The study utilises the “Sarcasm on Reddit” dataset downloaded from [Kaggle](https://www.kaggle.com/datasets/danofer/sarcasm?select=train-balanced-sarcasm.csv) and uses the `train-balanced-sarcasm.csv` file. The dataset is valid because the comments are already labelled as sarcastic [1] and non-sarcastic [0] by the person who made the comment. It also includes a column named `ups`, which indicates the upvote count for a comment, allowing for splitting the data into "loud" popular comments and "quiet" ambiguous ones.

### Technology Stack
The practical experiment is conducted using Python, and the files are saved as `.ipynb` notebooks. The core tools used are:
* **Jupyter Notebooks:** For running experiments step-by-step.
* **Pandas:** Loading, filtering, cleaning, and sorting the financial comments dataset.
* **NumPy:** For calculating mathematical scores, accuracy metrics, and consistency equations.
* **Matplotlib:** To create clean charts and confusion matrix visualizations of the final comparison tests.
