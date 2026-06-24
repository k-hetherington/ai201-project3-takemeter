# ai201-project3-takemeter
Evaluation Results

The fine-tuned DistilBERT model achieved a test accuracy of 32.4%.

Test Accuracy
Accuracy: 32.4%
Per-Class Performance
Label	Precision	Recall	F1
Analysis	0.33	1.00	0.50
Hot Take	0.25	0.09	0.13
Reaction	0.00	0.00	0.00
Question	0.00	0.00	0.00
Observations

The model performed best on the Analysis category and frequently predicted Analysis for examples belonging to other classes. The confusion matrix shows that Hot Take, Reaction, and Question comments were often misclassified as Analysis.

One likely explanation is that the label definitions overlap significantly. Many NBA discussion comments contain both opinions and reasoning, making it difficult to distinguish between Analysis, Hot Take, and Reaction. Additionally, the dataset contained only 243 examples, which limited the amount of training data available for each class.

Future improvements could include collecting more examples, refining the label definitions to reduce overlap, and balancing the dataset further across categories.

## Error Analysis

To better understand the model's performance, I reviewed several incorrect predictions from the test set.

### Example 1

**Text:** "Whichever one gets me paid more."

* **True Label:** Hot Take
* **Predicted Label:** Analysis

This comment was likely misclassified because it is very short and lacks strong opinion-related keywords. While a human reader can recognize it as expressing a personal preference, the model may have interpreted it as a general statement due to the lack of context.

### Example 2

**Text:** "I love OG, but the hell is he doing at 11th spot?"

* **True Label:** Question
* **Predicted Label:** Analysis

Although the comment is phrased as a question, it functions more as a rhetorical criticism of a player ranking. This highlights the overlap between the Question and Hot Take categories. The model appeared to focus on the basketball discussion content rather than the grammatical structure of the sentence.

### Example 3

**Text:** "Well we now have a new meme."

* **True Label:** Reaction
* **Predicted Label:** Analysis

This comment is primarily an emotional reaction and does not contain any reasoning or analysis. However, the model frequently predicted Analysis when it was uncertain. The confusion matrix shows that many Reaction examples were incorrectly classified as Analysis.

### Overall Observations

The model achieved a test accuracy of **32.4%**. While this is better than random guessing for a four-class problem (25%), the results show that the classifier struggled to distinguish between some categories.

Several factors likely contributed to the lower accuracy:

* Significant overlap between the **Reaction**, **Hot Take**, and **Analysis** labels.
* Many comments were extremely short and lacked enough context for reliable classification.
* Rhetorical questions often resembled opinions or reactions.
* The dataset contained only 243 examples, which limited the amount of training data available for each class.

The confusion matrix shows that the model heavily favored the **Analysis** label when uncertain. Future improvements could include collecting additional training examples, refining the label definitions to reduce overlap, or merging similar categories such as Reaction and Hot Take into a broader Opinion category.

## Baseline vs Fine-Tuned Model Comparison

Two models were evaluated on the same held-out test set:

| Model                                   | Accuracy |
| --------------------------------------- | -------: |
| Fine-Tuned DistilBERT                   |    32.4% |
| Groq Llama 3.3 70B (Zero-Shot Baseline) |    51.4% |

Surprisingly, the zero-shot Groq baseline significantly outperformed the fine-tuned DistilBERT model.

One likely explanation is that the dataset contained only 243 examples and several labels had substantial overlap. Categories such as Hot Take, Reaction, and Analysis often shared similar language patterns, making them difficult to separate using a small supervised dataset.

The large language model was able to use the label definitions and examples provided in the prompt to reason about the intended category, while the fine-tuned model struggled to learn clear decision boundaries from the limited training data.

This result demonstrates that modern instruction-tuned language models can sometimes outperform traditional fine-tuning approaches on small subjective classification tasks.
