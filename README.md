# Chatbot-For-Psychotherapy
Use SFT, Preference Optimization (DPO, KTO, IPO) and RAG base on Llama3, Falcon and GPT to develop a chatbot simulate people with mental issues. Use SelfCheckGPT NLI and G-EVAL scores in LLM evaluation.

Detailed peformance analysis refer to: JiazhenLiu_Research.pdf

Dataset and models refer to: https://huggingface.co/JiazhenLiu01.  

Output and Evaluation refer to: https://drive.google.com/drive/folders/1wN5xfkBX7HkZ5Bk_wyjEFN4of0Fa8UpR?usp=sharing







## Analysis
Abstract - With the development of large language models (LLMs), these increasingly 
mature models are being applied across various interdisciplinary fields. The psychological 
domain is one of the significant areas for LLM application. To date, most LLMs have 
been used to simulate therapists, aiming to reduce the cost of psychotherapy and make it 
more accessible. This paper proposes the development of a bot that simulates people with 
mental issues. This innovation can aid in training interns and offer therapists deeper 
insights into their patients' experiences. The objective of my research is to create a bot 
that simulates a single patient's dialogue using LLMs, drawing from existing 
psychotherapy transcripts. This study utilizes three different training methods:
Supervised Fine-Tuning (SFT), Preference Tuning, and Retrieval-Augmented 
Generation (RAG) based on three types of LLMs (Llama3, Falcon, and GPT). Through 
both automated and human evaluations, the superiority of Preference Tuning and 
Retrieval-Augmented Generation (RAG) is demonstrated, proving their potential for 
large-scale application in psychotherapy chatbots. Additionally, the consistency between 
automated and human evaluations confirms the potential of SelfCheckGPT NLI and G-EVAL scores in LLM evaluation.
Index Terms – psychotherapy, chatbot, natural language processing, large language model, 
supervised fine-tuning, preference tuning, retrieval-augmented generation, large language 
model evaluation.


Index Terms – psychotherapy, chatbot, natural language processing, large language model,
supervised fine-tuning, preference tuning, retrieval-augmented generation, large language
model evaluation

### Experimental Setup
The study employs three methods (supervised fine-tuning, preference tuning and retrieval augmented generation) based on three different LLMs (Llama3-8b, Falcon-7b and GPT) to train models to simulate a single patient’s response during the psychotherapy based on given transcripts. Automated evaluations are then used to compare within each method, and finally, human evaluation is conducted for all models. This chapter introduces the preparation of the dataset, the LLMs and the three methods used in the study, and finally the evaluation methods.
3.1	Environment
Development Environment:
	PyTorch Version: 2.1.0
	Python Version: 3.10 (Ubuntu 22.04)
	CUDA Version: 12.1
	GPU: NVIDIA RTX 4090 (24GB) x 1
	CPU: 12 vCPU Intel(R) Xeon(R) Platinum 8352V @ 2.10GHz

3.2	Dataset
The psychotherapy transcripts used in this study are sourced from the STEP (Staged Treatment in Early Psychosis) research project. Established in 2016, the STEP research involves psychotherapists and researchers working at five Headspace sites in Melbourne, as well as the Orygen Youth Health PACE (Personal Assessment and Crisis Evaluation) clinic. The STEP project is dedicated to early intervention for young people at risk of psychosis and is one of Orygen's largest research initiatives. For more details, please visit the website: https://www.orygen.org.au/Research/Current-studies/STEP-study.
3.2.1	Preprocessing
The data used in this article are derived from conversations between psychotherapist and one single patient, recorded in audio and transcribed into text format. Fig. 1 illustrates the format of the unprocessed raw data sample. (where S1 represents the therapist and S2 represents the patient).	

 ![image](https://github.com/user-attachments/assets/eef3b9db-8500-4cab-a4d3-351954716a0f)
Fig. 1 Raw data sample.
The text is transcribed from audio recordings, there are terms such as [inaudible], [redacted], and [crosstalk] present in the text. Table 1 illustrates the processing for these  
terms. I use the BERT model (Devlin, Chang, Lee, & Toutanova, 2019) to predict the word for [MASK] in cases of [inaudible], [redacted], and [crosstalk]. Then, I remove words representing laughter and other actions, and directly replace uncertain words.





