I chose to work with BERT because its transformer architecture is well-suited for natural language processing tasks. My goal was that, given a pair of sentence that has one as grammatically correct and the other a grammatically incorrect version with minor changes (like typos, switched words/letters) to identify the correct one by leveraging the contextual understanding capabilities of these models. Along the way, I explored different strategies, from training models from scratch to leveraging transfer learning, to find the most effective approach for this classification problem.

**Files Description**

Go to Demo.ipynb to see demonstration of model making sentence predictions, confidence scores, etc.. Note that the final accuracy will be higher than tested because the final test involves giving the model exactly one correct sentence and one incorrect sentence. In cases where the model predicts both sentence as either correct or incorrect, it can use confidence scores to make a better judgement.

This repository does not contain all my code. Some files, especially model weights, training data, and logs were too large for me to upload. I'm happy to send it by email.

**Process**

Initial Approach: Training and writing BERT from Scratch

I started by implementing a BERT model for Masked Language Modeling (MLM) from scratch.
The idea was to train the MLM on correct sentences to learn the contextual relationships between words and then fine-tune the model with correct and incorrect sentences for classification.

Challenge: This approach had an excessively long training time.

Iteration 1: Untrained DistilBERT
I shifted to using DistilBERT, a smaller variant of BERT, initialized with random weights for sequence classification.
Outcome: While this reduced the training time, the model achieved only ~60% validation accuracy, far below the ~80% achieved with pretrained models.

Iteration 2: Transfer learning
I used the model weights from the sequence classification training, trained it on MLM tasks, and then trained it on sequence classification tasks again. The model finally achieved a perplexity below 10 and an MLM loss of 2.9, indicating strong contextual learning. Some other thoughts/challenges I had were:

- Whether to freeze layers: I decided in the end not to because DistilBERT only has 6 layers.

Results:
Validation accuracy improved to ~75% after training on one-third of the dataset.
Training on the entire dataset further increased accuracy to ~80%.
