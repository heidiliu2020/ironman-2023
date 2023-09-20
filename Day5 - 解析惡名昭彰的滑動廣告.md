###### tags: `2023鐵人賽` `qiita` `Advertising`
# [2023 15th鐵人賽] Day5 - 解析惡名昭彰的滑動廣告

原文連結：[悪名高きスワイプ広告を解析する - Qiita](https://qiita.com/huzisuke/items/cdc63b4bf9d2ded5b5ca?utm_source=Qiitaニュース&utm_campaign=5f35ea5616-Qiita_newsletter_579_08_16&utm_medium=email&utm_term=0_e44feaa081-5f35ea5616-62820449)

--- 

[toc]

## 本文摘要

在被使用者厭惡的廣告當中，有一種叫做「滑動廣告」。

容易誤觸是原因之一，但經過調查發現，這個廣告似乎是故意將使用者轉移到廣告頁面，而非單純的誤觸。


![](https://i.imgur.com/wSOiSRO.png)

*滑動廣告是一種藉由左右滑動顯示圖片的廣告類型。*

## 什麼是滑動廣告

滑動廣告是在廣告聯盟網站上常見的廣告形式。

使用者可以用手指在螢幕上左右滑動，藉此切換廣告圖片。

特徵是利用滑動的互動性，使用多個訊息和媒體，提供引人入勝的廣告體驗。

## 為什麼會惡名昭彰

然而，滑動廣告並不受使用者歡迎。原因是它容易引發誤觸，一不小心點擊廣告導致頁面跳轉的機會非常高。

當然，從使用者的角度來看，可能會以為是自己誤觸了廣告，或是滑動的手指太早移開螢幕，才會導致跳轉到廣告頁面。

然而，根據本次調查結果，滑動廣告似乎是一種設計，即便使用者並未實際誤觸到，也會模擬誤觸的行為。

以下動畫展示當時的行為：

![](https://imgur.com/opkAgHk.gif)

*只有思慕昔（スムージー）的廣告，在上下滑動時會跳轉到廣告頁面。*

這明顯和*漫畫廣告的行為不同。*

*此外，我們還注意到，左右滑動時也不會造成畫面跳轉。*

## 總結

通過追蹤程式碼，發現滑動廣告只要符合以下條件，就會被視為點擊廣告：

- 點擊起始位置在廣告區域內
- 點擊持續時間不超過 250ms
- 點擊起始和結束位置的 X 坐標差不超過 50pix

換句話說，

**從廣告位置開始的垂直滑動，這動作將會被視為強制點擊廣告。**

所以，至今為止您感受到的「啊、糟糕」，

這絕對不是您的錯，而是廣告的運作方式。

## 相關程式碼

以下是使用 Developer Tools 仔細分析過的內容，其中名為 `swipegallery_layout.js` 的導案負責管理點擊位置等內容。

### 點擊開始時 (touchstart event)

第 1051 行～第 1061 行

重點如下：

- b.time = Date.now(); … 記錄點擊開始時間
- b.p = 0 … 記錄點擊開始座標，初始值為 0

由於 Source code 基本上經過了混淆處理，因此僅供參考。

```jsx
Y.prototype.Ba = function(a) {
    this.V || a.preventDefault();
    if (!this.W && 0 != this.b.length) {
        var b = this.T;
        b.U = !0;
        this.V ? (b.pageX = a.e.touches[0].pageX, b.G = a.e.touches[0].pageX) : (b.pageX = a.e.pageX, b.G = a.e.pageX);
        b.time = Date.now();
        b.A = 0;
        b.p = 0
    }
};
```

### 當手指在點擊時移動 (touchmove event)

第 1061 行～第 1089 行

重點如下：

- a.preventDefault(); … 這段語句將禁用垂直滾動時的畫面移動
- b.p = a.e.touches[0].pageX - b.pageX; … 將初始點擊位置和目前點擊位置的 X 軸座標值相減並代入

```jsx
    Y.prototype.Aa = function(a) {
        if (!this.W && 0 != this.b.length) {
            var b = this.T;
            if (this.V) {
                a.preventDefault();
                if (1 < a.e.touches.length || a.e.scale && 1 !== a.e.scale) return;
                b.p = a.e.touches[0].pageX - b.pageX;
                b.A = a.e.touches[0].pageX - b.G;
                b.G = a.e.touches[0].pageX
            } else {
                if (!b.U) return;
                b.p = a.e.pageX - b.pageX;
                b.A = a.e.pageX - b.G;
                b.G = a.e.pageX
            }
            b.ea = !0;
            var c = this.b[this.d].h();
            this.Ma = 0 > b.p ? 0 : 1;
            a = Math.abs(b.p / this.P);
            var d = !1;
            0 == this.Ma ? ($(c, this.H * a, this.I * a, this.J * a, this.K * a, 0), this.d != this.b.length - 1 ? (c = this.b[this.d + 1].h(),
                $(c, -this.H * (1 - a), -this.I * (1 - a), this.J * (1 - a), this.K * (1 - a), 0)) : d = !0) : ($(c, this.H * -a, this.I * -a, this.J * a, this.K * a, 0), 0 != this.d ? (c = this.b[this.d - 1].h(), $(c, this.H * (1 - a), this.I * (1 - a), this.J * (1 - a), this.K * (1 - a), 0)) : d = !0);
            d && (b.A /= Math.abs(b.A) / this.P + this.La);
            A(this.f.style, Eb(0));
            this.B += b.A;
            A(this.f.style, Fb(this.B, 0, 0))
        }
    };
```

### 結束點擊時 (touchend event)

第 1090 行～第 1097 行

重點如下：

```jsx
((50 > Math.abs(b.p))  // 點擊初始位置和結束位置的 X 座標值差小於 50pix
	&& 250 > a - b.time) // 且點擊持續時間小於 250ms
		&& (this.dispatchEvent("tap"), this.dispatchEvent("tap-" + this.d)), // 發生點擊廣告的事件
```

請注意下方敘述，從第 4 行開始的 `b.U && ...` 這段程式碼實現了上述功能。

```jsx
    Y.prototype.la = function(a) {
        if (!this.W && 0 != this.b.length) {
            var b = this.T;
            b.U && "mouseout" != a.type && (a = Date.now(), 500 < a - this.ua && (50 > Math.abs(b.p) && 250 > a - b.time) && (this.dispatchEvent("tap"), this.dispatchEvent("tap-" + this.d)), this.ua = a);
            b.U = !1;
            b.ea && (a = this.d, Math.abs(b.p) > this.Na && (0 > b.p ? a = this.d == this.b.length - 1 ? this.d : this.d + 1 : 0 < b.p && (a = 0 == this.d ? this.d : this.d - 1)), this.Q(a), b.ea = !1)
        }
    };
```

### 換言之，這些操作代表什麼

當使用者誤以為「在滑動螢幕時，手指卻意外觸摸到廣告」，這種所謂的誤觸實際上是經過精心編寫的「設計」。

當偵測到快速的垂直滑動時，會觸發跳轉到廣告頁面，此時畫面呈現靜止狀態，進而讓使用戶以為是自己「誤點擊」所導致。

反之，如果滑動速度較慢，不論垂直或橫向滑動都不會跳轉廣告頁面。

此外，由於圖像會跟著手指移動，即使被禁止滑動也不容易察覺。

## 誤觸廣告不僅損害使用者體驗，也降低廣告主的品牌價值

每當看到滑動廣告時，最明顯的感受就是，誤觸廣告對使用者並沒有任何好處。不僅損害所在網站的使用者體驗，對於那些被意外點擊的廣告主也不會產生良好印象。

雖然這只是我的猜測，可能存在一些公司利用這種誤觸廣告系統，藉此虛報展示給廣告主看的廣告曝光率。

雖然這次廣告主的產品我也實際使用過，今後也想繼續使用這個品牌，但看到透過這種方式展示廣告真的感覺非常遺憾。

希望廣告主能夠意識到，展示這類型的廣告只會降低品牌價值，並進一步採取相關措施，以確保未來不再出現這種形式的廣告。

從根本上來說，滑動廣告的廣告頁面跳轉絕不是使用者誤觸或程式錯誤造成，而是經過明確設計過的跳頁效果。

我不曉得這是公司的方針或單一工程師想出的壞主意，但比起使用者優先考慮個人利益的態度，同樣作為一名工程師實在令人感到遺憾。

    
## Release Note

### 2023/08/7

- 修正錯誤
- 新增說明

### 2023/08/08

- 新增 *syntax* highlighting 語法高亮效果
    - 感謝 [@getty104](https://qiita.com/getty104) 様

### 2023/08/10

- 新增 Release Note
- 刪除廣告主的名稱
    - 滑動廣告是由刊登網站設定所引起，無法確定廣告主是否得知這件事情。因此考慮品牌名聲，在此選擇不公開廣告主的名稱。
