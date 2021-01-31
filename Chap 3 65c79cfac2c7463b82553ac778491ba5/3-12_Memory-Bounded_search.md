# 3-12 Memory-Bounded Search

在前面的 A*方法裡面，都忘記太多東西了，所以要重走的時候，很多東西都要重來。其實我們memory也不是那麼少，我們是有能力提供多一點memory的，你就多用一點，來提升Time complexity啊。

於是，我們可以給定某個定額的memory，再還沒把memory用完之前，你就盡量記錄，等到memory不夠了，再來刪node就好。

### Simplified Memory-Bounded A* (SMA*)

滿的時候，丟掉 `含有最大 f 的 path` (把表現最差的path丟掉)，然後把這個path 的 f 記到 parent上面，這樣以後萬一還有需要回頭，我們能評估這條路值不值得走。

但是萬一有很多條路的 f 都一樣呢........那我們可以每次都加上 timestamp 的資訊，要丟的時候，把最舊的 path 丟掉。

## Properties

只要有足夠的 memory，就能達成 complete and optimal。