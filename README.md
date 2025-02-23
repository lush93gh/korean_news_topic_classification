# Project：韓文新聞分類

這個專案的資料修改自 [YNAT](https://klue-benchmark.com/tasks/66/overview/description) 資料集，藉由韓文的新聞標題，來判斷該新聞的主題分類

訓練資料集（`train.csv`） 、驗證資料集（`val.csv`）、測試資料集（`test.csv`）分別有 40,000、5,000、5,000 筆新聞的資料，每個資料集都包含以下欄位：
- `id`: 該新聞的 ID
- `title`: 該新聞的標題，例如 `G20 때 홍콩 문제 알리자…홍콩 시민들 릴레이 시위 예고`
- `topic`: 該新聞的主題，例如 `사회`

`tppic` 有 7 種可能：
- `IT과학`: 資訊與科技
- `경제`: 經濟
- `사회`: 社會
- `생활문화`: 生活文化
- `세계`: 國際
- `스포츠`: 運動
- `정치`: 政治

目標是要用訓練資料集來訓練一個模型，輸入一個新聞標題，輸出一個預測的主題（上述 7 種的其中一個），並且用預測測試集來計算準確率 (Accuracy)。

## 思路及流程

此為純文字分類問題。

比較有效的方式是找一個 pre-trained language model，該模型必須能 output 韓文的 sentence embedding，接著 apply transfer learning 去訓練分類的 task。 詳細流程如下：

*   需求理解
*   資料分析 (EDA)
*   資料前處理 (Preprocess)
*   Proof of Concept (設計小模型，MVP 概念驗證、快速迭代)
*   Model Design and Training
*   Evaluation

### TL;DR;

Best model，evaluation 數據如下:
- accuracy: 0.7910
- f1_macro: 0.7916
