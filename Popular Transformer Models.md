


## BERT 


![[Pasted image 20241212222302.png]]


Bidirectional Encoder Representation from Transformer

- Encoder Only Architecture 

### Training 

- Used 2 Objectives : 
	- NSP : Next Sentence Prediction 
	- MLM : Masked Language Modeling 

Input looks like : [CLS] Token1 Token2 Token3 .... SEP Token N+1 TokenN+2 ......SEP
- Some words are masked at the input level 

Output Looks like [CLS] Token1 Token2 Token3 .... SEP Token N+1 TokenN+2 ......SEP
- Masked Tokens are predicted along with the given tokens 
- Only the BCE loss for predictions for Masked Tokens is taken into account
- CLS Token = 0/1 and states whether sentence 2 follows sentence 1


## GPT 

![[Pasted image 20241212223648.png]]

- Famous for Pretraining and Finetuning on Specific Tasks 
- Decoder Only Architecture

## T5 Text To Text Transfer Learning Transformer 

- Transformer Architecture 
- Trained on sanitized version of C4 Common Crawl. 
- Google Developed 
- All Tasks are treated as generation tasks. 
- Each type of task is separated by an starting tokens specifying what the task is
	- Stsb : Sentence Similarity 
	- Grammer : 
	- Translation : 
	- etc 

- Semi Causal Mask 
	- Mask is fully visible during the task token inputs. 
	- Mask Becomes Causal for the duration of Actual Tokens. 

![[Pasted image 20241212224301.png]]