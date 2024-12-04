This project explores the use of BERT and DistilBERT models for sentence classification, focusing on distinguishing grammatically correct sentences from incorrect ones. The project highlights the challenges, iterations, and lessons learned while experimenting with different approaches to tackle the task effectively.

I chose to work with BERT because its transformer architecture is well-suited for natural language processing tasks. My goal was to classify sentences as correct or incorrect by leveraging the contextual understanding capabilities of these models. Along the way, I explored different strategies, from training models from scratch to leveraging transfer learning, to find the most effective approach for this classification problem.

**Process**
Initial Approach: Training BERT from Scratch
I started by implementing a BERT model for Masked Language Modeling (MLM) from scratch. The idea was to:
Train the MLM on correct sentences to learn the contextual relationships between words.
Fine-tune the model with correct and incorrect sentences for classification.
Challenge: This approach had an excessively long training time and didn’t align with the problem's simpler classification requirements.
Iteration 1: Untrained DistilBERT
I shifted to using DistilBERT, a smaller variant of BERT, initialized with random weights for sequence classification.
Outcome: While this reduced the training time, the model achieved only ~60% validation accuracy, far below the ~80% achieved with pretrained models.
Iteration 2: Fine-Tuning an MLM-Based DistilBERT
Realizing the importance of transfer learning, I trained DistilBERT for Masked Language Modeling:
Achieved a perplexity below 10 and an MLM loss of 2.9, indicating strong contextual learning.
Transferred the MLM weights to a sequence classification model.
Results:
Validation accuracy improved to ~75% after training on one-third of the dataset.
Training on the entire dataset further increased accuracy to ~80%.
