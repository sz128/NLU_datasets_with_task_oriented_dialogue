# NLU datasets for task-oriented dialogue

Datasets of natural language understanding and dialogue state tracking for task-oriented dialogue, which can be used in research. There are some other survey of datasets in respective of diaogue system, like [AtmaHou's Task-Oriented-Dialogue-Dataset-Survey](https://github.com/AtmaHou/Task-Oriented-Dialogue-Dataset-Survey) (I am one of the contributors). But we focus on how to build a semantic parser for spoken dialogue system.

If you want to know more about NLU of task-oriented dialogue, please see [recommended papers](https://github.com/sz128/Natural-language-understanding-papers).

## Table of Contents

- #### [Introduction](#intro)
- #### [Datasets with single turn](#single_turn)
- #### [Datasets with multiple turns](#multi_turns)
- #### [Details](#details)

## <a name="intro"></a>Introduction

|  Items | description | example | 
|:--------:|:--------:|:--------:|
| NLU | Natural Language Understanding, which should contains text classification, sequence labelling and semantic parsing tasks. | |
| DST | Dialogue State Tracking | [DSTC 2](http://camdial.org/~mh521/dstc/downloads/handbook.pdf) |
| domain | dialogue domain | movie, music, flight, restaurant, ... |
| intent | It an abstract meaning which always refers to a sentence or sub-sentence. | The intent of "*show me a movie named Titanic*" is "*find_movie*" |
| slot | It is attribute or key, which should have a value. | "*show me a movie named Titanic*" has a slot-value pair "*movie_name = Titanic*" |
| act type | a general speech action | *inform, deny, confirm, request, hello, bye,* ... |
| dialogue act | act_type(slot=value,...), http://camdial.org/~mh521/dstc/downloads/handbook.pdf | *inform(movie_name = Titanic), request(price),* ... |

 * **Intent Detection or intent classification**: sentence classification task
 * **Slot Tagging**: sequence labelling task
 * **Slot Filling**: It equals to slot tagging if all values of slots can be aligned into input sentence. Otherwise, the value of slot should be predicted in a classification or generation way.


## <a name="single_turn"></a>Datasets with single turn (not a dialogue)

|  dataset | semantic annotation | tasks | url |
|:--------:|:--------:|:--------:|:--------:|
| [ATIS](#atis) | intent, slot | Intent classification, slot tagging | https://github.com/yvchen/JointSLU |
| [MIT corpus](#mit_corpus) | slot | slot tagging | https://groups.csail.mit.edu/sls/downloads/ |
| [SNIPS](#snips) | slot | slot tagging | https://github.com/snipsco/nlu-benchmark/tree/master/2017-06-custom-intent-engines |
| [facebook TOP semantic parsing](#top_semantic_parsing) | hierarchical intent, slot | constituency parsing  | http://fb.me/semanticparsingdialog, https://arxiv.org/abs/1810.07942 |
| [SMP2017-ECDT](#smp2017_ecdt) (in Chinese) | intent | Intent classification | http://ir.hit.edu.cn/SMP2017-ECDT, https://github.com/HITlilingzhi/SMP2017ECDT-DATA |

## <a name="multi_turns"></a>Datasets with multiple turns (dialogue with context)

|  dataset | semantic annotation | NLU/DST tasks | url |
|:--------:|:--------:|:--------:|:--------:|
| [cam DSTC 2&3](#dstc_23) | dialogue act | NLU (slot filling), DST (slot-value pairs) | http://camdial.org/~mh521/dstc/ |
| [DSTC 4](#dstc_4) | speech action, slot | NLU (slot tagging), DST (slot-value pairs) | (challenge participants only) http://www.colips.org/workshop/dstc4/ |
| [google Sim-R/Sim-M/Sim-gen](#google_simulated_dialogue) | act type, slot | NLU (slot tagging), DST (slot-value pairs) | https://github.com/google-research-datasets/simulated-dialogue |
| [cam MultiWOZ 1.0/2.0](#cam_multiwoz_12) | multiple | DST (slot-value pairs) | http://dialogue.mi.eng.cam.ac.uk/index.php/corpus/ |
| [maluuba Frames](#maluuba_frames) | intent, dialogue act | NLU (intent classification, slot tagging), DST (slot-value pairs) | https://datasets.maluuba.com/Frames/dl |
| [Microsoft Dialogue Challenge](#msr_dc) | dialogue act | NLU (slot tagging) | https://github.com/xiul-msr/e2e_dialog_challenge |

## <a name="details"></a>Details

More information about each dataset.
 
### <a name="atis"></a>ATIS
 * single turn;
 * input sentences: natural language;
 * data size (single domain of "flight information searching"):
   * training set: 4978 utterances;
   * test set: 893 utterances;
 * semantic annotation: intent (sentence class), slot (sequence labelling)
   * intent number: 18
   * slot number: 83
 * Download: https://github.com/yvchen/JointSLU

### <a name="mit_corpus"></a>MIT corpus
 * single turn;
 * input sentences: natural language;
 * data size:
   * MIT_Restaurant domain:
     * training set: 7660 utterances;
     * test set: 1521 utterances;
   * MIT_Movie domain (simple query):
     * training set: 9775 utterances;
     * test set: 2443 utterances;
   * MIT_Movie domain (complex query):
     * training set: 7816 utterances;
     * test set: 1953 utterances;
 * semantic annotation: slot (sequence labelling)
 * Download: https://groups.csail.mit.edu/sls/downloads
 
 ### <a name="snips"></a>SNIPS
 * single turn;
 * input sentences: natural language;
 * data size:
   * 7 intents: each has more than 2000 queries.
 * semantic annotation: intent (sentence class), slot (sequence labelling)
 * Download: https://github.com/snipsco/nlu-benchmark/tree/master/2017-06-custom-intent-engines
 
 ### <a name="top_semantic_parsing"></a>TOP semantic parsing
 * single turn;
 * input sentences: natural language;
 * data size: 
   * training set: 35741 queries
   * test set: 9042 queries
 * semantic annotation: hierarchical intents, slot  (it is a tree)
   * intent number: 25
   * slot number: 36
 * Download: http://fb.me/semanticparsingdialog

 ### <a name="smp2017_ecdt"></a>SMP2017-ECDT (in Chinese) 
 * single turn;
 * input sentences: natural language;
 * data size: 
   * http://ir.hit.edu.cn/SMP2017-ECDT
   * training set: 2299 queries
   * development set: 770 queries
   * test set: 666 queries
 * semantic annotation: intent
   * intent number: 31
 * Download: https://github.com/HITlilingzhi/SMP2017ECDT-DATA
 
 ### <a name="dstc_23"></a>DSTC 2&3
 * multiple turns: human-machine dialogues;
 * input sentences: 
   * transcription by human;
   * ASR output: n-best, word confusion network;
 * data size: 
   * DSTC 2 (Restaurant Information Domain): source domain
     * training set: about 2k dialogues;
     * test set: about 1k dialogues;
   * DSTC 3 (Tourist Information Domain): extented domain
     * seed data: about 10 dialogues;
     * test set: about 2k dialogues;
 * semantic annotation: dialogue act
   * DSTC 2: 8 slots;
   * DSTC 3: 13 slots;
 * Download: http://camdial.org/~mh521/dstc/

 ### <a name="dstc_4"></a>DSTC 4
 * multiple turns: human-human dialogues;
 * input sentences: natural language, transcription by human;
 * data size: 
   *  This data is about touristic information for Singapore collected from Skype calls.
   *  35 dialogs sum up to 31,034 utterances and 273,580 words
 * semantic annotation: speech action, slot, dialogue state (slot-value pairs) in sub-dialogue level
 * Download: challenge participants only, http://www.colips.org/workshop/dstc4/
 
 ### <a name="google_simulated_dialogue"></a>google Sim-R/Sim-M/Sim-gen
 * multiple turns: conversations between an agent and a simulated user;
 * input sentences: natural language;
 * data size: 
 
| Dataset            | Slots                                                                          | Train | Dev | Test |
| ------------------ | ------------------------------------------------------------------------------ | ----- | --- | ---- |
| Sim-R (Restaurant) | price\_range, location, restaurant\_name,<br>category, num\_people, date, time | 1116  | 349 | 775  |
| Sim-M (Movie)      | theatre\_name, movie, date, time,<br>num\_people                               | 384   | 120 | 264  |
| Sim-GEN (Movie)    | theatre\_name, movie, date, time,<br>num\_people                               | 100K  | 10K | 10K  |

 * semantic annotation: slot
 * Download: https://github.com/google-research-datasets/simulated-dialogue
 
 ### <a name="cam_multiwoz_12"></a>cam MultiWOZ 1.0/2.0
 * multiple turns: human-human dialogues collected in the way of WOZ (Wizard-of-Oz);
 * input sentences: natural language;
 * data size: There are 3,406 single-domain dialogues that include booking if the domain allows for that and 7,032 multi-domain dialogues consisting of at least 2 up to 5 domains.
 * semantic annotation: dialogue state (slot-value pairs)
 * Download: http://dialogue.mi.eng.cam.ac.uk/index.php/corpus/

 ### <a name="maluuba_frames"></a>maluuba Frames
 * multiple turns: human-human dialogues collected in the way of WOZ (Wizard-of-Oz);
 * input sentences: natural language;
 * data size: 
   * It is about travel.
   * 1369 dialogues, 19986 turns;
   * http://www.aclweb.org/anthology/W17-5526
 * semantic annotation: intent, dialogue act
 * tasks: NLU (intent classification, slot tagging), DST (slot-value pairs)
 * Download: https://datasets.maluuba.com/Frames/dl
 
 ### <a name="msr_dc"></a>Microsoft Dialogue Challenge
 * multiple turns: 
   * human-human dialogues collected via Amazon Mechanical Turk;
   * Built-in user simulators are provided;
 * input sentences: natural language;
 * data size: 
 
|Task|Intents|Slots|Dialogues|
| -----| ----- | ----- | ----- |
|Movie-Ticket Booking|11|29|2890|
|Restaurant Reservation|11|30|4103|
|Taxi Ordering|11|29|3094|

 * semantic annotation: dialogue act
 * tasks: NLU (slot tagging)
 * Download: https://github.com/xiul-msr/e2e_dialog_challenge
 
