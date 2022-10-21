

EH-FT(LoRA) results

There is little change in the results as the intermediate dimension r increases. This is very similar to the phenomenon of LoRA[1], probably because of the normalization factor.


| r    | RTE   | BoolQ | QNLI  |
|------|-------|-------|-------|
| 8    | 88.68 | 86.69 | 94.73 |
| 16   | 87.73 | 86.42 | 94.62 |
| 32   | 87.54 | 86.30 | 94.73 |
| 256  | 87.82 | 86.40 | 94.81 |
| 512  | 87.20 | 86.54 | 94.75 |
| 1024 | 88.26 | 86.65 | 94.79 |


[1] Edward J Hu, Yelong Shen, Phillip Wallis, Zeyuan Allen-Zhu, Yuanzhi Li, Shean Wang, Lu Wang, and Weizhu Chen. 2021. Lora: Low-rank adaptation oflarge language models. arXiv preprint arXiv:2106.09685.