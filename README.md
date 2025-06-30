# Sentiment_Analysis

这是一个使用预训练 **BERT 模型** 进行**情感分类（积极 / 消极）**的小项目，支持训练、评估和在线部署。

---

## 🧾 项目结构
```
sentiment/
├── code.ipynb # 主代码，包含训练、评估、部署逻辑
├── sentiment_model/ # 模型保存目录
├── finetuned_sentiment_model/ # 微调后的模型
```

---

## 💡 项目亮点

- ✅ 使用 HuggingFace `bert-base-uncased` 模型进行微调  
- ✅ 使用 `Gradio` 快速构建并部署 Web 页面  
- ✅ 提供模型保存、加载、压缩和下载功能  
- ✅ 使用 `sklearn` 输出精确率、召回率、F1 分数和混淆矩阵  

---

## 🔍 示例预测（部署界面）

> 输入：`I really love this book.`  
> 输出：`Positive (0.99)`

---

## 🚀 快速开始

### ✅ 加载模型和分词器

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

model = AutoModelForSequenceClassification.from_pretrained("./finetuned_sentiment_model")
tokenizer = AutoTokenizer.from_pretrained("./finetuned_sentiment_model")
```

## ✅ 运行 Gradio 部署
```
gr.Interface(fn=predict, inputs="text", outputs="text").launch()
```

## 模型保存与导出
```
# 保存模型
model.save_pretrained("finetuned_sentiment_model")
tokenizer.save_pretrained("finetuned_sentiment_model")

# 打包下载（Colab 示例）
import shutil
from google.colab import files

shutil.make_archive("sentiment_model", 'zip', "finetuned_sentiment_model")
files.download("sentiment_model.zip")
```

## 模型评估结果
准确率（Accuracy）：91%

混淆矩阵结果：

True Positive (TP): 405

True Negative (TN): 390

False Positive (FP): 38

False Negative (FN): 39



