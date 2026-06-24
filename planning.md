# Project 3 Planning: TakeMeter

## Community Choice

I chose NBA discussion communities, primarily r/nba and r/NBATalk, because they contain a wide variety of discussion styles. Users frequently post statistical analysis, player rankings, reactions to news, predictions, memes, and discussion questions.

This makes NBA Reddit a good fit for a classification task because comments often have different intentions even when discussing the same topic. The challenge of distinguishing between analysis, opinions, reactions, and questions creates an interesting machine learning problem.

---

## Label Taxonomy

### Analysis

Comments that explain an idea using reasoning, evidence, statistics, comparisons, strategy, or context.

Examples:

* "Towns at 8 when he averaged 15/10 in the playoffs and had a subpar finals is ridiculous."
* "The Knicks have better wing defenders than the Spurs which could create matchup problems."

### Hot Take

Comments that express a strong opinion, prediction, ranking, or claim without substantial supporting evidence.

Examples:

* "Jokic, SGA, Wemby, Luka, and Giannis are the top five. Any other list is wrong."
* "The Spurs just lost the series with this choke."

### Reaction

Comments that primarily express emotion, surprise, humor, frustration, agreement, or disagreement.

Examples:

* "No way dude."
* "Well we now have a new meme."

### Question

Comments whose primary purpose is to request information, clarification, opinions, or discussion.

Examples:

* "Who is the face of basketball right now?"
* "What are the greatest NBA games of all time?"

---

## Hardest Anticipated Edge Case

The most difficult edge case will likely be distinguishing between Hot Take and Reaction.

For example:

* "Brunson at 2 lol"
* "This list is terrible"

These comments express opinions but are also emotional reactions. My approach will be to identify the primary intent of the comment. If the comment mainly expresses an opinion or judgment, it will be labeled Hot Take. If it mainly expresses emotion or surprise, it will be labeled Reaction.

Another difficult case will be rhetorical questions that function as opinions rather than genuine requests for information.

---

## Data Collection Plan

I will collect NBA-related comments from public Reddit discussions in r/nba and r/NBATalk.

My goal is to create a dataset of at least 200 labeled examples distributed across all categories. I will manually review each comment and assign a label based on the primary purpose of the comment.

To reduce class imbalance, I will intentionally search for threads that contain a mix of analysis, reactions, opinions, and questions.

---

## Evaluation Plan

I will split the dataset into training, validation, and test sets.

Performance will be measured using:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

Accuracy will provide an overall performance measure, while per-class metrics and the confusion matrix will help identify which labels the model confuses most often.

I will also compare the fine-tuned classifier against a zero-shot large language model baseline.

---

## Definition of Good Enough Performance

I would consider the model successful if it achieves:

* At least 50% overall accuracy
* Reasonable performance across all four labels
* No label with an F1 score below 0.30

Because the task involves subjective labels with overlapping meanings, I do not expect perfect performance. My primary goal is to determine whether the model can distinguish broad discussion styles better than random guessing.

---

## AI Tool Plan

I plan to use AI tools in the following ways:

1. Label Stress Testing

   * Ask an LLM to classify sample comments and compare its decisions with my own labels.

2. Annotation Assistance

   * Use AI to help identify potential examples from NBA discussion threads while manually reviewing and correcting labels.

3. Failure Pattern Analysis

   * Use AI to help analyze misclassifications and identify common error patterns after training.

All final labeling decisions will be reviewed manually.

