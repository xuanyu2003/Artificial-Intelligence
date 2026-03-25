# Group 5
**Members:**  
- Eaint Mon – t3moea00@students.oamk.fi  
- Xuanyu Liu – t3lixu00@students.oamk.fi  
- Yue Chen – yuchen24@students.oamk.fi  
- Ke Zhang – kzhang24@students.oamk.fi  
- Sitt Min – t3mith00@students.oamk.fi  

# Week 3 Monday

we made our own LLM model:[https://colab.research.google.com/drive/1yxVNUEtX52c1bKT0RYJFX_ZbLdzgVqr3?usp=sharing]

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

- Sequence Length(Quantity)
the number of symbols in a sequence (message).

A sequence is a string of symbols (like bits, characters, or signals).
The length simply counts how many symbols are in that sequence.

- Symbol size(Information per symbol)
The amount of information each symbol carries, usually measured in bits per symbol.

**Explain why sequence length is critical source (this explanation is not very well stated in the video, you must probably search for other sources too)**

We want to trade off with the symbols or vocabulary size and sequence length. With longer sequence and small vocabulary, it can lead to slower training execution time and memory usage with more computing power needed but it is able to understand linguistic nuances and context better. With shorter sequences and more vocabulary size, it reduces the number of steps that the model should take and can reduce costs so it is more efficient. Therefore, sequence length is a critical source because it determines the balance between the model’s ability to understand complex context and the computational resources required for training.

**Find out what is sequence length and symbol size with new LLMs today.**

Modern LLMs use much longer sequences than older models. Typical ranges are 8K–32K tokens for common models and 100K–200K tokens for advanced models. A larger sequence length helps the model handle long texts and improves reasoning.
A symbol is a token. Modern LLMs use about 30,000 to 100,000 tokens in their vocabulary.

**Explain term context**

Context means all the previous tokens in a sequence. The model uses this context to predict the next token. It reads tokens one by one, and each prediction depends on everything it has seen so far.

# Tuesday

**Explain how neural network inference is different from training.**

Training is the learning phase of our model where our model is shown a lot of data and it adjusts its weights to become better at predicting the next token. Inference is the generation of new data from the model that we trained during that training phase. We mainly want to see what patterns that our model has internalised in the parameters of its network. 

**Explain what Karpathy means with sampling from a distribution or with biased coin.**

Through the model, we get a probability distribution over possible tokens at each step. By sampling from this distribution, Karpathy means selecting a token randomly, where the likelihood of each token is weighted by its probability which similar to flipping a biased coin. This allows the model to produce more diverse outputs instead of always choosing the highest-probability token.

**What is nano-GPT?**

- Uses just a few hundred lines of Python 
- Focuses only on the core transformer architecture
- Lets you train your own small language model

**Explain reasons why training cost of LLMs has been getting down**

- Dataset quality has improved significantly, with better filtering and preprocessing allowing models to learn more efficiently from less data.
- Hardware has become much faster, greatly reducing training time and cost.
- Software frameworks have improved, making training more efficient and reducing wasted computation.

**Explain Karpathy’s GPT-2 model training example. What did you understood from it?**

Karpathy explains that a neural network is just a giant mathematical expression that mixes input tokens with parameters (weights) using simple operations like multiplication and addition. Training means iteratively adjusting those parameters so the network gets better at predicting the next token, which you can see happening in real time by watching the loss number go down. Once training is done the weights are frozen and you switch to inference feeding tokens in and sampling the next token one at a time from the model's probability distribution, which is exactly what happens when you chat with ChatGPT. He uses GPT-2 as a concrete example, showing his live training run where each update processes 1 million tokens and takes ~7 seconds, needing 32,000 total steps on 8 H100 GPUs rented from the cloud all just to get good at that one task of predicting the next token.

**How much it took from Karpathy to train GPT-2 and what kind of equipment he used?**

Karpathy took ＄672 and only one day to train GPT-2 on a 8xH100 node

# Wednesday

**Explain difference between base model and assistent model**

A base model is trained on large amounts of raw text using unsupervised learning. Its main objective is to predict the next word or token in a sequence. As a result, it generates text based on statistical patterns in the data rather than true understanding of meaning or intent.<br>

An assistant model, such as ChatGPT, is built on top of a base model and further improved through additional training. This includes instruction tuning, where the model learns to follow tasks and respond appropriately, and reinforcement learning from human feedback (RLHF), which helps make responses more helpful, accurate, and aligned with user expectations.

```text
=== Prompt ===
Convert 5 km to meters

=== Base model output ===
“Kilometers are used in many countries and are part of the metric system…”
→ Gives unrelated explanation instead of answer

=== Assistant model output ===
“5000 meters”
→ Correct and concise answer
```````

**Why assistent model training is much shorter than base model**

assistant models reuse most of the base model’s knowledge, so they only need a relatively small amount of additional training to become helpful, safe, and aligned.
Assistant training is shorter because:

- It updates fewer parameters significantly (often small adjustments)
- It uses much less data
- It doesn’t require learning language from scratch
- It focuses on narrow objectives (alignment, not knowledge)

**Explain how assistent model is trained from base model, what is similar to TCP/IP protocol stack?**

Because both systems build functionality layer by layer.
| AI Training Layer         | Similar TCP/IP Layer  | What it does                                          |
| ------------------------- | --------------------- | ----------------------------------------------------- |
| Base model pretraining    | Internet layer (IP)   | Core capability: move information (generate language) |
| Supervised fine-tuning    | Transport layer (TCP) | Structured communication (instructions, conversation) |
| Preference / RL alignment | Application layer     | User-friendly behavior and correct interaction        |
| Safety tuning             | Application policies  | Rules for acceptable use                              |


Key similarity:
- Each layer depends on the lower layer
- You don’t rebuild the base each time
- You add capabilities without changing the foundation too much

**How assistent model is programmed?**

Assistant model is programmed during the post-training after creating a base model from the pretraining stage where the base model is trained on massive amount of internet data. It is programmed by fine tuning the base model into conversation style structure and learning from example dialogues between human and assistant. It will be trained on the statistical conversation patterns rather than large standalone texts from the internet like an internet document simulator. 

**Explain how assistent model training data is tokenized. I.e. how conversations are tokenized**

The tokenisation of the assistant model is by creating special new tokens that gets introduced and interspersed with text to imply whose turn in the conversation between the user and assistant it is, the followup text and the end of their turn to show the boundary between messages. This is how the conversations get turned by some encoding into one dimensional sequences of tokens.

**Explain how assistent training data is obtained.**

Assistant training data is mainly created by humans who are hired to simulate ideal conversations between a user and an AI. These human labelers write prompts (questions or requests) and then craft high-quality responses following detailed guidelines such as being helpful, truthful, and safe. This produces datasets of example conversations that the model learns to imitate. In modern systems, this process is often augmented with other language models that help generate drafts of responses, which humans then review and refine. The final dataset is thus a mix of human-written and AI-assisted conversations, covering many topics and teaching the model how to behave like a helpful assistant.

**How inference is now different when we have new tokens, within chatGPT?**

**When we are asking a question from chatGPT we are actually asking a question from domain experts. Is this true?**

# Thursday
 
**Explain what model hallucination means.**

**Explain why model hallucinates**

**What kind of mitigations there are to improve model behaviour on hallunications?**

**How model is trained to use tools like web-search?**

**Explain the difference between vaque recollection and working memory**

**What are difficult problems for model, why?**

**What happens if you give model a permission to use code**

