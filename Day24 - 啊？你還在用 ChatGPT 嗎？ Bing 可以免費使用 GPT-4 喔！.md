###### tags: `2023鐵人賽` `qiita` `ChatGPT`  `Bing` `GPT-4`
# [2023 15th鐵人賽] Day24 - 啊？你還在用 ChatGPT 嗎？ Bing 可以免費使用 GPT-4 喔！

> 原文連結：[えっ、まだChatGPT使ってんの？ Bingは無料でGPT-4使えますよ！ - Qiita](https://qiita.com/takao-takass/items/16a7052a4a0e857b7c90)

這篇文章主要是介紹 Bing Chat，和 ChatGPT Plus 同樣支援 GPT-4，卻能夠免費使用！然而，使用次數限制卻是一大硬傷，這點文中也有提及，但用作個人開發等用途，或許也不失為一種選擇。

此外，作者也舉出幾項實際導入開發使用的範例，可提供參考：

- 用於建立 Debug 配置
- 完成轉換（移植）腳本語言
- 改善程式碼

以下正文開始。

---

[toc]

## 前言

儘管使用這種吸睛的標題，但我無意說 ChatGPT 任何壞話。無庸置疑，ChatGPT 是非常優秀的產品，實際上也帶給世界巨大變化。ChatGPT 作為大力普及 LLM 的先驅者，是相當偉大的存在。

而這一回，我會將重點聚焦在使用費用上。

對於那些想使用 Chat GPT Plus（或已經在使用），但覺得價格有點高的人，希望這篇文章能夠有所幫助。

## ChatGPT⋯⋯感覺有點貴

GPT-4 的高準確度，真的很棒啊！

我在編寫程式，或決定使用哪些產品時也經常使用！

然而，要使用 ChatGPT 的 GPT-4，每月個需支付 3,000日圓(※)。

如果公司出錢的話完全沒問題，但如果是用於個人使用，老實說不覺得有點貴嗎？

> ※ 確切來說是 20 美元，以 1 美元兌換 150 日圓的匯率計算，會是 3000 日圓。

![](https://hackmd.io/_uploads/BJocvZxb6.png)

## 一起免費使用 GPT-4 吧

想使用 GPT-4！但每個月 3000 日圓有點貴啊！ ！

在這種情況下，試試免費使用 GPT-4 吧！ ！

是否能在不支付 3,000 日圓的情況使用 GPT-4？

是否真有這麼好的事情？

原來這種好事，還真的存在著。

## 雖然叫做 Bing

你是否聽過 Bing 搜尋呢？這是 Microsoft 的搜尋引擎。

https://www.bing.com/search?q=Bing+AI&showconv=1&FORM=hpcodx

Bing 搜尋有個名為「Chat」的功能，其功能與 ChatGPT 完全相同，並且也可以使用 GPT-4。

選擇「より厳密に（更精確）」的選項，將得到更準確的答案（與 AI 查詢資訊來源一致）。
如果使用個人帳號登入，UI 會略有不同，可以透過開啟「使用 GPT-4」的開關來使用 GPT-4。

當然，這是可以免費使用的。

![](https://hackmd.io/_uploads/HJjAoGeZT.png)

在過去兩週中，我透過 Bing Chat 來編寫程式和進行研究。我的感想是，Bing Chat 能做到與  ChatGPT 的 GPT-4（每個月 3,000日圓的方案）相同的事情。

首先，由於是 GPT-4，回答給出的程式碼相當準確。

我當時基於興趣，正在學習 Go 語言，僅透過複製貼上的動作，就完成了一個 Web 程式。

若是 ChatGPT 的免費版本（GPT-3.5），在許多情況下都需要進行些微修改，因此不出所料 GPT-4 表現得更好。

## 唯一的缺點

~~依照 Microsoft 的慣例，使用 Bing Chat 必須透過 Microsoft Edge 瀏覽器。~~
~~請注意如果不是用 Edge 瀏覽器，就無法使用 Bing Chat。~~
~~Fu○k Microsoft！~~

2023 年 9 月 4 日 追記
Bing Chat 現在也可以在 Google Chrome 中使用了。謝謝 Microsoft！

![](https://hackmd.io/_uploads/HJ-RXQgZp.png)

2023 年 9 月 28 日 追記
雖然在 Google Chrome 也可以使用 Bing Chat，但似乎只能保留 5 次對話紀錄。而在 Microsoft Edge 可保留 30 次對話紀錄，看來 Edge 以外的瀏覽器還是存在著限制⋯⋯（此外，這是以 Microsoft 帳號登入使用 Bing 為前提。）

![](https://hackmd.io/_uploads/BJ-QEveZT.png)


上下分別代表使用 Microsoft Edge 和 Google Chrome 瀏覽器的對話紀錄次數。

## 實踐：嘗試在實際開發中導入使用

### 建立用於 Debug 的配置！

雖然想要自己建立 VS Code 的 Debug 配置，但完全不知道該怎麼寫才好。

因此，我決定完全交給 Bing Chat。

![](https://hackmd.io/_uploads/BJiXZrlZa.png)

將 Bing Chat 編寫的 Debug 配置複製貼上，並嘗試進行 Debug。 

結果，不需要任何人工介入，Debug 就可以完美進行。

這樣的高準確度，不愧是 GPT-4。 （如果是用 GPT-3.5，可能會出現部分錯誤，導致無法運行。）

![](https://hackmd.io/_uploads/r1wIZSeWp.png)

### 完成轉換（移植）腳本語言！

過去建立的 Windows 批次檔（.bat），通常缺乏可維護性。

如果習慣可能就沒有問題，但對於只熟悉高階語言（例如 Python 或 Java）的人來說，或許會感到困難。現代 Windows 似乎已經將 PowerShell 作為標準，那麼何不將其移植到 PowerShell，使其向高級語言一樣，藉此提高可維護性。

在這種情況下，透過 Bing Chat，語言轉換（移植）即可瞬間完成。

![](https://hackmd.io/_uploads/SJAlE8xbp.png)

只需複製貼上 Bing Chat 生成的腳本，建立 PowerShell 腳本（.ps1 文件），即可正常運行。

![](https://hackmd.io/_uploads/BJMzVLlW6.png)

### 試著改善了程式！

#### 之一：重構所寫的程式

對於自己編寫的程式碼，可能會想知道是否有更好的寫法。

但也不可能每次都請專家來檢查⋯⋯這種時候，就使用 GPT-4 來幫忙檢查重構吧！

![](https://i.imgur.com/GnDAoz5.png)

#### 之二：在自己編寫的程式導入 [OR Mapper（對象關係對映）](https://zh.wikipedia.org/zh-tw/%E5%AF%B9%E8%B1%A1%E5%85%B3%E7%B3%BB%E6%98%A0%E5%B0%84)

在編寫程式時，你是否曾經出現過「有沒有更好的作法啊？」這樣的想法呢？
這種時候，就讓 GPT-4 來實現這個更好的做法吧！

這次因為不想對 SQL 硬編碼（Hard Code），因此想導入使用 OR Mapper。如果想要靠自己引入 OR Mapper，可能會花費相當大的學習成本。

但有了 GPT-4 就是一瞬間的事情，更友善的是，還可以得知推薦使的工具以及安裝方式（如以下回答，是介紹 Go 的使用方式）。

![](https://i.imgur.com/yXdIYEN.png)

#### 之三：由於替換不同的 Library，需要修改程式

在替換 Library 時，大多數的情況下，函數的使用方式也會改變。換句話說，必須全面重新檢查該程式。

因為通常會發生錯誤，因此需要瞭解該修復的部分，但是「那該如何重新編寫才對？」這件事將會產生學習成本。閱讀文本學習需要花費許多時間，希望能夠快速完成。

能夠自己閱讀和理解固然重要，但如果能更先查看完成的程式碼，或許有助於更快理解內容。特別是在工作時間內，可能無法提供太多的學習時間。

像這種程式修改的情況，有了 GPT-4 將能夠立即完成，準確性也非常出色，只需複製貼上程式碼，程式即可如預期運行。

![](https://i.imgur.com/tW2Pckm.png)

#### 之四：將冗長的程式碼進行拆分

有時在實作中得意忘形，可能一不小心寫出冗長的程式碼⋯⋯
雖然想要拆分成多個檔案，但又不確定該如何分割才好⋯⋯

你是否有過這樣的想法呢？
在這種時候，使用 GPT-4 來協助進行分割吧。

![](https://i.imgur.com/nIjqJce.png)

## 最後

至今為止，為了使用 GPT-4，必須每個月支付 3,000 日圓給 ChatGPT，但當我意識到 Bing Chat 的 GPT-4 也相當優秀後，便開始用於個人興趣的開發用途，並停止支付 ChatGPT 的費用。

GPT-4 回答的精確度非常高，和程式設計的相容性極佳。若是想使用 GPT-4 的同時節省費用，請務必嘗試使用 Bing Chat！
