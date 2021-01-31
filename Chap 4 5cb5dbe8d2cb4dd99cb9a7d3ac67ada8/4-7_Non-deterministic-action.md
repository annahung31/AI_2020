# 4-7 Non-deterministic action(2): with sensor

![4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_7.07.37.png](4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_7.07.37.png)

prediction stage: 給定一個belief state, 做一個 action,  預測他會到哪裡。對照下面是 (1) 

Observation Prediction stage: 針對所有的 belief state 做觀測, 得到一個集合 o。 (2)

Update stage: 真正去做觀測，選取觀測到的那一支。假設觀測到 [B, Clean]，那下一步的結果剩下 b0 belief state。(3)

![4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_6.53.50.png](4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_6.53.50.png)

(a) 是 deterministic 的（沒有不確定性）：

初始狀態 b (belief states) 有兩個

(1) → 向右移動，得到 b^ (Possible- Perceptions )

(2)→ 列出所有可能觀測到的結果: [R, Dirty, B, clean] 

(3)→ 做觀測 → 選取真正觀測到的那個結果，得到 b0

![4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_6.55.07.png](4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_6.55.07.png)

(b) 是 Non-deterministic的，可以看到 b^ 會變大，但是經過觀測之後還是能夠把 belief state 縮小。

![4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_6.56.33.png](4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_6.56.33.png)

總結成一個遞迴式： 給定一個 b (belief state), 做一個 a (action), 得到 b^ ，做 o (observation) , 得到最後結果 b', 成為新的 b, 繼續往下做。

下方的例子是 幼稚園的吸塵器世界，吸完還是有可能又長灰塵，所以 3 有可能變 5 或 7。

另外一個例子：走迷宮

![4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_7.01.12.png](4-7%20Non-deterministic%20action(2)%20with%20sensor%20853bb391f076419687b2c849de84e20c/_2020-04-28_7.01.12.png)

有 4 個 sensor, 代表 4 個可能位置。

→ 每個 sensor 都可以 random 移動一步

→ 觀測旁邊有沒有牆 → 觀測結果是 North, South有牆，所以是在左上方的位置。

（灰色的是牆）