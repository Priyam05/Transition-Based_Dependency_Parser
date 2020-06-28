# Transition-Based_Dependency_Parser
![Parser_Tree](/Images/parser.png)

**Files used**:
* train.projective.short.conll: training dataset containing 9,568 tokens.
* dev.projective.conll: dataset to evaluate parser’s performance

# Important Functions:
**is_projective**: The transition-based dependency parser we’ve been considering requires projective trees for training; before training the parser on a tree, we need to make sure the tree is projective. Recall from class and the textbook, “An arc from a head to a dependent is said to be projective if there is a path from the head to every word that lies between the head and the dependent in the sentence. A dependency tree is then said to be projective if all the arcs that make it up are projective.”

**perform_shift, perform_arc, tree_to_actions**: The parser relies on a classifier to decide the best action (SHIFT, LEFTARC or RIGHTARC) to take at each step, given the current state of the configuration. To train a classifier, we want to have training data in the form of (configuration, action) pairs.The raw inputs from the data files, however, are in the form of dependency trees—lists of (idd, tok, pos, head, lab) tuples.

On a high level, we are trying to create:
* X: list of configurations of the parser, which is determined by the states of the input buffer, stack and arcs.
* Y : list of actions for the parser (e.g. SHIFT, LEFTARC_nsubj)

**action_to_tree**: Now that we have a classifier, it’s time to evaluate the performance of the parser. Essentially we are trying to carry out the reverse steps of part 2—based on recommended actions (predictions) from the classifier, we want to generate a dependency tree for a sentence. It will update the dependency tree based on the action predictions.


