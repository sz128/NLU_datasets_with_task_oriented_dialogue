# NLU datasets with task-oriented dialogue

Datasets of natural language understanding and dialogue state tracking for task-oriented dialogue, which can be used in research. There are some other survey of datasets in respective of diaogue system, like [AtmaHou's Task-Oriented-Dialogue-Dataset-Survey](https://github.com/AtmaHou/Task-Oriented-Dialogue-Dataset-Survey) (I am one of the contributors). But we focus on how to build a semantic parser for spoken dialogue system.

If you want to know more about NLU of task-oriented dialogue, please see [recommended papers](https://github.com/sz128/Natural-language-understanding-papers).

There is an [implementation](https://github.com/sz128/slot_filling_and_intent_detection_of_SLU) of joint training of slot filling and intent detection for SLU, which is evaluated on ATIS and SNIPS datasets.

## Table of Contents

- #### [Introduction](#intro)
- #### [Datasets with single turn](#single_turn)
- #### [Datasets with multiple turns](#multi_turns)
- #### [Details](#details)

## <a name="intro"></a>Introduction

|  Items | description | example | 
|:--------:|:--------:|:--------:|
| NLU | Natural Language Understanding, which should contains text classification, sequence labelling and semantic parsing tasks. | |
| DST | Dialogue State Tracking | [DSTC 2](https://github.com/matthen/dstc/blob/master/handbook.pdf) |
| domain | dialogue domain | movie, music, flight, restaurant, ... |
| intent | It an abstract meaning which always refers to a sentence or sub-sentence. | The intent of "*show me a movie named Titanic*" is "*find_movie*" |
| slot | It is attribute or key, which should have a value. | "*show me a movie named Titanic*" has a slot-value pair "*movie_name = Titanic*" |
| act type | a general speech action | *inform, deny, confirm, request, hello, bye,* ... |
| dialogue act | act_type(slot=value,...), https://github.com/matthen/dstc/blob/master/handbook.pdf | *inform(movie_name = Titanic), request(price),* ... |

 * **Intent Detection or intent classification**: sentence classification task
 * **Slot Tagging**: sequence labelling task
 * **Slot Filling**: It equals to slot tagging if all values of slots can be aligned into input sentence. Otherwise, the value of slot should be predicted in a classification or generation way.


## <a name="single_turn"></a>Datasets with single turn (not a dialogue)

|  dataset | domain | semantic annotation | tasks | url |
|:--------:|:--------:|:--------:|:--------:|:--------:|
| [ATIS](#atis) | book flight | intent, slot | Intent classification, slot tagging | https://github.com/yvchen/JointSLU |
| [MIT corpus](#mit_corpus) | Restaurant & Movie  | slot | slot tagging | https://groups.csail.mit.edu/sls/downloads/ |
| [SNIPS](#snips) | Playlist, Restaurant, Weather, Music, RateBook, etc. | intent, slot | Intent classification, slot tagging | https://github.com/snipsco/nlu-benchmark/tree/master/2017-06-custom-intent-engines |
| [facebook TOP semantic parsing](#top_semantic_parsing) | navigation and event | hierarchical intent, slot | constituency parsing  | http://fb.me/semanticparsingdialog, https://arxiv.org/abs/1810.07942 |
| [Facebook Multilingual Task Oriented Dataset](https://arxiv.org/pdf/1810.13327.pdf) | ALARM, REMINDER, and WEATHER | intent,slot | Intent classification, slot tagging | https://download.pytorch.org/data/multilingual_task_oriented_dialog_slotfilling.zip |
| [snips_slu_data_v1.0](https://github.com/snipsco/spoken-language-understanding-research-datasets) | SmartLights, SmartSpeaker | intent,slot | Intent classification, slot tagging  | https://github.com/snipsco/spoken-language-understanding-research-datasets |
| [SMP2017-ECDT](#smp2017_ecdt) (in Chinese) | flight, hotel, Chit-chat | intent | Intent classification | http://ir.hit.edu.cn/SMP2017-ECDT, https://github.com/HITlilingzhi/SMP2017ECDT-DATA |
| [E-commerce Shopping Assistant (ECSA)](https://github.com/pangolulu/DCMTL) (in Chinese) | E-commerce Shopping | slot | slot tagging | https://github.com/pangolulu/DCMTL |
| [Clinc Intent Detection](https://www.aclweb.org/anthology/attachments/D19-1131) | Banking, Work, Meta, Auto, Travel, Home, Utility, Kitchen, Small Talk, Credit Cards | intent | Intent classification and out-of-scope detection | https://www.aclweb.org/anthology/attachments/D19-1131.Attachment.zip |
| [FewJoint](https://arxiv.org/abs/2009.08138) (in Chinese) | Many domains for few-shot learning | intent, slot | Intent classification, slot tagging | [Dataset](https://atmahou.github.io/attachments/FewJoint.zip); [Baseline](https://github.com/AtmaHou/MetaDialog) |

## <a name="multi_turns"></a>Datasets with multiple turns (dialogue with context)

|  dataset | #domains | cross_domains | semantic annotation | NLU/DST tasks | url |
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| [cam DSTC 2&3](#dstc_23) | 2 | No | dialogue act | NLU (slot filling), DST (slot-value pairs) | https://github.com/matthen/dstc |
| [DSTC 4](#dstc_4) | ~5 | Yes | speech action, slot | NLU (slot tagging), DST (slot-value pairs) | (challenge participants only) http://www.colips.org/workshop/dstc4/ |
| [google Sim-R/Sim-M/Sim-gen](#google_simulated_dialogue) | 3 | No | act type, slot | NLU (slot tagging), DST (slot-value pairs) | https://github.com/google-research-datasets/simulated-dialogue |
| [cam MultiWOZ 2.0/2.1](#cam_multiwoz_12) | 5 | yes | multi-domains, slot-value pairs | DST (slot-value pairs) | http://dialogue.mi.eng.cam.ac.uk/index.php/corpus/ |
| [maluuba Frames](#maluuba_frames) | 1 | No | intent, dialogue act | NLU (intent classification, slot tagging), DST (slot-value pairs) | https://datasets.maluuba.com/Frames/dl |
| [Microsoft Dialogue Challenge](#msr_dc) | 3 | No | dialogue act | NLU (slot tagging) | https://github.com/xiul-msr/e2e_dialog_challenge |
| [dstc8-schema-guided-dialogue](https://github.com/google-research-datasets/dstc8-schema-guided-dialogue) | 17 | Yes | multi-domains, slot-value pairs, request-slots | DST | https://github.com/google-research-datasets/dstc8-schema-guided-dialogue |
| [MultiDoGo](https://www.aclweb.org/anthology/D19-1460.pdf) | 6 | Yes | over 81K dialogues harvested across six domains | NLU, DST | https://github.com/awslabs/multi-domain-goal-oriented-dialogues-dataset |
| [Taskmaster-1/2](https://www.aclweb.org/anthology/D19-1459.pdf) | 6+7 | No | 13,215 + 17,289 task-based dialogs comprising multiple domains | NLU/DST | https://github.com/google-research-datasets/Taskmaster |
| [CrossWOZ](https://arxiv.org/pdf/2002.11893.pdf)(In Chinese) | 5 | Yes | 5,012 task-based dialogs comprising five domains | NLU/DST | https://github.com/google-research-datasets/Taskmaster |

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
 * Download: https://github.com/matthen/dstc

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
 
 ### <a name="cam_multiwoz_12"></a>cam MultiWOZ 2.0/2.1
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
 
