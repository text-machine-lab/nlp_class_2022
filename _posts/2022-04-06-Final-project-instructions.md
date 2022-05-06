---
toc: true
layout: post
description: NLP class final project description
categories: [markdown]
title: Final Project
---

For your final project, you will need to extend your HW5 to produce a high-quality sequence-to-sequence system.
This could be machine translation, multilingual machine translation, summarization, dialogue generation, code generation, or another seq-to-seq task of your choice.
We provide you with a list of recommended datasets at the end of this document.

We strongly advise that you work in groups of two. Note that we expect both of you to make equal contributions to the codebase. If you would like to work on a project individually, please talk to us. You will need to let us know who is on your team in your design document due Apr 12.

> Optionally, you can propose a different final project.
> In this case, you need to discuss it with a TA before Apr 12.
> You need to provide a task description, dataset, metrics, and what codebase you will use for it.

Your project should contain the following elements:

1. Unlike HW5, your model should contain a pre-trained component, which could be a pre-trained encoder or a pre-trained encoder-decoder model.
1. You will need to compare the performance of a seq-to-seq model trained from scratch with your model that includes a pre-trained component. You don’t need to train the model until convergence and can use an early checkpoint (200-300 iterations) to perform this comparison.
1. You should have a live demo of your model, i.e., a live interface where we would be able to enter input and view the output. You can use streamlit or gradio to create the demo.
1. Any extra features/ideas implemented (such as back-translation, new decoding methods, data augmentation, ensembling models, using model predictions in a non-standard way, …, ask TA for more ideas) are a big plus and would count for extra points.

**Tips**:
* Pay attention to your cloud credits. Not planning your compute utilization in advance or not tracking it can leave you without access to a cloud GPU (and DAN417 machines have a lot of issues). For example:
  * Do not spend 12 GPU hours verifying your HW5 works. Try to squeeze it into one or two hours.
  * If you are low on credits, plan accordingly and try to minimize the time you use the cloud. Test your code on your laptop before deploying it to the cloud.
* Ask questions if you are stuck. We expect you to make progress every week. If you are struggling with the same bug or facing the wall for a day, please seek help. Ask questions in #discussion or DM a TA. Arranging one-on-one meetings is also possible, but we have a limited capacity for that.

# Project Milestones

Every class starting next week will be split into two parts: lecture and final project work.
Each demonstration / document submission should be done on Tuesday during the final project work section of the class.
You should do this **in person**, zoom submissions are possible only given a sufficient justification and should be approved a day before the class.

1. **Apr 12:** Design document. A half-page summary of what you are planning to do. Google docs format with comments enabled. This document should contain
  * Who is working on the project (one or two people).
  * A link to a GitHub repository of the project.
  * Your dataset (or datasets) description i.e., task, language, size, source of the dataset.
  * What pre-trained model checkpoint you are planning to use, its architecture, its pre-training objective, language(s) it was pre-trained on.
  * How you are going to use this model for your task: do you need to add any extra layers / a new decoder.
  * The metric for model evaluation. It should be reasonable and well-suited for the task. For example, accuracy is not a good metric for machine translation. BLEU is better. At the same time, BLEU is not a good metric for summarization or code generation.
  * How you are planning to sample from your model at test time: greedy search, beam search, top-k sampling, etc.
1. **Apr 12 (same day as design document):** demonstrate that your HW5 works. I.e., you are able to train your model and achieve BLEU > 10 (an hour of training should be enough).
1. **Apr 19:** Demonstrate that your training script and model (with integrated pre-trained component) works. This means that
  * the data is pre-processed and batched correctly,
  * the training loop does not fail because of a bug and evaluation produces the metrics.
  * you don’t have to have a properly trained network at this point. Just make sure you can complete 10 training iterations and an evaluation. Showing that the model can perfectly fit 100 training examples (training accuracy > 99% without regularization) would be a great plus and can give you extra points for the final project.
1. **Apr 26:** Demonstrate that your model learns the task.
  * Your evaluation metrics should show significantly better performance than a random untrained model. And your model should outperform a model without a pre-trained component. At this point, you should have a trained checkpoint of the model that might perform suboptimally, but reasonably well. After that, you can focus on your presentation, writeup and demo code.
1. **May 5:** Final writeup is due.  A conference-style writeup of 4-6 pages that describes your problem, your model, your experiments and results, and what you have learned.  You should also have an appendix that describes the specific contributions of each person in your group.  
1. **After May 3:** Writeup submission. A 4-page conference paper-style writeup with introduction, related work, methods, and results sections. More details on that soon.

## You will be evaluated on:
* The quality of the presentation
  * The slides are simple, clear, and convey the information you want, they do not contain a lot of visual clutter
  * The presentation is well-rehearsed and intersting to watch
* The quality of the demo:
  * A nice Streamlit or Gradio demo is expected
  * A Jupyter or command-line demo is a big minus, but better than nothing
* The quality of the model:
  * Is it able to solve the task at all?
  * Does it perform better than the model without a pre-trained component?
  * How does it compare to the other models trained on this dataset?
* The quality of the codebase:
  * Does it contain README.md which explains a) what this project is about b) how to train the network and how to start the demo.
  * Contains up-to-date requirements.txt with all dependencies of your project. Every single thing you had to pip-install should be there.
  * Do README.md instructions actually work and we can run your code without errors.
  * Is it possible to run your code on a machine without a GPU?
  * Does your code follow PEP-8? Feel free to use auto-formatting tools such as Black.
* The quality of the writeup
  * Clarity of writing
  * Do you clearly define and motivate the problem you are solving?
  * Do you appropriately reference the relevant previous work, e.g. the relevant work for the extra features you implemented?
  * Are your methods, experimental setup, and results clearly described?
  * Do you have any insightful interpretations of your results and suggestions for future improvements?

# Writeup

You should submit a conference-style writeup of 4-6 pages. The writeup should be written in the style of a conference paper and should include:
1. An abstract, describing briefly what you have done and results you obtained [1 paragraph]
1. An introduction, a statement of the problem you are trying to address and a brief description of your solution.
1. Related work section (can be folded into the introduction), which should include brief references to related work mentioning relevant results and methods that your work draws on.
    1. Description of your methodology, including
    1. Machine learning methods, including an explanation of variables and formulas
    1. A figure that illustrates your method
    1. Data sets used 
    1. Experimental setup and evaluation methods.
1. Description of your results, including tables, comparisons with baselines, and figures if applicable.
1. A brief discussion of results, conclusions of your study, future directions if any. 

Approximate length: intro/related work (1.5 pages), methods/experimental setup (1.5-2 pages), results/conclusions (1-2 pages).

**IMPORTANT:** Please use the ACL conference style templates provided here: https://github.com/acl-org/acl-style-files

> this writeup should be in your project’s GitHub repository


# Recommended datasets
Before deciding to work on a dataset (milestone 1) make sure it’s not too large and fits on your disk.
You additionally need to analyze if the texts are not too large (>> 512 tokens).
If they are too big, you need to figure out how to trim it or not to work on the dataset at all.
If you really want to work with large texts, ask TA for tips (before milestone 1).
Note, that if the dataset is so large that one epoch takes more than some reasonable time
(wastes your cloud credits) and you are sure this is not a bug (e.g. GPU utilization is very close to 80-100%),
you can train for less than one epoch, given that the final model perfomance is reasonable.

### Translation
* https://huggingface.co/datasets/code_x_glue_tt_text_to_text

### Question answering
* https://huggingface.co/datasets/qasper

**Multilingual translation**

**a hard task, consult with a TA**

* https://huggingface.co/datasets/Helsinki-NLP/tatoeba_mt
* Feel free to find other translation datasets, but consult with a TA about them

### Summarization
* https://huggingface.co/datasets/cnn_dailymail
* https://huggingface.co/datasets/gigaword
* https://huggingface.co/datasets/orange_sum
* https://huggingface.co/datasets/ai4bharat/IndicSentenceSummarization
* https://huggingface.co/datasets/xsum
* https://huggingface.co/datasets/gem
* https://huggingface.co/datasets/reddit

**Long-document summarization**

**a hard task, consult with a TA**

* https://huggingface.co/datasets/ccdv/arxiv-summarization
* https://huggingface.co/datasets/ccdv/pubmed-summarization
* https://huggingface.co/datasets/ccdv/govreport-summarization

### Dialogue generation
* https://huggingface.co/datasets/conv_ai_2

### Code generation (or the opposite task of code explanation)
* https://huggingface.co/datasets/code_x_glue_tc_text_to_code

### Text to SQL (or SQL to text)
* https://huggingface.co/datasets/spider

### Math problems

**a very hard task, consult with a TA**

* https://huggingface.co/datasets/competition_math

# Suggestions for extra points
* Train your model on a TPU. You will need to learn PyTorch XLA and adapt your code to static shapes. Demonstrate stable TPU utilization >60%. One good thing about TPUs is that they are cheaper in terms of performance/$.
* Implement backtranslation (it can be used not just for translation, but for any seq2seq task) and demonstrate that it improves your model performance compared to a model that doesn't use backtranslation.
* Perform human evaluation of 100-200 generated examples and compute the correlation between your opinion and the automated metrics.
* Feel free to ask TA about any other ideas.
