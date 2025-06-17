# Creative Requirement Generator (RAG + FLAN-T5 / BERT)

This project is a prototype tool for generating creative software requirements using:
- Retrieval-Augmented Generation (RAG)
- Either FLAN-T5 (for full-text generation) or BERT (for masked word prediction)

## Key Features
- Retrieval-Augmented Generation (RAG) using FAISS
- Sentence embedding with sentence-transformers
- Generative approach with FLAN-T5
- Masked Language Modeling with BERT
- Smart masking using spaCy (verbs and nouns)


## How It Works
### Step 1: Retrieval (RAG)
A small corpus of sample requirements is vectorized using all-MiniLM-L6-v2. Given a base requirement, we retrieve the top-k similar requirements using FAISS.

### Step 2A: FLAN-T5 (Full Generation)
The base requirement + retrieved examples are passed to a FLAN-T5 model. The model generates creative alternatives via natural language generation.

### Step 2B: BERT (Masked Prediction)
A key verb or noun in the base requirement is masked using spaCy. BERT then predicts possible words to fill in the masked position, generating creative variants.

## Sample Corpus
The current prototype uses a small sample set of requirements. You can modify the array according to your need. In real-world use, this corpus would be much larger. But as this is a prototype so tried to keep it smaller.

## Example Output
Base requirement: <br>
**"Users should be able to manage their subscriptions."**

BERT Output: ( Only the masked word is predicted to generate new requirement)
```
1. Users should be able to renew their subscriptions.
2. Users should be able to update their subscriptions.
3. Users should be able to review their subscriptions.
```
FLAN-T5 Output: ( Full sentence is generated )
```
- Users should be able to customize subscription duration.
- Let users change their plan frequency anytime.
- Allow flexible billing options for subscribers.
```

## Future works
- Use masked diffusion or LLM finetuning for higher creativity
- Expand to domain-specific requirement sets

This project is a simple prototype and it is inspired by research in Requirements Engineering, specifically:
- AI in Requirement generation

