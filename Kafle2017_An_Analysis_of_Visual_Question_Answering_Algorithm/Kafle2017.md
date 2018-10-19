# Introduction

## Visual Question Answering

![Examples from VQA 2.0](images/vqa_examples.jpg)

## SOTA

- VQA research began in late 2014 with DAQUAR
- 4 other datasets
- VQA, the most popular
- last algorithms approach 70\% accuracy VS human performance is 83\%

## Problems

- multiple kinds of biases not taken in count
    - existing tasks (dataset+metric) do not group questions into meaningful categories
- not easy to compare the abilities of individual algorithms
    - ex: one method excel at color questions, bad at spatial reasoning. an other method excel at spatial reasoning. color questions are far more common


## Contribution

1. New VQA real image dataset where question are divided into 12 categories
2. New evaluation metrics that compensate for bias
3. Assess whether a balanced distribution can help algorithms learn better
4. Novel absurd questions category

# TDIUC Dataset

## Examples

![Examples from TDIUC](images/tdiuc_examples.png)

## Nuanced VQA Analysis

1. Object Presence (e.g., ‘Is there a cat in the image?’)
2. Subordinate Object Recognition (e.g., ‘What kind of
furniture is in the picture?’)
3. Counting (e.g., ’How many horses are there?’)
4. Color Attributes (e.g., ‘What color is the man’s tie?’)
5. Other Attributes (e.g., ‘What shape is the clock?’)
6. Activity Recognition (e.g., ‘What is the girl doing?’)
7. Sport Recognition (e.g.,‘What are they playing?’)
8. Positional Reasoning (e.g., ‘What is to the left of the
man on the sofa?’)
9. Scene Classification (e.g., ‘What room is this?’)
10. Sentiment Understanding (e.g.,‘How is she feeling?’)
11. Object Utilities and Affordances (e.g.,‘What object
can be used to break glass?’)
12. Absurd (i.e., Nonsensical queries about the image)

![Number of questions per type](images/questions_type.png)

## Creating the dataset

- Importing questions from COCO-VQA and Visual Genome
- Generating questions using image annotations
    - using COCO annotations
    - using Visual Genome annotations
- Manual Annotation
- Post processing

## Proposed Evaluation Metric

- Arithmetic mean-per-type (MPT)
- Harmonic MPT
- Arithmetic Normalized-MPT
- Harmonic N-MPT

Normalize: compute the accuracy for each unique answer separately within a question-type and then average them together for the question-type

# Experiments

## Models

- YES: Predicts ‘yes’ for all questions.
- REP: Predicts the most repeated answer in a questiontype
category using an oracle.
- QUES: A linear softmax classifier given only question
features (image blind).
- IMG: A linear softmax classifier given only image features
(question blind).
- Q+I: A linear classifier given the question and image..
- MLP: A 4-layer MLP fed question and image features.
- MCB: MCB [5] without spatial attention.
- MCB-A: MCB [5] with spatial attention.
- NMN: NMN from [1] with minor modifications.
- RAU: RAU [23] with minor modifications.

## All Results

![](images/all_models.png)

## Easy Question-Types

- > /90% under MPT: 
    - scene recognition
    - sport recognition
    - object presence
    - absurd

## Effects of Proposed Metrics

- MLP better than MCB and NMT on simple accuracy, but bad on MPT
- RAU better than MCB-A on simple accuracy, but bad on MPT
- Comparing unnormalized and normalized metrics can help us determine the generalization capacity

## Can Algorithms Predict Rare Answers?

- Create subset of TDIUC (TDIUC-Tail) consists of questions with answers repated less than 1000 times.
- Train MCB on 1) full TDIUC, 2) TDIUC-Tail
- Evaluate on TDIUC-Tail
- 2) better than 1) shows MCB capacity to learn to correctly predict rarer answers, but simple biased towards common answers to maximize overall accuracy

## Effects of Including Absurd Questions

- Good absurd performance is achieved by sacrificing performance on other categories.
- MCB better to discriminate between absurd and real questions than Q+I

## Effects of Balancing Object Presence

- COCO-VQA biased towards yes answers on object presence questions
- TDIUC contains 50\% yes and 50\% no
- MCB-A performed poorly by learning the biases in the COCO-VQA dataset, but it is capable of performing well when the dataset is unbiased.

## Advantages of Attentive Models

- MCB versus MCB-A
- Most pronounced increases are for:
    - color recognition
    - attribute recognition
    - absurd
    - counting
- All of these require to detect specified object (or lack of)
- The attention mechanism learns the relative importance of these features

## Compositional and Modular Approaches

- NMT perform better than MLP using MPT and N-MPT, but not so much.
- NMT seems limited bu the quality of the S-expression parser
- RAU can learn to solve different tasks over multiple hops (does not need to rely on rigid questions parses)
- RAU showes very good perf on absurd questions and on other categories
