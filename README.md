# Mistral 7B model parameter efficient fine-tuning for dialogue summarization with LoRA

## Introduction

In this experiment I have implemented a parameter efficient fine-Tuning (PEFT) of `Mistral-7B-Instruct-v0.2` base model for dialogue summarization task using the great `samsum` dataset (kudos to Samsung R&D Institute Poland) using LoRA technique.

Summarization is - kind of traditionally speaking - a seq2seq task. This means that it takes one sequence of tokens and transforms it into another. Usually for this group of problems an encoder-decoder architecture model is applied. Mistral 7B as a decoder-only architecture model is rather specialized in autoregressive text generation rather than seq2seq transformation.

In this experiment I wanted to find out how well can such decoder-only model learn to perform better in a non-orthodox type of task like summarization. Spoiler alert: the fine-tuned model performs really well. After fine-tuning Mistral base model with not so many dialogue summarization examples it learned the task pretty well and showed great improvement both in terms of ROUGE metric and also human level clarity of the generated summaries.

If you are interested mostly in the final model performance - please scroll down to the Section 3 of this notebook to see its full evaluation.

You can access the code yourself directly in Colab (https://colab.research.google.com/drive/1EuAldJmYSHi9YwjCGQ4u8ZYpnf7dn1XC?usp=sharing) or clone it from this repository (https://github.com/msznajder/mistral-7b-samsum-dialogue-summary-finetune).

## Setup

As the base model I have used `Mistral-7B-Instruct-v0.2` model.

For fine-tuning I have used `samsum` dialogue summarization dataset (I used over 7k examples out of 14k available).

For GPU memory efficiency I have used LoRA technique for training.

I have run training notebook using Google Colab PRO A100 GPU. Model training run for around 6h. The highest GPU RAM usage reached a little over 30 GB. Running this notebook of lower GPU model will probably lead to this ugly out-of-memory error we all hate so much.

I have conducted the fine-tuned model evaluation using ROUGE metric and analyzing the actually generated summaries. I have also compared fine-tuned model performance with the base model I used.

## Results summary

TLDR; Fine-tuned model learned to generate pretty good and consistent summaries. You can see it in the ROUGEL metric: 0.43 for the fine-tuned model vs. 0.22 for the original base model. Even more importantly, I think, when you check the actually generated summaries it is clearly how much performance the fine-tuned model gained in this task. You can check it out right at the bottom the notebook above.

