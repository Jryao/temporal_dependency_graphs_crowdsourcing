# Annotating Temporal Dependency Graphs via Crowdsourcing

This repository contains the temporal dependency graph dataset.


## Data
The temporal dependency graph dataset is in `tdg_data/`. The train.txt contains 400 articles, dev.txt and test.txt both contain 50 articles.

Each article has three parts: file name, sentence list and edge list, seperated by `:SNT_LIST` and `EDGE_LIST`.

- The edge list has three parts: edges between timex and timex, edges between event and timex and edges between events and events. For example, in `dev.txt`, line 21-33 are the timex timex edges, line 34-56 are the event timex edges, and line 57-79 are the event event edges.

- Each edge has 4 fields, separated by tabs:
```
child    child_type    parent  relation
```
- child: the child node
- child_type: the child is a timex node or an event node
- parent: the parent node of this child
- relation: the temporal relation between the child and the parent

The child node and parent node are represented by their `sentence id, start token id in the sentence and end token id in the sentence`. For example, `0_0_3` means this node is in the first sentence of this document, its start token position in this sentence is 0, and its end token position in this sentence is 3. We use `-1_-1_-1` to represent the `ROOT` node.

Please note: some events do not have an event reference time, we add `-1_-1_-1` as a mate event reference time.


## Annotation Guidelines
You can find our annotation guidelines in `guidelines_and_example_questions/`, which are essentially our Amazon Mechanical Turk annotation interface. Some example questions are also included.


## Additional Resource
The `generic_event.whitelist.wn-fn.variants` file contains a list of common event trigger words. We use this list to extract possible events in the 3rd pass annotation.