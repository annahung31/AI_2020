# 3-9 Best first search- A* search

[https://lh4.googleusercontent.com/VJXlE6xOuo9tQr_yP02Gnc8hW0Lax11Lgfa8W7ss0WnGCYNwg39RgR4TXiepjPlcvdkl_yObqAmKp-hp0ACMHpvJYlkdkJ5kUZoio5MobCIsi81V73UcQOf7IqaAO_UbKjsGPBB4](https://lh4.googleusercontent.com/VJXlE6xOuo9tQr_yP02Gnc8hW0Lax11Lgfa8W7ss0WnGCYNwg39RgR4TXiepjPlcvdkl_yObqAmKp-hp0ACMHpvJYlkdkJ5kUZoio5MobCIsi81V73UcQOf7IqaAO_UbKjsGPBB4)

F(n)將代表從起點經過state n 到 goal 的總path coast。

### Properities

[https://lh4.googleusercontent.com/SM2EghyVWIY03wI1EGhS4f9KuhDevo1f2MVuqv6viZxZUDjDfPRtVcmqaKtodKUHInArEP7nUZi9LipN_Bl0z_RiN182Vsy3moZBn7fl-oNPEksJ5R_GUPxB9MbLFtPrOAshKi2_](https://lh4.googleusercontent.com/SM2EghyVWIY03wI1EGhS4f9KuhDevo1f2MVuqv6viZxZUDjDfPRtVcmqaKtodKUHInArEP7nUZi9LipN_Bl0z_RiN182Vsy3moZBn7fl-oNPEksJ5R_GUPxB9MbLFtPrOAshKi2_)

- Completeness: 通常會，除非有無限多的nodes, 他的f 都比goal f還小。但這個條件很容易達成，只要 step cost > 0
- 時間複雜度：

    h* = 完美估計的激勵函數，也可以理解成從init到goal實際上花的cost。

    如果h = h*, 代表h真的完美估計，那є = 0, 時間複雜度接近constant。

    反之，如果h = 0, 代表激勵函數完全沒用，則時間複雜度退化回 O(b^d)。

- 空間複雜度：推導過程中可以看到frontier 要紀錄的node越來越多，所以也會佔記憶體。
- 對optimal 的討論：
    1. A* is optimal on trees if h is admissible.	#如果是tree只要符合admissible
    2. A* is optimal on graphs if h is admissible and consistent. #如果是Graph，不只admissible還要consistent

- Admissible: h 永遠不高估，亦即 h < = h*
- Consistent: 三角不等式。在目前state 的 h < 往下一步的step cost + 下一步的 h

但這兩個條件，都是充分但不必要的。

意思是如果符合條件，那一定可以找到optimal

假如不符合，還是有可能找到optimal,只是沒辦法保證。

### 對admissible 的證明：

[https://lh4.googleusercontent.com/O-GtJDB6pGMti1GCKHu9ehgmM7A9H8QrJY3QAZLfGLWa2dv0DtUzKS29aW2lsgljq-TotCo0XNkPHUJUAupAEs7YQoGvUp9hNqnFIs-8miNlSRFcBsNJHT831eW_QKNFzZ08Bjp7](https://lh4.googleusercontent.com/O-GtJDB6pGMti1GCKHu9ehgmM7A9H8QrJY3QAZLfGLWa2dv0DtUzKS29aW2lsgljq-TotCo0XNkPHUJUAupAEs7YQoGvUp9hNqnFIs-8miNlSRFcBsNJHT831eW_QKNFzZ08Bjp7)

- 假設不會有多條path通往同一個goal。假設有通往同一個goal, 他會被視為不同的goal。
- n是路徑上經過的某一個node
- G’ 是sub-optimal goal, 也就是第二好的answer。

### 對consistent 的證明：

只要Lemma成立，就可以保證optimal。

[https://lh6.googleusercontent.com/MV3uW_0pAzRYKH2S8Q7rPcgjVndlBEuY-rcJ0ttP3QSpozEIl_5nwS1M6IQ4hwdCRTT5UufT4COfaJTeuRP74MYZjJ67RTvJeO_Yf8yEpLdkSNVgUlNYi5y35Fzfn1qxdO4IZ2MZ](https://lh6.googleusercontent.com/MV3uW_0pAzRYKH2S8Q7rPcgjVndlBEuY-rcJ0ttP3QSpozEIl_5nwS1M6IQ4hwdCRTT5UufT4COfaJTeuRP74MYZjJ67RTvJeO_Yf8yEpLdkSNVgUlNYi5y35Fzfn1qxdO4IZ2MZ)

就像等高線一樣，例如是80的等高線，那範圍以內，< 80的都一定會被造訪過。在等高線外，f只會越來越大，不可能 < 80

[https://lh3.googleusercontent.com/UsY6pAmd4wHD7Db3Nl9EfIJXAD3oTbUgAsAL0WNqYkbgAs20279vu4GGmroNqVSdfrshA6eO3xOTEZIZsYLKpEQCaw3L4WDydVJE1ooEYYbEyDRFgGHf-iHbucjOtcsMOqmMSsTS](https://lh3.googleusercontent.com/UsY6pAmd4wHD7Db3Nl9EfIJXAD3oTbUgAsAL0WNqYkbgAs20279vu4GGmroNqVSdfrshA6eO3xOTEZIZsYLKpEQCaw3L4WDydVJE1ooEYYbEyDRFgGHf-iHbucjOtcsMOqmMSsTS)

[https://lh6.googleusercontent.com/yoGnTrO3MZp32cUBx2QPEk_FKYgIPGdaJsC_x19AIwKK3Es1MG-IQN6sWOQsRw1AI_yB7nfULyGXOOzDfJxdrJowiHejw93wcgAVYLcvobuC-f6YEcDA7j1ETfawdj_VDzC1K6gX](https://lh6.googleusercontent.com/yoGnTrO3MZp32cUBx2QPEk_FKYgIPGdaJsC_x19AIwKK3Es1MG-IQN6sWOQsRw1AI_yB7nfULyGXOOzDfJxdrJowiHejw93wcgAVYLcvobuC-f6YEcDA7j1ETfawdj_VDzC1K6gX)