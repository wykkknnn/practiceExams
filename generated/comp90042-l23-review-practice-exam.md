# COMP90042 NLP Practice Exam

Generated with the `practice-exams` skill from `l23-review-part1-v1.pdf`.

## Exam Assumptions

- Format: on-campus, closed book.
- Allowed aid: non-programmable calculator.
- Writing time: 120 minutes, plus 15 minutes reading time.
- Total: 120 marks.
- Structure follows the lecture review: Part A short answer, Part B method questions, Part C algorithm questions.
- Scope is limited to topics visible in the supplied review slides, so this is a practice paper rather than a full-semester guarantee.

## Coverage Blueprint

| Area | Marks | Main skills tested |
|---|---:|---|
| Preprocessing and tokenisation | 10 | Definitions, design choices, examples |
| N-gram language models | 20 | Derivation, smoothing, interpolation |
| Text classification | 15 | Model comparison, bias-variance, feature design |
| POS tagging and HMMs | 25 | Tagging models, emissions/transitions, Viterbi |
| Neural networks for NLP | 20 | FFN/RNN/LSTM design and interpretation |
| Transformers and pretrained models | 20 | Attention, model architecture, GPT/BERT/T5 |
| Word embeddings | 10 | Distributional matrices, PMI/PPMI, evaluation |

## Part A: Short Answer Questions

Answer each in 2-3 sentences. Each question is worth 3 marks.

1. Explain the difference between sentence segmentation and tokenisation. Give one example where tokenisation is not straightforward.
2. What is the difference between derivational and inflectional morphology, and why might the distinction matter for word normalisation?
3. Contrast lemmatisation and stemming. Give one advantage and one disadvantage of each.
4. In an n-gram language model, what independence assumption is being made?
5. Why is smoothing necessary in n-gram language modelling?
6. What is the purpose of interpolation in language modelling?
7. Give two examples of text classification tasks and explain what the input and output are in each.
8. Explain the bias-variance trade-off in the context of text classification.
9. What is the difference between open-class and closed-class POS categories?
10. In an HMM POS tagger, what do emission probabilities and transition probabilities represent?
11. Why are word embeddings useful compared with one-hot word representations?
12. What is the main architectural difference between GPT and BERT?

Total: 36 marks.

## Part B: Method Questions

Answer all questions. Show reasoning clearly.

### B1. Preprocessing Pipeline Design

You are building a sentiment classifier for short social media posts. Describe a preprocessing pipeline that includes sentence segmentation, tokenisation, subword handling, word normalisation, and stop word handling. For each step, explain one design choice and one possible risk.

Marks: 12. Estimated time: 12 minutes. Difficulty: medium.

### B2. Smoothing Methods

Compare add-k smoothing, absolute discounting, Katz backoff, Kneser-Ney smoothing, and interpolation. Your answer should explain the core motivation of each method and identify one situation where a more sophisticated method is preferable to add-k smoothing.

Marks: 16. Estimated time: 16 minutes. Difficulty: hard.

### B3. Classifier Choice

A course wants to classify student discussion posts by topic. Compare Naive Bayes, logistic regression, SVM, kNN, and a neural network for this task. Discuss assumptions, data requirements, interpretability, and likely bias-variance behaviour.

Marks: 16. Estimated time: 16 minutes. Difficulty: hard.

### B4. Pretrained Model Selection

For each task below, choose GPT, BERT, or T5 and justify your choice: sentiment classification, open-ended story generation, and rewriting a sentence into a simpler form. Include one limitation or risk for each selected model.

Marks: 16. Estimated time: 16 minutes. Difficulty: medium.

Total: 60 marks.

## Part C: Algorithm Questions

Answer both questions. Show calculations or algorithm steps.

### C1. N-gram Probability and Interpolation

Suppose a corpus gives the following counts:

- `count(the cat) = 8`, `count(the) = 20`
- `count(cat sat) = 3`, `count(cat) = 10`
- `count(sat down) = 1`, `count(sat) = 5`
- unigram probabilities: `P(cat)=0.04`, `P(sat)=0.02`, `P(down)=0.01`

Estimate the interpolated probability of `the cat sat down` using bigram and unigram models with `lambda_bigram = 0.7` and `lambda_unigram = 0.3`. Use:

`P(w_i | w_{i-1}) = 0.7 * P_bigram(w_i | w_{i-1}) + 0.3 * P_unigram(w_i)`

Marks: 12. Estimated time: 12 minutes. Difficulty: medium.

### C2. One Viterbi Step

Consider a tiny HMM POS tagger with tags `N` and `V`. For the sentence `fish swim`, use the following values:

- Initial probabilities: `P(N)=0.6`, `P(V)=0.4`
- Emissions: `P(fish|N)=0.5`, `P(fish|V)=0.2`, `P(swim|N)=0.1`, `P(swim|V)=0.6`
- Transitions: `P(N|N)=0.3`, `P(V|N)=0.7`, `P(N|V)=0.4`, `P(V|V)=0.6`

Run Viterbi for the two words and give the most likely tag sequence with its probability.

Marks: 12. Estimated time: 12 minutes. Difficulty: medium.

Total: 24 marks.

## Answer Key And Marking Rubric

### Part A Rubric

Award up to 3 marks per question:

- 1 mark for accurate definition or core concept.
- 1 mark for correct contrast, motivation, or implication.
- 1 mark for a relevant example or precise NLP context.

Expected points:

1. Sentence segmentation splits text into sentences; tokenisation splits sentences into units such as words, punctuation, or subwords. Difficult cases include abbreviations, contractions, URLs, hashtags, or languages without whitespace.
2. Inflection changes grammatical form without changing core lexical category; derivation can create a new word or category. This affects whether normalisation should collapse forms.
3. Lemmatisation maps to dictionary forms using linguistic analysis; stemming strips affixes heuristically. Lemmatisation is cleaner but costlier; stemming is simple but can over- or under-normalise.
4. The next word is assumed to depend only on the previous `n-1` words, not the full history.
5. Smoothing avoids zero probability for unseen n-grams and redistributes probability mass.
6. Interpolation combines estimates from multiple n-gram orders to balance specificity and robustness.
7. Examples include topic classification, sentiment analysis, and native language identification.
8. High-bias models may underfit; high-variance models may overfit, especially with sparse text features.
9. Open classes admit new words, such as nouns and verbs; closed classes are more fixed, such as prepositions and determiners.
10. Emissions model word likelihood given a tag; transitions model tag sequence likelihood.
11. Embeddings are dense vectors that encode similarity and distributional information.
12. GPT is decoder-only and suited to generation; BERT is encoder-only and trained with masked language modelling for contextual representation.

### Part B Rubric

B1:

- 2 marks for a coherent pipeline.
- 2 marks for sentence segmentation/tokenisation issues.
- 2 marks for subword tokenisation motivation.
- 2 marks for normalisation choices.
- 2 marks for stop word discussion.
- 2 marks for risks such as losing negation, domain terms, emojis, or morphology.

B2:

- 3 marks for add-k.
- 3 marks for absolute discounting.
- 3 marks for Katz backoff.
- 3 marks for Kneser-Ney.
- 2 marks for interpolation.
- 2 marks for a justified comparison and example.

B3:

- 3 marks for Naive Bayes.
- 3 marks for logistic regression.
- 3 marks for SVM.
- 3 marks for kNN.
- 3 marks for neural networks.
- 1 mark for an integrated bias-variance/data/interpretability comparison.

B4:

- 4 marks for BERT on sentiment classification: encoder representations, classification head, limitation.
- 4 marks for GPT on story generation: decoder autoregressive generation, limitation.
- 4 marks for T5 on sentence rewriting: encoder-decoder text-to-text framing, limitation.
- 4 marks for clear task-model matching and pros/cons.

### Part C Worked Solutions

C1:

- `P(cat|the) = 8/20 = 0.4`; interpolated = `0.7*0.4 + 0.3*0.04 = 0.292`.
- `P(sat|cat) = 3/10 = 0.3`; interpolated = `0.7*0.3 + 0.3*0.02 = 0.216`.
- `P(down|sat) = 1/5 = 0.2`; interpolated = `0.7*0.2 + 0.3*0.01 = 0.143`.
- Sequence probability, ignoring the first-word prior for `the`, is `0.292 * 0.216 * 0.143 = 0.009018816`.
- Award marks for formula, each conditional probability, each interpolation, and final multiplication.

C2:

- Step 1 for `fish`: `N = 0.6*0.5 = 0.30`; `V = 0.4*0.2 = 0.08`.
- Step 2 for `swim` ending in `N`: max of `0.30*0.3*0.1 = 0.009` and `0.08*0.4*0.1 = 0.0032`, so previous tag is `N`.
- Step 2 ending in `V`: max of `0.30*0.7*0.6 = 0.126` and `0.08*0.6*0.6 = 0.0288`, so previous tag is `N`.
- Best final path is `N V` with probability `0.126`.
- Award marks for initialization, recursion, backpointers, final sequence, and probability.

## Revision Diagnostics

Heavily tested areas: n-gram smoothing, HMM/POS tagging, classifier comparison, and neural/pretrained model architecture.

Skills to practise:

- Explaining why a modelling choice is suitable for a task.
- Doing small numerical probability calculations cleanly.
- Comparing related methods without only listing definitions.
- Connecting architecture to NLP task type.

Common mistakes:

- Confusing stemming with lemmatisation.
- Treating all smoothing methods as interchangeable.
- Forgetting the difference between HMM emissions and transitions.
- Saying GPT and BERT are both "transformers" without explaining decoder-only vs encoder-only use.
- Giving model names without task-specific justification.
