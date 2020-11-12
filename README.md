# Supporting Comedy Writers: Predicting Audience’s Response from Sketch Comedy and Crosstalk Scripts

We would like to express our sincere appreciation to **all comedians** and **backstage teams** for their hard work to make audiences happy!

![NLP for Comedy Scripts](/Slides/Supporting%20Comedy%20Writers%20-%20Predicting%20Audience's%20Response%20from%20Sketch%20Comedy%20and%20Crosstalk%20Scripts.png)

## Datasets

### Raw Data - Without Annotations

30 items - Each item is a *.txt file of a performance.

**Each file has following content:**

*Actor A：*...

*Actor B:* ...

*Actor A:* ...

*Actor C:* ...

### Annotated Data
#### Paper Experiments Data
This folder contains the data split used for our experiments described in the paper. If you would like to run experiments in order to compare the results to that of the paper, I would recommend using the data splits in this folder. However, if you just would like to use this data to do something for fun or other things, you can also choose the data in other formats (i.e., CONLL, JSON formats). :)

#### CONLL-Format

**Each file has following content:**

word1 O

word2 O

word3 B-Happy

word4 I-Happy

word5 O

...

#### JSON-Format (There are 2 types of json and choose the one you like)
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
