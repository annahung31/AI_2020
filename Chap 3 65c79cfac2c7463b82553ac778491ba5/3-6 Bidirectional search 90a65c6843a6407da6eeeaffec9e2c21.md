# 3-6 Bidirectional search

不只從init開始搜，也從goal搜回來，這樣可以把time 複雜度 開根號（因為深度變一半）。可是要犧牲space複雜度，因為如果要把init跟goal出發的路接起來，就要把兩邊的路程都記下來。空間複雜度回復到exponential的狀態。

### 不適用的時候

1. 當goal非單一

2. 當state之間不可逆時（可以去不一定回得來）