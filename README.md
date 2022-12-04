# Dcard Popular Posts Prediction
## I. Dcard Popular Posts
* **Dcard Popular Posts**: Dcard 為一大型網路論壇，提供台灣民眾分享各式各樣的貼文。Dcard 首頁會呈現當前的熱門文章，並依照熱門程度排序文章，而能成為熱門文章的貼文，為 36 小時內快速取得大家關注的文章。

    ![](https://i.imgur.com/8pa7wUQ.png)
    
* **Objective:** 透過文章的標題、內文、標籤及發文者資訊等，預測該篇文章發布後是否能成為熱門文章，也希望能藉此了解流行趨勢跟時下熱門話題，找出熱門文章通常具備什麼要素。
## II. Data Collection
* 爬蟲抓取popular/not popular data，資料量為1:1，各約五百多筆資料。

    ![](https://i.imgur.com/su1fRg1.png)

## III. Data Analysis
**1. Popular and Not Popular Forum:**

![](https://i.imgur.com/NtGwjht.png)

**2. Word Cloud**



|        | Popular | Not Popular |
| ------ | ------- | ----------- |
| **Title**  |    ![](https://i.imgur.com/Ogq6eBZ.png) | ![](https://i.imgur.com/37b0plv.png)
| **Topics** |![](https://i.imgur.com/A2cifFI.png)| ![](https://i.imgur.com/rqQFKDf.png)|

## IV. Data Preprocessing

![](https://i.imgur.com/ya0ekNb.jpg)

## V. Model
* Naive Bayes
* Logistic Regression
* K Nearest Neighbor
* MLP

## VI. Experiments
### All Model

|          Method          | Accuracy | Precision | F1 score | ROC AUC score |
|:------------------------:|:--------:|:---------:|:--------:|:-------------:|
|        Naive Bayes       |   0.85   |    0.84   |   0.84   |      0.85     |
|    Logistic Regression   |   0.85   |    0.84   |   0.84   |      0.85     |
|         KNN(k=10)        |   0.79   |    0.78   |   0.79   |      0.80     |
| MLP 4 layer with dropout | **0.87** |  **0.81** | **0.87** |    **0.87**   |

### KNN
|  k | without  categorical feature | with  categorical feature |
|:--:|:----------------------------:|:-------------------------:|
| 10 |           **0.76**           |          **0.79**         |
| 20 |             0.73             |            0.76           |
| 30 |             0.71             |            0.71           |

### MLP
* **Models**

|                             | input layer | hidden layer 1 | hidden layer 2 | output layer | dropout |
|-----------------------------|:-----------:|:--------------:|:--------------:|:------------:|:-------:|
| MLP 4 layer without dropout |     128     |       64       |       32       |       1      |  False  |
|  MLP 4 layer  with dropout  |     128     |       64       |       32       |       1      |   True  |
|         MLP 3 layer         |      64     |       32       |                |       1      |   True  |
|         MLP 2 layer         |      64     |                |                |       1      |   True  |

* **Results**

|            Method           | Accuracy | Precision | F1 score | ROC AUC score |
|:---------------------------:|:--------:|:---------:|:--------:|:-------------:|
| MLP 4 layer without dropout |   0.81   |    0.81   |   0.81   |      0.81     |
|   MLP 4 layer with dropout  | **0.87** |  **0.88** | **0.87** |    **0.87**   |
|         MLP 3 layer         |   0.82   |    0.82   |   0.82   |      0.82     |
|         MLP 2 layer         |   0.82   |    0.82   |   0.82   |      0.82     |

### Categorical Feature

|            Method           | without  categorical feature | with  categorical feature |
|:---------------------------:|:----------------------------:|:-------------------------:|
|        Multinomial NB       |             0.71             |            0.85           |
|     Logistic Regression     |             0.76             |            0.85           |
|          KNN(k=10)          |             0.76             |            0.79           |
| MLP 4 layer without dropout |             0.76             |            0.81           |
|   MLP 4 layer with dropout  |             0.86             |            0.87           |
|         MLP 3 layer         |             0.81             |            0.82           |
|         MLP 2 layer         |             0.79             |            0.82           |




