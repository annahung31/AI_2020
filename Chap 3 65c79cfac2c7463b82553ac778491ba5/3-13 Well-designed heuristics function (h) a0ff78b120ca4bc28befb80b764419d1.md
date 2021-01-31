# 3-13 Well-designed  heuristics function (h)

前面可以看到，通常 Time complexity 取決於一個好的激勵函數 h，那麼怎麼樣才能設計出好的激勵函數，省時省力呢？

## Example

![3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-26_11.53.11.png](3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-26_11.53.11.png)

結論：

當 h 的值越接近 h*（越接近真實），就越好。

![3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-26_4.45.33.png](3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-26_4.45.33.png)

對任意的 node 而言， h2 > h1， 那稱做 h2 `dominates` h1， h2 會比 h1 好。

### Effective Branching Factor ( b* )

是一種用來衡量 激勵函數設計得好不好的指標，受到層數的影響較小，所以比較好比較。

b* : 假設理想狀態是每一次展開都是 b* 個 branch。

意義： 平均的 branch 值。

當 b* 越小， search 越有效率。（不用展開那麼多node）

## 如何設計出好的激勵函數？

### [法一] 把問題簡化、拿掉一些constraint

(relaxed problem)

![3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-27_12.00.51.png](3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-27_12.00.51.png)

### [法二] 從子問題下手

![3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-27_12.02.01.png](3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-27_12.02.01.png)

例如： 先看 1,2,3,4的移動，把其餘的都當作一樣。

把所有可能都算過，存成pattern database，在之後處理真正問題時，當成 激勵函數來查表使用。

Q: 可以直接把子問題們的 h 相加作為最後的 h 嗎？

A: 不行的，這樣會高估 h，因為在移動 1,2,3,4的問題中，某些情況下 其餘的數字也可能幫助目標。直接相加會毀掉 admissible。

要這樣做可以，就是要在做 1,2,3,4子問題時，把 * 們的移動步數扣掉。 → disjoint pattern databases

### [法三]萬事靠經驗，參數tune起來!

靠經驗知道要挑哪些feature，靠經驗知道要怎麼挑weight

但這不一定保證能找到最佳解，就只是可能找到解而已。

![3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-27_12.07.09.png](3-13%20Well-designed%20heuristics%20function%20(h)%20a0ff78b120ca4bc28befb80b764419d1/_2020-04-27_12.07.09.png)