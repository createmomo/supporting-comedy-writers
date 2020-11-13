# Supporting Comedy Writers: Predicting Audience’s Response from Sketch Comedy and Crosstalk Scripts

We would like to express our sincere appreciation to **all comedians** and **backstage teams** for their hard work to make audiences happy!

**Paper:** [link](https://www.aclweb.org/anthology/2020.codi-1.5) 

![NLP for Comedy Scripts](/Slides/Supporting%20Comedy%20Writers%20-%20Predicting%20Audience's%20Response%20from%20Sketch%20Comedy%20and%20Crosstalk%20Scripts.png)

## Datasets

> Raw Data - Without Annotations

30 items - Each item is a *.txt file of a performance.

**Each file has following content:**

*Actor A：*...

*Actor B:* ...

*Actor A:* ...

*Actor C:* ...

> Annotated Data
#### * Paper Experiments Data
This folder contains the data split used for our experiments described in the paper. If you would like to run experiments in order to compare the results to that of the paper, I would recommend using the data splits in this folder. However, if you just would like to use this data to do something for fun or other things, you can also choose the data *in other formats* (i.e., CONLL, JSON formats). :)

There are two sub-folders inside: **Classification** and **Information Extraction**.

In **Classification**, the format of each file (i.e., script of each performance) is as follows:

1 *Actor A:* ...

0 *Actor B:* ...

1 *Actor A:* ...

...

Therefore, this is actually a binary sentence classification problem. 1 indicates the audience laughed on this sentence, 0 the audience not.

In **Information Extraction**, the format of each file is:

*Actor A : word1 word2 word3* O O O B-Happy I-Happy

#### * CONLL-Format

**Each file has following content:**

*word1* O

*word2* O

*word3* B-Happy

*word4* I-Happy

*word5* O

...

#### * JSON-Format (There are 2 types of json and choose the one you like)
##### *.json1
```json
{
   "id":12, # sentence id, you can ignore this field
   "text":"文松：太神奇了，我踩你腰了，那我怎么一点感觉都没有啊。",
   "meta":{ # you can ignore this field
      
   },
   "annotation_approver":null, # you can ignore this field
   "labels":[ 
      [
         18, # start index
         26, # end index
         "Happy" # class
      ]
   ]
}
```

##### *.json
```json
{
   "id":12, # sentence id, you can ignore this field
   "text":"文松：太神奇了，我踩你腰了，那我怎么一点感觉都没有啊。",
   "annotations":[
      {
         "label":1,
         "start_offset":18,
         "end_offset":26,
         "user":1 # you can ignore this field
      }
   ],
   "meta":{ # you can ignore this field
      
   },
   "annotation_approver":null # you can ignore this field
}
```

## Code
*Classification Baselines*
- [CNN, RCNN, BiLSTM, BiLSTM + Attention, FastText, DPCNN, Transformer](https://github.com/649453932/Chinese-Text-Classification-Pytorch)
- [Bert-tiny, small and base](https://github.com/dbiir/UER-py) (The pre-trained model used for berts can be found [here](https://github.com/dbiir/UER-py/wiki/Modelzoo))

*Information Extraction Baselines*
- [HMM, CRF, BiLSTM, BiLSTM-CRF](https://github.com/649453932/Chinese-Text-Classification-Pytorch)
- [Bert-tiny, small and base](https://github.com/dbiir/UER-py) (The pre-trained model used for berts can be found [here](https://github.com/dbiir/UER-py/wiki/Modelzoo))

This is the command I used for bert mdoels. (You can also find how to use these bert models in official documents. I just put what I used here in case it may help you to more quickly set up the running experiments)
```
! python3 run_ner.py --pretrained_model_path models/mixed_large_bert_tiny_model.bin --config_path models/bert_tiny_config.json --vocab_path models/google_zh_vocab.txt \
                   --train_path 0.train.uer --dev_path 0.test.uer --test_path 0.test.uer \
                   --epochs_num 5 --batch_size 16 --encoder bert
```

> !Note: The information extraction evaluation used relax-match precision, recall and f-scores. Please find more information in the paper.
