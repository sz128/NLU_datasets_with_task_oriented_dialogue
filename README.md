# NLU and DST datasets

Datasets of natural language understanding and dialogue state tracking, which can be used in research.

### Content

- ##### [Introduction](#intro)
- ##### [Datasets in single turn](#single_turn)
- ##### [Datasets with multiple turns](#multi_turns)

## <a name="intro"></a>Introduction

|  Items | description | example | 
|:--------:|:--------:|:--------:|
| NLU | Natural Language Understanding, which should contains text classification, sequence labelling and semantic parsing tasks. | |
| DST | Dialogue State Tracking | |
| intent | It an abstract meaning which always refers to a sentence or sub-sentence. | The intent of "show me a movie named Titanic" is "find_movie" |
| slot | It is attribute or key, which should have a value. | "show me a movie named Titanic" has a slot-value pair "movie_name = Titanic" |
| act type | a general speech action | inform, deny, confirm, request, ... |
| dialogue act | a triple of (act_type, slot, value), http://camdial.org/~mh521/dstc/downloads/handbook.pdf | inform(movie_name = Titanic), request(price), ... |


## <a name="single_turn"></a>Datasets in single turn (not a dialogue)

|  dataset | single turn or multi-turns | tasks | url |
|:--------:|:--------:|:--------:|:--------:|
| ATIS | single | Intent classification, slot tagging | https://github.com/yvchen/JointSLU |
| MIT corpus | single | slot tagging | https://groups.csail.mit.edu/sls/downloads/ |
| SNIPS | single | slot tagging | https://github.com/snipsco/nlu-benchmark/tree/master/2017-06-custom-intent-engines |
| TOP semanitc parsing | single | Tree parsing (hierarchical intent + slots) | http://fb.me/semanticparsingdialog, https://arxiv.org/abs/1810.07942 |

## <a name="multi_turns"></a>Datasets with multiple turns (dialogue with context)

|  dataset | single turn or multi-turns | NLU/DST tasks | url |
|:--------:|:--------:|:--------:|:--------:|
| DSTC 2&3 | multiple | NLU (dialogue act), DST (slot-value pairs) | http://camdial.org/~mh521/dstc/ |
| DSTC 4 | multiple | NLU (slots), DST (slot-value pairs) | http://www.colips.org/workshop/dstc4/ |
| Sim-R/Sim-M/Sim-gen | multiple | NLU (intent + slots + dialogue act), DST (slot-value pairs) | https://github.com/google-research-datasets/simulated-dialogue |
| MultiWOZ 1.0/2.0 | multiple | DST (slot-value pairs) | http://dialogue.mi.eng.cam.ac.uk/index.php/corpus/ |
| Frames | multiple | NLU (intent + slots + dialogue act), DST (slot-value pairs) | https://datasets.maluuba.com/Frames/dl |
| Microsoft Dialogue Challenge | multiple | NLU (dialogue act) | https://github.com/xiul-msr/e2e_dialog_challenge |
