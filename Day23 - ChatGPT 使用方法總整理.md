###### tags: `2023鐵人賽` `qiita` `ChatGPT`
# [2023 15th鐵人賽] Day23 - ChatGPT 使用方法總整理

> 原文連結：[ChatGPT使い方総まとめ - Qiita](https://qiita.com/sakasegawa/items/82069c97a1ee011c2d1e)

這篇文章主要介紹現在正流行的 ChatGPT，整理幾項不論是日常或在工作上，都很實用的提問方式。作者是 [sakasegawa](https://twitter.com/gyakuse)。

使用方法分類如下：

+ 文章範例
    + 提問-回答
    + 創作 Wikipedia 風格的文章
    + 建立任務列表
    + 建立時間表
    + 歸納
    + 將列點用文章呈現
    + 將文章列點呈現
+ 程式碼
    + 生成程式碼
    + 生成程式碼的文件
    + 重構
    + 單元測試
    + DB 設計（資料庫設計）
+ 故事範例
    + 語氣變化
    + 模仿角色的語氣來回答

以下正文開始。

---

[toc]

## ChatGPT 是什麼

這是一款基於 OpenAI，並以令人驚嘆的語言模型 GPT-3(※) 為基底，所開發的聊天應用程式，能夠立即回答任何問題。
本文將介紹各種使用方法。

> ※ 確切來說，是被稱為 GPT-3.5 系列

https://chat.openai.com/

順帶一提，關於 GPT-3，以下 note 的文章也很有用，有興趣也可參考：
[AIがコミットメッセージ自動生成！神ツール『auto-commit』『commit-autosuggestions』の紹介](https://note.com/sakasegawa/n/n9f63e82ef391)

[ChatGPTの仕組みを考えながらプロンプトを作る手法はこちらに別途まとめています](https://qiita.com/sakasegawa/items/e13e29c96fc711cf84bb)

## 使用範例

### 提問-回答

```
〜について教えて

請告訴我關於～

[範例] 請告訴我什麼是 TPP
```

![](https://hackmd.io/_uploads/rJFsKf1Z6.png)

以下是中文版本：

![](https://hackmd.io/_uploads/r1SRKzyWa.png)

### 創作 Wikipedia 風格的文章

```
〜について説明するWikipedia風の記事を出力して

請寫出用 Wikipedia ****風格的文章來解釋～

[範例] 請用 Wikipedia 風格來解釋 gpt-3
```

![](https://hackmd.io/_uploads/Hk8N5fJWa.png)


以下是中文版本：

![](https://hackmd.io/_uploads/B1EI5f1ba.png)

### 建立任務列表

```
〜をタスク化して

請將～任務化

[範例] 請舉出「APEX 變強的方法」
```

![](https://hackmd.io/_uploads/HJFvczy-a.png)

以下是中文版本，發現如果用「任務化」步驟會太詳細，因此換個方式問：

![](https://hackmd.io/_uploads/r1Dd5zkZ6.png)

### 建立時間表

```
xx〜yyの間にzzします。この間のスケジュールを30分刻みで提示して

zz 介於 xx 和 yy 之間，請以 30 分鐘為單位，顯示該時段的時間表

[範例] 我想在 20:00-24:00 這段時間製作報告，請以 30 分鐘為單位安排時間表
```

![](https://hackmd.io/_uploads/S1f5qM1-a.png)

以下是中文版本：

![](https://hackmd.io/_uploads/ryeR9zyb6.png)

### 歸納

```
mixed=以下を要約して

請歸納以下內容

[範例] 請歸納以下內容：

## GPU Resourse 的取得方法

若想要取得 GPU Resourse，現在主要有以下幾種方式：

基本上是根據預算和目的做選擇。

- Host 型的 Juptyer Notebook Service
	- 目的：使用 Spot
	- 預算：每個月 5000 日幣
- GPU（租用或購買 Gaming PC）
	- 目的：持續性學習與推論
	- 預算：每個月 1 萬日幣～
- Cloud GPU
	- 目的：持續性學習與推論
	- 預算：每個月 2 萬日幣～
```

![](https://hackmd.io/_uploads/r1kgjGJ-T.png)

以下是中文版本，這裡意外發現如果沒有加上「幾句話」，會一直鬼打牆用列點的方式回答，因此還是要確實指定希望的格式：

![](https://hackmd.io/_uploads/rk9xoM1-T.png)

### 將列點用文章呈現

```
以下を文章化して

請將以下內容用文章呈現

[範例] 請用以下內容，寫出一段文章：

## GPU Resourse 的取得方法

若想要取得 GPU Resourse，現在主要有以下幾種方式：

基本上是根據預算和目的做選擇。

- Host 型的 Juptyer Notebook Service
	- 目的：使用 Spot
	- 預算：每個月 5000 日幣
- GPU（租用或購買 Gaming PC）
	- 目的：持續性學習與推論
	- 預算：每個月 1 萬日幣～
- Cloud GPU
	- 目的：持續性學習與推論
	- 預算：每個月 2 萬日幣～
ChatGPT
```

![](https://hackmd.io/_uploads/HkkfjG1-6.png)

以下是中文版本：

![](https://hackmd.io/_uploads/B1CfjMk-a.png)

### 將文章列點呈現

```
以下をタスク化して

將以下內容列點呈現

[範例] 將以下內容列點呈現：
明天早上吃完早餐後要去學校午休時必須到花圃澆水，接著放學後要去社團跟老師道歉
```

![](https://hackmd.io/_uploads/BJRNiMJWT.png)

以下是中文版本：

![](https://hackmd.io/_uploads/BJoBiG1Za.png)

## 程式碼

### 生成程式碼

```
xxするyyの関数を出力して

請輸出執行 xx 的 yy 函數

[範例] 請寫出如何判斷閏年的 JavaScript 函數
```

![](https://hackmd.io/_uploads/S1SwoMyWp.png)

以下是中文版本：

![](https://hackmd.io/_uploads/rJz_sGJZT.png)

### 生成程式碼的文件

```jsx
以下の関数のドキュメントをxx形式で出力して

請將以下函數的文件以 xx 形式呈現

[範例] 請將下方函數的說明以 JSDoc 形式表示：

```
function isLeapYear(year) {
    if ((year % 4 === 0 && year % 100 !== 0) || (year % 400 === 0)) {
        return true; 
    } else {
        return false;
    }
}
```
```

![](https://hackmd.io/_uploads/HkQYoz1Wp.png)

以下是中文版本：

![](https://hackmd.io/_uploads/rke9oz1ba.png)

### 重構

以下程式碼的[引用出處](https://www.seplus.jp/dokushuzemi/blog/2018/07/practice_refactoring.html)。

```jsx
以下をリファクタリングして

請重構以下內容

[範例] 請重構以下程式碼：

package composing_methods.replace_temp_with_query.after;

public class Example {

    private int quantity;
    private int itemPrice;

    public double getPrice() {

        int basePrice = quantity * itemPrice;
        double discountFactor;

        if(basePrice > 1000) {
            discountFactor = 0.95;
        } else {
            discountFactor = 0.98;
        }

        return basePrice * discountFactor;
    }
}
```

![](https://hackmd.io/_uploads/SJX6oMkbT.png)

![](https://hackmd.io/_uploads/SktpozyWa.png)

以下是中文版本：

![](https://hackmd.io/_uploads/BJ01nz1Z6.png)

### 單元測試

```
以下の単体テストを書いて

請根據以下內容，寫出單元測試
```

![](https://hackmd.io/_uploads/rk8RoMJ-a.png)

![](https://hackmd.io/_uploads/ryWy2zyWT.png)

※ 第二項測試的 expected 有誤，因為 900*0.98 = 882 才正確，需注意由 AI 產出的測試程式碼也必須經過測試。

### DB 設計（資料庫設計）

```
〜に必要なtable一覧を出力して

請輸出～必要的 table 列表

[範例] 請列出建立 EC 網站必需的 table 列表
```

![](https://hackmd.io/_uploads/S1kZ3M1WT.png)

以下是中文版本：

![](https://hackmd.io/_uploads/rkq-3My-6.png)

## 故事

### 語氣變化

```
「〜ですの」を語尾につけてxxについて説明して

請在句尾加上「〜ですの」對 xx 內容進行說明

[範例] 請用「的語氣」對 xx 內容進行說明
```

![](https://hackmd.io/_uploads/B1b7hfJWp.png)

也可以加上「用 ◯◯ 語調」、「用 ◯◯ 風格」等指令來表示。

以下是中文版本：

![](https://hackmd.io/_uploads/Bko42zkba.png)

### 模仿角色的語氣來回答

```
以下はxxのセリフです
{セリフ例}
xxっぽく、敬語を使わず可愛く、yyについて説明してください。

以下是 xx 的台詞
{台詞範例}
請不用敬語，以可愛並且類似 xx 的方式說明 yy
```

![](https://hackmd.io/_uploads/rynXnfJbT.png)

以下是中文版本：

```
[範例] 以下是魯夫的台詞

"我要成為海賊王！"
"如果你是我的夥伴，我會保護你直到最後一刻！"
"不管發生什麼事，我絕不會成為別人的部下！"
"我不會對任何人低頭，即使是海軍上將也一樣！"
"夢想是不會死的！"
"我要保護的東西，絕對不會被奪走！"
"即使是一個人也要勇往直前！"

請用像魯夫的語氣，不使用敬語且充滿朝氣又像個笨蛋，針對薩爾達傳說進行說明。
```

![](https://hackmd.io/_uploads/HJWK3Mk-6.png)

## Bonus

### GPT-3 的特性

- 可以做到
    - 自動生成各種文件
    - 用來回答問題
- 特徴
    - 超厲害的[馬可夫鏈（Markov chain）](https://zh.wikipedia.org/zh-tw/%E9%A9%AC%E5%B0%94%E5%8F%AF%E5%A4%AB%E9%93%BE)
    - 使用一種稱為 [Transformer](https://zh.wikipedia.org/zh-tw/Transformer%E6%A8%A1%E5%9E%8B) 的架構（曾經成為熱門話題的 [BERT](https://zh.wikipedia.org/zh-tw/BERT) 等也同樣是）
    - 學習前文中詞語之間的關係模式

### [大規模語言模型](https://zh.wikipedia.org/wiki/%E5%A4%A7%E5%9E%8B%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B)

- Flan-U-PaLM（Google），540B（5400 億）類
    - PaLM 學習 540B，Flan-PaLM 在其中進行 1.8k（1800）個任務學習的調整
- Gopher（Google / DeepMind），280B（2800 億）類
- Bloomz（bigscience），176B（1760 億）類
    - https://huggingface.co/bigscience/bloomz
- GPT-3（OpenAI），175B（1750 億）類
    - 提供方式：僅提供付費 API
    - 授權：遵守 API 使用條款
- OPT-175B（Meta），175B（1750 億）類
    - 提供方式：GitHub
    - 授權：非營利性
- Galactica：120B（1200 億）類
    - https://arxiv.org/abs/2211.09085
    - https://galactica.org/
    - 科學相關
- HyperCLOVA（LINE），82B（820 億）類
GPT-NeoX（EleutherAI）：GPT-NeoX-20B，20B（200 億）類
GPT-J（EleutherAI）：GPT-J-6B，6B（60 億）類
    - 提供方式：huggingface
    - 授權：apache-2.0
- GPT-J-japanese-6.8B（Sta）
    - [https://huggingface.co/naclbit/gpt-j-japanese-6.8b](https://huggingface.co/naclbit/gpt-j-japanese-6.8b?text=%E5%85%83%E6%B0%97%E3%81%A7%E3%81%99%E3%81%8B%EF%BC%9F)
    - （private）やみおとめ，20B（200 億）類
- japanese-gpt2-medium（Rinna），1.3B（13 億）類

## References

- [Chain of Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)
    - 有關提高 GPT-3 在執行對話等方面性能的 Chain of Thought（CoT）方法的論文
- [作って理解する Transformer / Attention](https://qiita.com/halhorn/items/c91497522be27bde17ce)
    - 闡述近期 DeepLearning 的超重要成果 Transformer 的好文章
