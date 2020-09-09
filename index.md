# 自然語言處理可視化(NLP visualization demo)

## 目錄
  * [前言](#前言)
    + [目的](#目的)
    + [主要工具](#主要工具)
    + [文本來源](#文本來源)
    + [文本預處理](#文本預處理)
  * [靜態可視化](#靜態可視化)
    + [依據中文文本](#依據中文文本)
    + [依據英文文本](#依據英文文本)
  * [動態可視化](#動態可視化)
    + [依據中文文本](#依據中文文本-1)
    + [依據英文文本](#依據英文文本-1)

## 前言
### 目的
為了在[祐生基金會](https://www.archilife.org)報告[Text Analytics with Python: A Practical Real-World Approach to Gaining Actionable Insights from your Data](https://www.amazon.com/Text-Analytics-Python-Real-World-Actionable/dp/148422387X)，實作了一遍書中介紹的各種NLP操作，並將結果以視覺化的圖表呈現。由於原作者已經提供了完整[程式碼](https://github.com/dipanjanS/text-analytics-with-python)，這裡就只簡單記錄一些結果以及書上沒提到的套件。

### 主要工具
  + `pandas`
  + `NLTK`
  + `scikit-learn`
  + `spaCy`
  + `gensim`
  + `scattertext`
  + `fastHan`

### 文本來源
祐生基金會的例行活動公開紀錄文，包含 `國政聯誼會` 57篇及 `見識之旅` 44篇，兩種文類合計 **101** 篇。文本包含中文原文及英文譯文。
  + 按[文章分類](https://github.com/haowen-howard/Archilife-NLP/blob/master/DataFrame_by_articles_101rows.pkl)，共101個資料點
  + 按[段落分類](https://github.com/haowen-howard/Archilife-NLP/blob/master/DataFrame_by_paragraphs_412rows.pkl)，共412個資料點

### 文本預處理
  + 中文斷詞跟NER都使用`fastHan`，斷詞風格依據中研院`as`
  + 英文斷詞跟NER都使用`spaCy`

## 靜態可視化

### 依據中文文本
- 文本類別分佈：使用PCA將文本向量降至2維，這裡的類別是文本實際的類別（`國政聯誼會` = Meeting， `見識之旅` = Trip）
---
![PCA](https://haowen-howard.github.io/Archilife-NLP/PCA%20Archilife%20events.png)

- 文本聚類分佈：使用Kmeans計算文本向量之間的距離，預先設定2個聚類中心，這裡的類別是根據Kmeans計算出來的類別（即`0` 或 `1`）
---
![Kmeans](https://haowen-howard.github.io/Archilife-NLP/Kmeans%20Archilife%20events.png)

- 文本相似度：使用餘弦相似性計算語料庫內的文本相似度，樹狀圖末梢標示文本事件的年、月以及文本類型（`國政聯誼會` = M， `見識之旅` = T）
---
![DocSim](https://haowen-howard.github.io/Archilife-NLP/Similarity%20across%20documents%20in%20the%20corpus_dendrogram.png)

- 句子相似度：使用餘弦相似性計算單一文本內的句子相似度，每個節點代表一個句子（共`16`）。後續導入`TextRank`，設定句子數量（例如`5`）後即獲得文本摘要
---
![SentSim](https://haowen-howard.github.io/Archilife-NLP/Similarity%20across%20sentences%20in%20a%20document_network.png)

  - 原始文本
  > 9月份見識之旅活動，於2019年9月21日由呂明澐小姐帶領12位祐生見習生及其家長們，進行桃園侏儸紀寶石教室暨防災教育體驗之旅。活動開始之初，領隊呂明澐小姐提醒本次活動注意事項及觀察重點，先行建立見習生的背景知識。 本次行程上午至德馨堂參訪，由當地發展協會志工擔任導覽老師。活動一開始即介紹該建築座東向西，風水上有聚財之意，俚語稱「座東向西，賺錢無人知」。隨後說明德馨堂為燕尾式閩南傳統民居，在古代認為鳥是通天靈物，能敬天通神，故燕尾翹脊多見於廟宇或官宅，由此可知其祖先當時有官職在身。緊接著前往侏儸紀博物館。導覽人員首先解說寶石生成的環境要件及各式寶石的特徵和產地，其中紅色尖晶石與紅剛玉外觀相似，過去常被誤認，英國皇家王冠上的黑王子紅寶石後被證實為紅色尖晶石即案例之一。接著觀賞寶石開採紀錄片，內容記述寶石礦坑的真實樣貌。礦工須下爬約台北101大樓高的距離至地底採礦，礦坑內部粉塵飛揚、工作環境惡劣，炸礦脈也易發生坍塌，故駐紮地底的礦工平均壽命不超過35歲，值得我們反思貧富差距的問題。影片播畢後，導覽人員教導簡易的琥珀鑑定方法—將琥珀放進飽和鹽水中，因其相對密度較小，會懸浮於飽和鹽水中。 中午飯後，前往桃園防災教育館。導覽人員藉由互動式模型解釋颱風、地震及土石流等天災發生的成因。其中特別說明地震發生時，人們會因地震波的傳播感受到搖晃，地震波主要有破壞力較小的P波與破壞力較大的S波，目前地震警報即透過最先抵達的P波預估S波之振動大小，並在S波抵達前發出警報，爭取數秒的預警時間。隨後至火災防治區，火災發生原因可分為四類，不同類型的火災須採取不同滅火方式，避免造成更大的危害，眾人亦於濃煙密布的房間演練火災發生時如何逃生。參訪當天為921大地震20周年，導覽人員特別提醒地震避難時應記住「趴下」、「掩護」、「穩住」三大步驟，找到適當躲避地點後應以雙手護住頭及頸椎趴跪於地面，隨即於地震體驗平台實地練習，以備往後地震避難時之需。至此，本日活動已近尾聲，大家一起合照留念後搭車返程，並期待於下次見識之旅再相見。
  
  - 摘要文本
  > 9月份見識之旅活動，於2019年9月21日由呂明澐小姐帶領12位祐生見習生及其家長們，進行桃園侏儸紀寶石教室暨防災教育體驗之旅。活動開始之初，領隊呂明澐小姐提醒本次活動注意事項及觀察重點，先行建立見習生的背景知識。導覽人員首先解說寶石生成的環境要件及各式寶石的特徵和產地，其中紅色尖晶石與紅剛玉外觀相似，過去常被誤認，英國皇家王冠上的黑王子紅寶石後被證實為紅色尖晶石即案例之一。導覽人員藉由互動式模型解釋颱風、地震及土石流等天災發生的成因。參訪當天為921大地震20周年，導覽人員特別提醒地震避難時應記住「趴下」、「掩護」、「穩住」三大步驟，找到適當躲避地點後應以雙手護住頭及頸椎趴跪於地面，隨即於地震體驗平台實地練習，以備往後地震避難時之需。
  
---
後記：後來發現有`textrank4zh` 這個套件，專門處理中文摘要。使用`TextRank`需要事先斷句、斷詞，而`textrank4zh` 的好處是直接餵入原始文本，就能獲得關鍵詞、關鍵短語、摘要。例如：

```python
import textrank4zh 
from textrank4zh import TextRank4Keyword, TextRank4Sentence

tr4w = TextRank4Keyword()
tr4w.analyze(text=text, lower=True, window=2) 

print( '關鍵詞：' )
for item in tr4w.get_keywords(20, word_min_len=1):
    print(item.word, item.weight)
print('='*20)
print( '關鍵短語：' )
for phrase in tr4w.get_keyphrases(keywords_num=20, min_occur_num=1):
    print(phrase)

tr4s = TextRank4Sentence()
tr4s.analyze(text=text, lower=True, source = 'all_filters')
print('='*20)
print( '摘要：' )
for item in tr4s.get_key_sentences(num=5):
    print(item.index, item.weight, item.sentence) 
```
這裡的text就是上面的`9月份見識之旅`，執行之後得到：

    關鍵詞：
    後 0.027962039363435023
    地震 0.022010169581731007
    於 0.014880799653226645
    發生 0.013589951544039922
    寶石 0.013551887178181725
    導覽 0.010060511434570879
    火災 0.009771097997533784
    波 0.00949178439970326
    時 0.009116332003172464
    見 0.008749194133705994
    人員 0.008166338970883414
    見識 0.007826782749554022
    桃園 0.007740704753034728
    前往 0.00760413864186173
    地底 0.007568837029280538
    活動 0.007468707396160205
    體驗 0.00739460652918148
    環境 0.0070961613242429295
    紀 0.006957075437160697
    錢 0.0069192172065872665
    ====================
    關鍵短語：
    導覽人員
    火災發生
    於地震體驗
    後地震
    地震發生時
    火災發生時
    ====================
    摘要：
    14 0.09016204400462761 參訪當天為921大地震20周年，導覽人員特別提醒地震避難時應記住「趴下」、「掩護」、「穩住」三大步驟，找到適當躲避地點後應以雙手護住頭及頸椎趴跪於地面，隨即於地震體驗平台實地練習，以備往後地震避難時之需
    0 0.07976884824618512 9月份見識之旅活動，於2019年9月21日由呂明澐小姐帶領12位祐生見習生及其家長們，進行桃園侏儸紀寶石教室暨防災教育體驗之旅
    6 0.07576174585612215 導覽人員首先解說寶石生成的環境要件及各式寶石的特徵和產地，其中紅色尖晶石與紅剛玉外觀相似，過去常被誤認，英國皇家王冠上的黑王子紅寶石後被證實為紅色尖晶石即案例之一
    9 0.07008120311442011 影片播畢後，導覽人員教導簡易的琥珀鑑定方法—將琥珀放進飽和鹽水中，因其相對密度較小，會懸浮於飽和鹽水中
    13 0.06998434006205283 隨後至火災防治區，火災發生原因可分為四類，不同類型的火災須採取不同滅火方式，避免造成更大的危害，眾人亦於濃煙密布的房間演練火災發生時如何逃生

以相同的文件來說，`TextRank`的摘要結果比`textrank4zh` 還要好，前者抓到了事件的起承轉合，後者則是拘泥於事件的細節。導致兩者差異的原因留待日後進一步了解。
  
### 依據英文文本
- 文本類別分佈(2D)：將文本向量的特徵限縮至2個，顏色代表文本的實際類別
---
![2Dtfdf](https://haowen-howard.github.io/Archilife-NLP/2_features_from_tfidf_EN.png)
- 文本類別分佈(3D)：將文本向量的特徵限縮至3個，顏色代表文本的實際類別，呈現25種角度
---
![3Dtfdf](https://haowen-howard.github.io/Archilife-NLP/3_features_from_tfidf_EN.png)


## 動態可視化
---
每一張圖表裡的文字都可以點選，也可以搜尋喔 :wink: 

### 依據中文文本
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromCH_CleanTokens.html)__ - 文類1 vs. 文類2
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromCH_CleanTokens.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromCH_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromCH_NER_Label.html)__ - 特徵詞 vs. 文類

### 依據英文文本
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromEN.html.html)__ - 文類1 vs. 文類2
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromEN.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromEN_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromEN_NER_Label.html)__ - 特徵詞 vs. 文類
- __[主題](https://haowen-howard.github.io/Archilife-NLP/Empath_topics_fromEN.html)__ - 文類1 vs. 文類2
- __[文本相似度](https://haowen-howard.github.io/Archilife-NLP/tfidf_embeddings_across_docs_fromEN.html)__ - TF-IDF詞嵌入

---
![Minion](https://octodex.github.com/images/minion.png)
