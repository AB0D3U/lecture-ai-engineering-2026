# Lecture 2 – Basic Homework

## 1. Attempted Level

Basic

## 2. Experiment Settings

I changed the `num_train_epochs` parameter from **20 to 10** while keeping all other configuration settings unchanged.

The experiment used the `Qwen/Qwen3.5-0.8B` base model and LoRA fine-tuning without quantization.

## 3. Results

I compared the original experiment (20 epochs) with the modified experiment (10 epochs).

| Metric | Original (20 epochs) | Modified (10 epochs) |
|---|---:|---:|
| Training steps | 40 | 20 |
| Training time | 221 seconds | 109 seconds |
| Final training loss | 0.013842 | 0.098616 |
| Format rate | 100% | 100% |
| Content rate | 90.48% | 90.48% |
| Both rate | 90.48% | 90.48% |

Before training, both experiments had a format rate of approximately 9.52% and a content rate of 0%.

After fine-tuning, both experiments achieved a format rate of 100% and a content rate of 90.48%.

## 4. Comparison and Discussion

Reducing the number of training epochs from 20 to 10 reduced training time from 221 seconds to 109 seconds, which is approximately a 50% reduction.

The 20-epoch experiment achieved a lower final training loss of 0.013842 compared to 0.098616 for the 10-epoch experiment. This indicates that the model fitted the training data more closely with 20 epochs.

However, both experiments achieved the same evaluation scores. This suggests that additional training epochs did not improve the overall evaluation performance on this test set.

Although the overall scores were identical, the specific errors differed between the two experiments. The 20-epoch model struggled with questions about grade release dates and office-hour reservations, while the 10-epoch model struggled with questions about alternative submission formats and reference formatting.

This demonstrates that identical aggregate scores do not necessarily mean that two models behave identically.

## 5. Knowledge and Limitations

The knowledge evaluation showed that the model still had difficulty distinguishing between information available in the FAQ and information that was not provided.

In particular, some questions whose answers were not available in the FAQ were classified as `asserted` rather than `needs_review`. This shows that fine-tuning does not completely eliminate unsupported answers.

## 6. When Fine-tuning Is Useful

Fine-tuning is useful when we want a model to consistently follow a particular response format, style, or task-specific behaviour. It can also help a model learn patterns from a specialised dataset.

However, fine-tuning alone is not always suitable when a task requires accurate, frequently updated information or answers that are not present in the training data. In such cases, retrieval-augmented generation (RAG) or other information-retrieval approaches can help provide relevant evidence to the model.

## 7. Conclusion

The experiment demonstrated that reducing training epochs from 20 to 10 significantly reduced training time while maintaining the same overall evaluation scores.

Although the 20-epoch experiment achieved a lower training loss, it did not produce better aggregate evaluation results. Therefore, for this particular task and dataset, 10 epochs provided a more time-efficient result without reducing the measured evaluation performance.
