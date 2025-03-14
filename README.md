# LLM Project

This project focuses on fine-tuning a **Large Language Model (LLM)** for a specific NLP task. Below are the details regarding the dataset, model, hyperparameters, and evaluation metrics.

---

## 📌 Project Task

Example:
- **Task**: Text Summarization
- **Objective**: Fine-tune **DistilBART** on the **Multi-News dataset** to generate high-quality news summaries.
- **Use Case**: Helps journalists or researchers quickly summarize multiple sources into a concise, accurate summary.

##  Dataset

Example:
- **Dataset Name**: Multi-News Dataset
- **Source**: [Hugging Face Dataset](https://huggingface.co/datasets/multi_news)
- **Size**: ~56K articles (train/test split)
- **Description**: Multi-News provides articles from multiple sources and their corresponding summaries.

## Pre-trained Model

Example:
- **Model Used**: DistilBART
- **Hugging Face Repo**: [sshleifer/distilbart-cnn-12-6](https://huggingface.co/sshleifer/distilbart-cnn-12-6)
- **Why this model?**  
  - **Faster than BART-large**  
  - **Lower computational cost**  
  - **Fine-tuned on CNN/DailyMail** for summarization tasks  

## Performance Metrics

Example:
- **Evaluation Metrics Used**:
  - **ROUGE Score** (Measures n-gram overlap between model-generated and reference summaries)
  - **BLEU Score** (Evaluates fluency and coherence)
  - **Inference Time** (Measures model speed)

### Results:
| Metric  | Score |
|---------|------:|
| ROUGE-1 | 18.2% |
| ROUGE-2 | 6.7% |
| ROUGE-L | 9.9% |
| BLEU    | 0.00 (Issue with overly compressed summaries) |

## Hyperparameters

Example:
- **Batch Size**: 8 (Optimal trade-off between memory usage & performance)
- **Learning Rate**: `2e-5` (Best performance in fine-tuning)
- **Max Input Length**: 1024 tokens
- **Max Output Length**: 512 tokens
- **Beam Search**: `num_beams=5` (Improves fluency)

### Key Findings:
- Increasing `num_beams` from **3 → 5** improved **coherence** without slowing inference too much.
- Using **lower learning rates (`2e-5`)** prevented overfitting.
- **Adjusting `max_output_length` to 512** allowed longer summaries, improving ROUGE scores.
