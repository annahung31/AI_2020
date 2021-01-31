# 3-10 Iterative deepening A* (IDA*)

A*可以找到optimal, 但是也一樣會遇到memory不夠的問題 -> Iterative deepening

和IDS的差別： 是用 f 做 cutoff

但一樣用DFS （為了讓space complexity 為linear）

### Time complexity 上的缺點

在前面IDS時是用depth做cutoff, 所以每次重做的部分不太會比新的node多，新的node比較多。

但如果使用 f 做 cutoff,  f 的成長不像 depth 那麼多，每次新增的node 不多，反而是重做的部分佔比例較高，那麼效率就很低。

甚至，假如 f 是 real-value， 那麼 f 是剛好一樣的機率就很低，那每次展開可能只有 b 個 node。

ex: 對 DFS 來說， 在第 d 層 所展開的 node 共有 b * d 個，但在 IDA, 要展開 f = 85.2 的  node 可能只有幾個。

改進 → [RBFS](3-11\RBFS\e6b372788b2446989351bd993a4d0ce4.md)