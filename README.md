# TweetQA

## Models
Fine-tuned models can be found at [here](https://drive.google.com/drive/folders/1Iud7XmXAGzq_j0hJvuf87RS8RlqPOU9y?usp=sharing).

## Generative QA

### ByT5

* BLEU: 0.558790131346158  
* METEOR: 0.502613575953765  
* ROUGE: 0.5774875569494207

ByT5 was fine-tuned based on [google/byt5-base](https://huggingface.co/google/byt5-base)

## Extractive QA

### BERT

* BLEU: 0.795610281998126  
* METEOR: 0.7561982297117271  
* ROUGE: 0.8254572055900666

BERT was fine-tuned based on [deepset/bert-base-cased-squad2](https://huggingface.co/deepset/bert-base-cased-squad2)

### DeBERTa

* BLEU: 0.825894667944233
* METEOR: 0.7979121897801108
* ROUGE: 0.8496681483876328

DeBERTa was fine-tuned based on [deepset/deberta-v3-base-squad2](https://huggingface.co/deepset/deberta-v3-base-squad2)

### RoBERTa

* BLEU: 0.8589009403662852
* METEOR: 0.8276891212958758
* ROUGE: 0.8743271900687026

RoBERTa was fine-tuned based on [deepset/roberta-base-squad2](https://huggingface.co/deepset/roberta-base-squad2)

### Small experiment using different base model

We conducted an small experiment to compare the performance between model fine-tuned based on `deepset/bert-base-cased-squad2` and `bert-base-uncased`. We found that the model fine-tuned based on `deepset/bert-base-cased-squad2` has much better performance.  

* Performance of fine-tuned model based on `bert-base-uncased`
  
| **epoch** | **Exact Match** | **F1 Score** |
| :---: | :---: | :---:|
| 1 | 1.9329896907216495 | 11.653774534483397 |
| 2 | 2.3195876288659796 | 13.183990030046795 |
| 3 | 2.8350515463917527 | 14.197351166926046 |

* Performance of fine-tuned model based on `deepset/bert-base-cased-squad2`
  
| **epoch** | **Exact Match** | **F1 Score** |
| :---: | :---: | :---:|
| 1 | 49.22680412371134 | 65.4802215859955 |
| 2 | 50.0 | 65.99263528443277 |
| 3 | 50.38659793814433 | 66.3370927426314 |

## Voting system

After we generate predictions using aforementioned models, we evaluated the answer for each question using METEOR matric to chose the best one as the final answer.

* BLEU: 0.7692314958713582
* METEOR: 0.7332506954325637
* ROUGE: 0.7786347026068464

## Evaluation

Before you run evaluation script, you need to install [nlg-eval](https://github.com/Maluuba/nlg-eval). Then run following code to evaluate fine-tuned model

```bash
cd data
python tweetqa_eval.py prediction_file ground_truth_file
```

## Acknowledgments

1. [TweetQA official website](https://tweetqa.github.io/)
2. [HuggingFace course - Question Answering](https://huggingface.co/course/chapter7/7?fw=pt)
3. [ByT5](https://huggingface.co/docs/transformers/main/en/model_doc/byt5)
4. [T5](https://huggingface.co/docs/transformers/main/en/model_doc/t5)
