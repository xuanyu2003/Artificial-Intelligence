# Group 5
**Members:**  
- Eaint Mon – t3moea00@students.oamk.fi  
- Xuanyu Liu – t3lixu00@students.oamk.fi  
- Yue Chen – yuchen24@students.oamk.fi  
- Ke Zhang – kzhang24@students.oamk.fi  
- Sitt Min – t3mith00@students.oamk.fi  

# week 3 part 1

https://colab.research.google.com/drive/1LwDtJnD6BkjmSH1IV5PjnuQ-Irn9nJSJ?usp=sharing

**Explain pretraining. What it is? What is result from pretraining** 

<img width="879" height="353" alt="pretaining" src="https://github.com/user-attachments/assets/ea592659-fc8a-4fc1-b8df-675f09c9a674" /><br>

Pretraining is the process of training a language model on a very large amount of raw text data so it can learn the general structure of language, patterns, and knowledge.<br>
After pretraining, you get a base model.it might can answer Continue text Generate paragraphs answer questions

**Name all the steps within pretraining** 

1.download  and process the internet Large amounts of text are collected (e.g., from the internet, books, and articles) and cleaned to remove low-quality or duplicate content.<br>
2.Tokenization<br>
The text is converted into numerical tokens so the model can process it.<br>
3.Neutral network training 

**Explain terms sequence length and symbol size** 

1.Sequence Length(Quantity)
the number of symbols in a sequence (message).

A sequence is a string of symbols (like bits, characters, or signals).
The length simply counts how many symbols are in that sequence.

2.Symbol size(Information per symbol)
The amount of information each symbol carries, usually measured in bits per symbol.

**Explain why sequence length is critical source (this explanation is not very well stated in the video, you must probably search for other sources too)**

We want to trade off with the symbols or vocabulary size and sequence length. With longer sequence and small vocabulary, it can lead to slower training execution time and memory usage with more computing power needed but it is able to understand linguistic nuances and context better. With shorter sequences and more vocabulary size, it reduces the number of steps that the model should take and can reduce costs so it is more efficient. Therefore, sequence length is a critical source because it determines the balance between the model’s ability to understand complex context and the computational resources required for training.

**Find out what is sequence length and symbol size with new LLMs today.**

Modern LLMs use much longer sequences than older models. Typical ranges are 8K–32K tokens for common models and 100K–200K tokens for advanced models. A larger sequence length helps the model handle long texts and improves reasoning.
A symbol is a token. Modern LLMs use about 30,000 to 100,000 tokens in their vocabulary.

**Explain term context**

Context means all the previous tokens in a sequence. The model uses this context to predict the next token. It reads tokens one by one, and each prediction depends on everything it has seen so far.

**Part 2 (Tuesday)**

**Explain how neural network inference is different from training.**

Training is the learning phase of our model where our model is shown a lot of data and it adjusts its weights to become better at predicting the next token. Inference is the generation of new data from the model that we trained during that training phase. We mainly want to see what patterns that our model has internalised in the parameters of its network. 

**Explain what Karpathy means with sampling from a distribution or with biased coin.**

Through the model, we get a probability distribution over possible tokens at each step. By sampling from this distribution, Karpathy means selecting a token randomly, where the likelihood of each token is weighted by its probability which similar to flipping a biased coin. This allows the model to produce more diverse outputs instead of always choosing the highest-probability token.

**Explain Karpathy’s GPT-2 model training example. What did you understood from it?**

Karpathy explains that a neural network is just a giant mathematical expression that mixes input tokens with parameters (weights) using simple operations like multiplication and addition. Training means iteratively adjusting those parameters so the network gets better at predicting the next token, which you can see happening in real time by watching the loss number go down. Once training is done the weights are frozen and you switch to inference feeding tokens in and sampling the next token one at a time from the model's probability distribution, which is exactly what happens when you chat with ChatGPT. He uses GPT-2 as a concrete example, showing his live training run where each update processes 1 million tokens and takes ~7 seconds, needing 32,000 total steps on 8 H100 GPUs rented from the cloud all just to get good at that one task of predicting the next token.

How much it took from Karpathy to train GPT-2 and what kind of equipment he used?
Karpathy took ＄672 and only one day to train GPT-2 on a 8xH100 node
