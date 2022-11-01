# Parameter-Efficient-Tuning-Makes-a-Good-Classification-Head

Source code for EMNLP2022 long paper: Parameter-Efficient Tuning Makes a Good Classification Head

We found that 
> 1. Finetune the pretrained LM with a parameter-efficient algorithm.
> 2. Finetune the pretrained LM with initializing the classification head as the weight from 1.

usually better than direct finetuning.

**We implement our methods base on a open source libary [SwissArmyTransformers](https://github.com/THUDM/SwissArmyTransformer).**

**Step 1.** 

Download checkpoint of [RoBERTa-Large](https://cloud.tsinghua.edu.cn/f/66c42c24ca304cecaf7e/?dl=1) or [BERT-Large](https://cloud.tsinghua.edu.cn/f/6d4f38c96e8c4c16917e/?dl=1) (Provided by SwissArmyTransformer) and decompress.

**Step 2.**


Add checkpoint dir path to line 5 in EH-FT/roberta/scripts/finetune.sh

 **Step3.**
```
cd EH-FT/roberta
python scripts/run_multiseed.py --number-gpu 1 --gpu-s 0 --seed-per-gpu 1 --dataset rte --finetune-type 2step+bitfit
```

 **Step4.**
```
cd EH-FT/roberta
python scripts/run_multiseed.py --number-gpu 1 --gpu-s 0 --seed-per-gpu 1 --dataset rte --finetune-type 2step+bitfit
```
The script will launch [number-gpu] processes with gpu [gpu-s], gpu [gpu-s+1], ..., gpu [gpu-s + number-gpu - 1]. Each process has a different random seed. 

**You can change dataset and finetune-type.**


Dataset: rte, mrpc, boolq, wic, cb, copa, wsc, qnli, stsb

| Finetune-type | name in paper             |
| ------------- | ------------------------- |
| all           | traditional finetuning    |
| 2step+head    | LP-FT                     |
| 2step+bitfit  | EH-FT(BitFit)             |
| 2step+lora    | EH-FT(LoRA)               |
| 2step+pt      | EH-FT(PT)                 |
| bitft/lora/pt | BitFit/LoRA/Prefix tuning |
| head          | Linear Probing            |
| child         | child-tuning              |
| mixout        | Mixout                    |

**Step4.**

See results in runs/ using tensorboard.
