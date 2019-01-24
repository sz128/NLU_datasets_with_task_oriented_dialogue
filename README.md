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
| domain | dialogue domain | movie, music, flight, restaurant, ... |
| intent | It an abstract meaning which always refers to a sentence or sub-sentence. | The intent of "show me a movie named Titanic" is "find_movie" |
| slot | It is attribute or key, which should have a value. | "show me a movie named Titanic" has a slot-value pair "movie_name = Titanic" |
| act type | a general speech action | inform, deny, confirm, request, ... |
| dialogue act | act_type(slot=value,...), http://camdial.org/~mh521/dstc/downloads/handbook.pdf | inform(movie_name = Titanic), request(price), ... |

 * Intent Detection or intent classification: sentence classification task
 * Slot Tagging: sequence labelling task
 * Slot Filling: It equals to slot tagging if all values of slots can be aligned into input sentence. Otherwise, the value of slot should be predicted in a classification or generation way.


## <a name="single_turn"></a>Datasets in single turn (not a dialogue)

|  dataset | semantic annotation | tasks | url |
|:--------:|:--------:|:--------:|:--------:|
| ATIS | intent, slot | Intent classification, slot tagging | https://github.com/yvchen/JointSLU |
| MIT corpus | slot | slot tagging | https://groups.csail.mit.edu/sls/downloads/ |
| SNIPS | slot | slot tagging | https://github.com/snipsco/nlu-benchmark/tree/master/2017-06-custom-intent-engines |
| TOP semanitc parsing | hierarchical intent, slot | constituency parsing  | http://fb.me/semanticparsingdialog, https://arxiv.org/abs/1810.07942 |

## <a name="multi_turns"></a>Datasets with multiple turns (dialogue with context)

|  dataset | semantic annotation | NLU/DST tasks | url |
|:--------:|:--------:|:--------:|:--------:|
| DSTC 2&3 | dialogue act | NLU (slot filling), DST (slot-value pairs) | http://camdial.org/~mh521/dstc/ |
| DSTC 4 | speech action, slot | NLU (slot tagging), DST (slot-value pairs) | http://www.colips.org/workshop/dstc4/ |
| Sim-R/Sim-M/Sim-gen | act type, slot | NLU (slot tagging), DST (slot-value pairs) | https://github.com/google-research-datasets/simulated-dialogue |
| MultiWOZ 1.0/2.0 | multiple | DST (slot-value pairs) | http://dialogue.mi.eng.cam.ac.uk/index.php/corpus/ |
| Frames | intent, dialogue act | NLU (intent classification, slot tagging), DST (slot-value pairs) | https://datasets.maluuba.com/Frames/dl |
| Microsoft Dialogue Challenge | dialogue act | NLU (slot tagging) | https://github.com/xiul-msr/e2e_dialog_challenge |
