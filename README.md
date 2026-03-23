# Group 5
**Members:**  
- Eaint Mon – t3moea00@students.oamk.fi  
- Xuanyu Liu – t3lixu00@students.oamk.fi  
- Yue Chen – yuchen24@students.oamk.fi  
- Ke Zhang – kzhang24@students.oamk.fi  
- Sitt Min – t3mith00@students.oamk.fi  

# week 3 part 1

**Explain pretraining. What it is? What is result from pretraining** 

<img width="879" height="353" alt="pretaining" src="https://github.com/user-attachments/assets/ea592659-fc8a-4fc1-b8df-675f09c9a674" />

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



