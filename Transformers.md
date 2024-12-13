
Algorithms that can generate new content / original content are called Gen AI Algorithms. 
# How RNNs worked 

Earlier you would have something like this : 

![[Pasted image 20241212215522.png]]

Where for each token you would generate a hidden state Hx and generate the token Yx for each Hx. Each RNN step would take Xx and Hx-1 to generate Hx  and Yx. 

- Slow. Requires T time steps to generate an output sequence fully. 
- Vanishing / Exploding Gradient Problems.
- Cannot carry context over long term. 

# Transformers 

- Presented in a paper by google in 2017 by Attention is all you need. 
- Gave Attention Mechanism for the first time. 

## Transformer Architecture 




![[attention_research_1.webp]]



- Encoder Layers stacked on top of each other. 
- Decoder layers stacked on top of each other. 

Input sequence and output sequence is given to us. 


For both sequences, 
- generate vector embeddings that capture the meaning of words. 
- Generate the positional encodings to capture the ordering of the words inside the sentence and for the embedding dimensions within the embedding vector. 

![[Pasted image 20241212220507.png]]

![[Pasted image 20241212220530.png]]


### Multi Head Attention

![[Pasted image 20241212220606.png]]


Where Q, K, V are : 

![[Pasted image 20241212220700.png]]
- Then we have the Layer Normalization layer that does 2 things : 

Step 1 : Add the residual connection to the output of the MHA

![[Pasted image 20241212221005.png]]

Step 2 : Normalize the matrix across the features. 

- For each feature, calculate the Myu and the Sigma. 
- Do ![[Pasted image 20241212221133.png]]


For Decoder : 

![[Pasted image 20241212221159.png]]


You simply add the Causal Mask to the Output of Softmax(Q x K.T / Root(D_model))
![[Pasted image 20241212221258.png]]

Then multiply it with the output vector embeddings that constitute Q.

- K and V come from Input (Encoder)
- Q Comes from Decoder Input (Output)

![[Pasted image 20241212221532.png]]

At Inference Time, you Simply keep feeding the Generated Tokens (Starting at [SOS]) to the Decoder Input and keep generating until EOS is reached. 

