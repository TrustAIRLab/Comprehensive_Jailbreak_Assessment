## Submission of DSN

### Methodology Overview

| Jailbreak Taxonomy | Jailbreak Method | Modify the Questions | Access | Models |
| --- | --- | --- | --- | --- |
| Optimization-Based | DSN | ✓ | White-box | Llama-2-7b-chat-hf, Vicuna-7b-v1.5 |

### Detailed Attack Success Rate

| Target Model | ASR@1 mean | ASR@1 std | ASR@1 max | ASR@3 |
| --- | --- | --- | --- | --- |
| Llama-2-7b-chat-hf | 0.721 | 0.078 | 0.825 | 0.95 |
| Vicuna-7b-v1.5 | 0.935 | 0.024 | 0.96875 | 1.0 |

### Methodology description

By incorporating the "Refusal Loss" item as well as the "Cosine Decay weighting schedule method", we propose a novel jailbreak optimization target `DSN loss`, which is proved to be powerful and jailbreak-performance-consistent. Universal jailbreak suffix could be obtained by optimizing the `DSN loss`. For more details, please refer to our paper [`Don't Say No: Jailbreaking LLM by Suppressing Refusal`](https://arxiv.org/abs/2404.16369).

### Settings

Following the submission instruction, the attack results we reported are `optimized from the forbidden_question dataset, and evaluate on the forbidden_question dataset`.  
The Llama-2 model's system prompt template is ensured to align with the `GCG` implementation, e.g. utilize the `fschat` package with version 0.2.20  
The evaluation is conducted using the exact prompt template proposed in the repo*, by querying the `gpt-4o-2024-08-06` model.  
The hyper-parameter settings are the same as our github repo suggested. Specifically the refusal alpha is set to 1E1=10.0, the steps are 500 and the progressive mode is deprecated.  
For each target model, we launch the `DSN` attack several times to report the average and max results.

**NOTE**: The ASR metric might be reported under different threat model settings. More concretely, some attack might be reporting the universal ASR@1 result, while some might report the non-universal ASR@N result, where N refers to the average jailbreak attempts. To clarify upon these points, we involve the ASR@1 and ASR@3 results. Both of them are universal, e.g. one suffix is evaluated upon the entire dataset.

### Contact information

Please feel free to e-mail us at zhouyk12023@shanghaitech.edu.cn if any further questions or concerns might arise.

---
\* The evaluator template, https://github.com/TrustAIRLab/Comprehensive_Jailbreak_Assessment/blob/4d37b103abcb1783b8edf83af03ea4614c03a903/scripts_label/label.py#L175