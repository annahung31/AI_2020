# 4-4 Local Beam Search

Beam: 光束

拿多個 states 去測試，撒多一點的 random state。多點爬山。

但有可能發生群聚的現象，不一定是好事

![4-4%20Local%20Beam%20Search%20371d091fc6b04b4ca94d835b40cf0119/IMG_3927.jpg](4-4%20Local%20Beam%20Search%20371d091fc6b04b4ca94d835b40cf0119/IMG_3927.jpg)

→ Stochastic beam search: 在選取下一個 states的時候， random 選取那些比較高機率是好的 states。