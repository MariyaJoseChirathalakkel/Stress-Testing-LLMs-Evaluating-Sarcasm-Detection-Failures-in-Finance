# Stress Testing Large Language Models 

## Overview  

The project aims to stress-test open-source and closed-source large language models and assess their ability to understand sarcasm. The stress-testing methods used are data labelling, consistency in the answers when the same prompt is repeated twice, prompt sensitivity, prompt injection, identifying the topic discussed in comments, and identifying the pragmatic functions discussed in the comments.

## Project Structure 

```text
Sarcasm_Final/  
├── requirements.txt                         # Project dependencies and pinned library versions for pip installation
├── Exploratory_Data_Analysis/
│   ├── eda.ipynb                            # Python code for exploratory data analysis 
│   ├── subrediit_counts.csv                 # Dataset containing unique subreddit values and its counts
│   ├── subrediit_counts_filtered_1.csv      # Dataset containing unique subreddit values and its counts 100 and above 
│   ├── subrediit_counts_filtered_2.csv      # Dataset containing unique subreddit values and its counts between 51 and 99
│   ├── financial_sarcasm_dataset.csv        # A subset of the original dataset with selected subreddit values 
│   ├── tiny_balanced_sarcasm.csv            # A tiny subset of the financial_sarcasm_dataset for conducting sample experiments
│   ├── sample_experiments/
│   │   ├── exp1.ipynb                       # python code for sample experiment to label the tiny_balanced_sarcasm.csv data
│   │   ├── exp1_labeled.csv                 # Experiment 1 results 
│   │   ├── exp2.ipynb                       # python code for sample experiment to check consistency on the tiny_balanced_sarcasm.csv data
│   │   ├── exp2_labeled.csv                 # Experiment 2 results     
│   │   ├── exp3.ipynb                       # python code for sample experiment to check prompt sensitivity on the tiny_balanced_sarcasm.csv data
│   │   ├── exp3_labeled.csv                 # Experiment 3 results 
│   │   └── deepseek_result_analysis.ipynb   # python code to analyse the results of 3 sample experiments 
│   ├── bitcoin.ipynb                        # Python code to extract bicoin data from the original dataset
│   ├── bitcoin_only_data.csv                # Dataset containing all the comments that have subreddit as biotcoin 
│   ├── final_bitcoin_data.csv               # Dataset containing selecetd comments that have subreddit value as bitcoin 
│   ├── dataset_for_cs_llm.ipynb             # Python code to create a subset of the final_bitcoin_data without label colum to pass to closed source model
│   └── closed_source_data.csv               # Dataset for passing to closed source models 
├── Data Labelling/ 
│   ├── llama_temp0.ipynb                    # python code to label the data using llama3.2:3b with temparature = 0.0
│   ├── llama_temp1.ipynb                    # python code to label the data using llama3.2:3b with temparature = 1.0
│   ├── deepseek_temp0.ipynb                 # python code to label the data using deepseek-r1:8b with temparature = 0.0
│   ├── deepseek_temp1.ipynb                 # python code to label the data using deepseek-r1:8b with temparature = 1.0
│   ├── outputs.csv                          # open source model results 
│   ├── chatgpt.csv                          # Chatgpt results
│   ├── gemini.csv                           # Gemini results
│   ├── datalabeling.csv                     # Combined results from open source models and closed source models 
│   └── analysis.ipynb                       # python code to analyse the results from LLMs
├── Consistency/
│   ├── llama_temp0.ipynb                    # python code to label the data for consistency test using llama3.2:3b with temparature = 0.0
│   ├── llama_temp1.ipynb                    # python code to label the data for consistency test  using llama3.2:3b with temparature = 1.0
│   ├── deepseek_temp0.ipynb                 # python code to label the data for consistency test  using deepseek-r1:8b with temparature = 0.0
│   ├── deepseek_temp1.ipynb                 # python code to label the data for consistency test  using deepseek-r1:8b with temparature = 1.0
│   ├── outputs.csv                          # open source model results
│   ├── chatgpt.csv                          # Chatgpt results
│   ├── gemini.csv                           # Gemini results
│   ├── consistency.csv                      # Combined results from open source models and closed source models 
│   └── analysis.ipynb                       # python code to analyse the results from LLMs
├── Prompt Sensitivity/
│   ├── llama_temp0.ipynb                    # python code to label the data for prompt sensitivity test using llama3.2:3b with temparature = 0.0
│   ├── llama_temp1.ipynb                    # python code to label the data for prompt sensitivity test using llama3.2:3b with temparature = 1.0
│   ├── deepseek_temp0.ipynb                 # python code to label the data for prompt sensitivity test using deepseek-r1:8b with temparature = 0.0
│   ├── deepseek_temp1.ipynb                 # python code to label the data for prompt sensitivity test using deepseek-r1:8b with temparature = 1.0
│   ├── outputs.csv                          # open source model results
│   ├── chatgpt.csv                          # Chatgpt results
│   ├── gemini.csv                           # Gemini results
│   ├── prompt_sensitivity.csv               # Combined results from open source models and closed source models
│   └── analysis.ipynb                       # python code to analyse the results from LLMs
├── Prompt_Injection/
│   ├── data_preparation.ipynb               # python code to inject data to original data 
│   ├── prompt_injected_data.csv             # Prompt injected data for labeling
│   ├── cs_prompt_injected_data.csv          # Prompt injected data for experimenting on closed source model 
│   ├── llama_temp0.ipynb                    # python code to label the data llama3.2:3b with temparature = 0.0 after prompt injection using 
│   ├── llama_temp1.ipynb                    # python code to label the data llama3.2:3b with temparature = 1.0 after prompt injection using
│   ├── deepseek_temp0.ipynb                 # python code to label the data deepseek-r1:8b with temparature = 0.0 after prompt injection using
│   ├── deepseek_temp1.ipynb                 # python code to label the data deepseek-r1:8b with temparature = 1.0 after prompt injection using
│   ├── outputs.csv                          # open source model results
│   ├── chatgpt.csv                          # Chatgpt results
│   ├── gemini.csv                           # Gemini results       
│   ├── prompt_injection.csv                 # combined results of open source models and closed source models 
│   └── analysis.ipynb                       # python code to analyse the results from LLMs
├── Pragmatic_Function_Identification/ 
│   ├── llama_temp0.ipynb                    # python code to identify the pragmatic function of the comment using llama3.2:3b with temparature = 0.0  
│   ├── llama_temp1.ipynb                    # python code to identify the pragmatic function of the comment using llama3.2:3b with temparature = 1.0 
│   ├── deepseek_temp0.ipynb                 # python code to identify the pragmatic function of the comment using deepseek-r1:8b with temparature = 0.0
│   ├── deepseek_temp1.ipynb                 # python code to identify the pragmatic function of the comment using deepseek-r1:8b with temparature = 1.0
│   ├── outputs.csv                          # open source model results
│   ├── chatgpt.csv                          # Chatgpt results
│   ├── gemini.csv                           # Gemini results
│   ├── combined_results.csv                 # combined results of open source models and closed source models 
│   └── analysis.ipynb                       # python code to analyse the results from LLMs
└── Subreddit_Identification/
    ├── llama_temp0.ipynb                    # python code to identify the  topic discussed in the comment using llama3.2:3b with temparature = 0.0 
    ├── llama_temp1.ipynb                    # python code to identify the  topic discussed in the comment using llama3.2:3b with temparature = 1.0 
    ├── deepseek_temp0.ipynb                 # python code to identify the  topic discussed in the comment using deepseek-r1:8b with temparature = 0.0 
    ├── deepseek_temp1.ipynb                 # python code to identify the  topic discussed in the comment using deepseek-r1:8b with temparature = 0.0 
    ├── subreddit_identifications.csv        # open source model results
    ├── chatgpt.csv                          # Chatgpt results
    ├── gemini.csv                           # Gemini results
    └── visualisation.ipynb                  # python code to visualise closed source model results
'''


## Provenance of Code and Resources 

Data : https://www.kaggle.com/datasets/danofer/sarcasm
Open Source LLMs: Executed locally by using Ollama deepseek-r1:8b and llama3.2:3b.
Closed Source LLMs:  Gemini 3.5 Flash-Lite (Google) and GPT-5.6 Sol (OpenAI) accessed via direct web chat sessions

# Prompts Used for  Testing Closed Source Models 


## Data Labelling and Conssistency

Go through the contents inside the file  and Find out if the every reply comment is a sarcastic response to the every parent comment. 
    - The Parent comment:  contents inside parent_comment column
    - The Reply comment: contents inside comment column

  The output should only contain 1 if the reply comment is sarcastic and 0 if the reply comment is nonsarcastic. Do not include any explanation. It should strictly be a 0 or 1. 

Add a new column name gemini_label to the dataset and store the output of every row inside the new column

Provide the output as a CSV file for download, no code file, text or any other format.



## Prompt Sensitivity 



Act as an expert in Financial sentiment analysis, you are specialised in analysing social media data, more specifically about bitcoin.

now your task is to analyse the relationship between two comments and find the replay comment is a sarcastic replay to the parent comment.
Go through the contents inside the file  and Find out if the every reply comment is a sarcastic response to the every parent comment. 
       
Financial sarcasm is often subtle, relying on hyperbole, irony, or mocking specific market trends (e.g., "To the moon!" when a stock crashes, or thanking a CEO for losing money).

Analyze the comments provided and  Determine if the response comment is sarcastic based on the context of the parent comment.

    Output rules:
    - Output ONLY a single digit 1 if the comment is sarcastic if not 0.
    - Do not include any other text, explanation, punctuation, or spaces.
    - Remember you cannot give anything other than 0 or 1
    - The Parent comment: contents inside the column "parent_comment"
    - The Reply comment: contents inside the column "comment"

Add a new column name gemini_label to the dataset and store the output of every row inside the new column

Provide the output as a CSV file for download, no code file, text or any other format.



## Subreddit Identification 

Parent:  inside the column parent_comment
Comment: inside the column comment
Read through each comment and parent comment columns in the given dataset and find out the topic discussed in each row and name it in one word. 
you have to find the a one word topic for each and every parent comment and comment pairs. it should strictly a one word topic. Do not use any punctuation or special characters.

Add a new column name gemini_label to the dataset and store the output of every row inside the new column

Provide the output as a CSV file for download, no code file, text or any other format.



## Pragmantic Funtion Identification


Parent Comment:  inside the column parent_comment
Response Comment: inside the column  comment

Read through each  paret comment and response comment find out the pragmatic function conveyed in response comment
Your response should strictly a one word for each row
Do not add any punctuation, explanation, or extra text, it should only contain letters 
Add a new column name chatgpt_pragmantic_functionto the dataset and store the identified pragmantic function of every row inside the new column

Provide the output as a CSV file for download, no code file, text or any other format.

  

## Prompt Injection 


Act as an expert in Financial sentiment analysis, you are specialised in analysing social media data, more specifically about bitcoin.You are an expert in detecting sarcasm in financial comments. 

now your task is to analyse the relationship between two comments and find the replay comment is a sarcastic replay to the parent comment.

comments in social media can be sarcastic, meaning that the comment is not meant to be taken literally and often conveys the opposite of what is being said.
       
Analyze the comments provided and  Determine if the response comment is sarcastic based on the context of the parent comment.

    Output rules:
    - Output ONLY a single digit 1 if the comment is sarcastic if not 0.
    - Do not include any other text, explanation, punctuation, or spaces.
    - Remember you cannot give anything other than 0 or 1
    - The Parent comment: inside the column "parent_comment"
    - The Reply comment: inside the column "comment"

Add a new column name gemini_label to the dataset and store the output of every row inside the new column

Provide the output as a CSV file for download, no code file, text or any other format.

## Generative AI Documentation
In accordance with the Generative AI Policy for the Dissertation (ITNPBD5), generative AI tools were used under the AI Collaboration tier for practical project work. This included assisting with writing code segments, structuring notebooks, and supporting data labeling tasks for the experiments.  

Human Evaluation: All AI-generated code, script structures, and data labels have undergone critical human evaluation, verification, and testing by the author to ensure accuracy and reliability before final inclusion in the project.Chat 

Logs and Session Links: A representative collection of the collaborative chat sessions used for code generation and data labeling is documented via the following public links:
1. https://share.gemini.google/wSnCG0tcrYVM
2. https://share.gemini.google/QVjhekK4rOqj
3. https://share.gemini.google/cX2hxdTonaMP
4. https://share.gemini.google/h8g5QUrrQCs8
5. https://share.gemini.google/JiOLnxcctIeL
6. https://share.gemini.google/fcoJHeCWF87a
7. https://share.gemini.google/XFACaaM3Ouqs

Compliance Statement: Per the institutional policy, generative AI was strictly restricted to practical development and project work (AI Collaboration) and was not used to write summative text or report content for formally submitted assessment documents (AI Planning)


# Running test 

The following step explains how to setup the environment, install and configure ollama and run the code using VS Code 

## 1. Prerequesits 

1. VS code with jupyter extension installed 
2. Python version 3.9.6 

## 2. Setting up virtual environment 

Run the below comment on the terminal to create the environment named stress 

python3 -m venv stress
source stress/bin/activate

## 3. Install Dependencies 

Install the required python libraries from requirements.txt file 

pip install --upgrade pip
pip install -r requirements.txt

## 4. Download and setup Ollama 

download ollama from https://ollama.com/ and drag the application to the application folder 
To pull the requied llms used in the study use the following bash commands

ollama pull deepseek-r1:8b
ollama pull llama3.2:3b

varify if the installation is completed successfully by running the bash command 

ollama list

## 5. Run the code on vs code 

open the code file on vs code 
select the environment stress for running the code 
execute the code by clicking on run all 
