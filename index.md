## 自然語言處理視覺化呈現

+ 目的：為了在[祐生基金會](https://www.archilife.org)報告[Text Analytics with Python: A Practical Real-World Approach to Gaining Actionable Insights from your Data](https://www.amazon.com/Text-Analytics-Python-Real-World-Actionable/dp/148422387X)，實作了一遍書中介紹的各種NLP操作，並將結果以視覺化的圖表呈現。

+ 主要工具：
  + `pandas`
  + `NLTK`
  + `scikit-learn`
  + `spaCy`
  + `gensim`
  + `fastHan`
  + `scattertext`

+ 文本來源：祐生基金會的例行活動公開紀錄文，包含 `國政聯誼會` 57篇及 `見識之旅` 44篇，兩種文類合計 **101** 篇。文本包含中文原文及英文譯文。
++ 按[文章分類](https://github.com/haowen-howard/Archilife-NLP/blob/master/DataFrame_by_articles_101rows.pkl)，共101個資料點
++ 按[段落分類](https://github.com/haowen-howard/Archilife-NLP/blob/master/DataFrame_by_paragraphs_412rows.pkl)，共412個資料點

+ 文本預處理：
++ 中文斷詞跟NER都使用`fastHan`，斷詞風格依據中研院`as`
++ 英文斷詞跟NER都使用`spaCy`

---
每一張圖表裡的文字都可以點選，也可以搜尋喔 :wink: 

### 中文文本的分析結果
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromCH_CleanTokens.html)__ - 文類1 vs. 文類2
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromCH_CleanTokens.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromCH_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromCH_NER_Label.html)__ - 特徵詞 vs. 文類

### 英文文本的分析結果
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromEN.html.html)__ - 文類1 vs. 文類2
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromEN.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromEN_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromEN_NER_Label.html)__ - 特徵詞 vs. 文類
- __[主題](https://haowen-howard.github.io/Archilife-NLP/Empath_topics_fromEN.html)__ - 文類1 vs. 文類2
- __[文本相似度](https://haowen-howard.github.io/Archilife-NLP/tfidf_embeddings_across_docs_fromEN.html)__ - TF-IDF詞嵌入

---
![Minion](https://octodex.github.com/images/minion.png)
