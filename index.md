## Scattertext文本分析視覺化呈現

+ 目的：為了在[祐生基金會](https://www.archilife.org)報告[Text Analytics with Python: A Practical Real-World Approach to Gaining Actionable Insights from your Data](https://www.amazon.com/Text-Analytics-Python-Real-World-Actionable/dp/148422387X)，實作了一遍書中介紹的各種NLP操作，並將結果以`Scattertext`呈現。
+ 文本來源：祐生基金會的例行活動紀錄文，包含`國政聯誼會` 及 `見識之旅` 兩種文類，共110篇。文本包含中文原文及英文譯文。
+ 主要工具：
  + `NLTK`
  + `spaCy`
  + `fastHan`
  + `gensim`
  + `scattertext`

### 中文文本的分析結果
- __[詞頻](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromCH_CleanTokens.html)__ - 文類1 vs. 文類2
- __[詞頻](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromCH_CleanTokens.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromCH_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromCH_NER_Label.html)__ - 特徵詞 vs. 文類

### 英文文本的分析結果
- __[詞頻](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromEN.html.html)__ - 文類1 vs. 文類2
- __[詞頻](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromEN.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromEN_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromEN_NER_Label.html)__ - 特徵詞 vs. 文類
- __[主題](https://haowen-howard.github.io/Archilife-NLP/Empath_topics_fromEN.html)__ - 文類1 vs. 文類2
- __[文本相似度](https://haowen-howard.github.io/Archilife-NLP/tfidf_embeddings_across_docs_fromEN.html)__ - TF-IDF詞嵌入

![The Dojocat](https://octodex.github.com/images/dojocat.png)

