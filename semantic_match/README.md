# Semantic Match
这里对不同的语义模型进行测评，语义模型可以用于sentence to sentence，sentence to passage这两个任务，当然通过变化也可以作为分类任务。

## 数据集
这里在线上找了一个s2s的数据集, 因为只是作为评估，所以只下载了1w条训练数据，三元组【sentence1, sentence2, isSimilar】
```json
{"sentence1": "找一部小时候的动画片", "sentence2": "求一部小时候的动画片。谢了", "label": "1"}
```
https://github.com/CLUEbenchmark/SimCLUE