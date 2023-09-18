###### tags: `2023鐵人賽` `qiita` `google`
# [2023 15th鐵人賽] Day3 - 工程師必備技能——Google 之力

> 原文連結：[ググり力、それはエンジニアには必須の能力である - Qiita](https://qiita.com/dodonki1223/items/955819806297ee554b31)

這篇文章介紹如何善用 Google 搜尋，找到想要的答案。根據本文段落標題，整理目錄如下：

+ 使用 `&lr=-lang_ja` 參數排除特定語言結果
+ 用標點符號的英文名稱搜索
+ 善用已定義的符號，提高搜索準確性
+ 搜尋完全相符的結果
+ 在特定網站中搜尋
+ 新增搜尋引擎設定
+ 利用排除搜尋
+ 使用域名搜索
+ 使用關鍵字 vs 進行比較
+ 使用關鍵字 not working 查詢無法運作
+ 使用關鍵字 upgrade 和 migration 查詢版本升級
+ 如何搜尋多個 OSS 程式碼
+ 建立屬於自己的搜尋資料庫

以下是正文。

---

[TOC]

**谷歌能力**，對於工程師而言逐漸成為**必備的技能**。

那麼，各位能否靠自己的谷歌能力找到所需的資訊呢？

以下內容出自 [@Yametaro](https://qiita.com/Yametaro) さん的文章。

```jsx
某天，在進行 Code Review 時

我：「好了，今天也來 Review 同事的 Code 啦」

我：「先從新進的 T 君寫的 Code 開始吧」

我：「我來看看⋯⋯」

我：「嗯？這個 ?? 是什麼寫法啊？」

我：「試著谷歌一下吧⋯⋯」

我：「輸入 JavaScript ?? ，然後按下搜索按鈕」

我：「⋯⋯奇怪？怎麼沒有相關的搜索結果呢⋯⋯」

我：「可惡，標點符號相關的問題確實有時很難谷歌到答案啊⋯⋯」

我：「這樣的話，今天大概只能喝酒然後躺平了吧⋯⋯」

～喝酒，然後進入夢鄉……～
```

所以 JavaScript?? 究竟該怎麼搜尋才對呢？這裡提供一個解答作為提示！

那就是**搜尋「javascript double question mark」**。

![](https://hackmd.io/_uploads/HkjRjoVJ6.png)

這篇文章將以切身經驗，介紹如何培養能夠有效搜尋所需資訊的谷歌能力。

## 不僅限於日本網站，而是從英語網站尋找！

因為看不懂而對英語網站莫名感到厭惡嗎？

遺憾的是，很有可能因此無法找到真正需要的資訊。

考慮到日本和英語系國家的人口，**英語系國家的人口明顯更多**。

因此，相關資訊在英語網站上自然也會更多。

在進行搜尋時，也考慮參考英語網站上的內容吧！

### 該如何搜尋英語網站呢？

雖然有些許差異，但以下是「javascript double question mark」在非日語網站（主要是英語網站）的搜索結果。

![](https://hackmd.io/_uploads/BJ4xhoN16.png)

與一般搜尋的不同之處，在於 Query Parameter（查詢參數）多了 **「&lr=-lang_ja」** 字串。

通過新增 **「&lr=-lang_ja」** 這段參數，可將搜尋範圍限制在非日語網站。

+ 排除日文：`&lr=-lang_ja`
+ 排除繁體中文：`&lr=-lang_zh-TW`
+ 排除簡體中文：`&lr=-lang_zh-CN`

> 可參考這篇指南：[Programmable Search Engine
](https://developers.google.com/custom-search/docs/json_api_reference?hl=zh-tw)

### 讓加上查詢參數這件事不再麻煩

每次搜尋都需要加上 **「&lr=-lang_ja」** 參數感覺有點麻煩對吧。

建議可以**調整瀏覽器的搜尋引擎設定**，便能夠直接搜尋英語網站。

一旦調整完成，即可像這樣進行搜尋：

![](https://i.imgur.com/xnmaTvh.gif)

### 新增搜尋引擎設定

![](https://i.imgur.com/pz5jTxw.gif)

在 Chrome 瀏覽器的網址列中輸入 `chrome://settings/searchEngines`，並按下 Enter 鍵，即可進入搜尋引擎管理畫面。

點擊其他搜尋引擎的「新增」按鈕，然後分別輸入「搜尋引擎」、「快捷字詞」、「網址（%s=搜尋關鍵字）」即可新增。

「搜尋引擎」和「快捷字詞」可依照個人喜好輸入。接著在「網址（%s=搜尋關鍵字）」欄位中，填入下方的 JavaScript 程式碼：

```jsx
javascript: (function () {
  window.open(
    `https://www.google.co.jp/search?q=${decodeURIComponent("%s")}&lr=-lang_ja`
  );
})();
```

在網址欄輸入的關鍵字將以 `%s` 的形式傳遞，加上 `&lr=-lang_ja` 字串產生的網址會顯示新的分頁。

以上操作是透過 JavaScript 實現的，因為 Chrome 的設定頁面並不支援 JavaScript，因此不會在設定頁面中運作。

有了這項功能，即可輕鬆地從非日語網站進行搜尋。只需進行以下三個步驟，就能使用鍵盤進行快速搜索：

1. 輸入 **「command + L」**（導引至網址列）
2. 輸入自行設定的 **「快捷字詞」** 後按下空格鍵
3. 輸入想要查詢的 **「關鍵字」** 後按下 Enter 鍵

## 用符號的英文名稱進行相關搜索吧！

如果在搜尋欄直接輸入符號，搜尋結果可能會不如預期。那該怎麼辦才好呢？

正如開頭的解答所述，可透過輸入符號的英文名稱來搜索。瞭解符號正確的英文名稱將有助於進行更精準的搜索。

儘管也可以用日文名稱進行搜索，理解正確的英文發音仍相當重要。

### 常見符號的英文名稱

這裡列出一些常見符號的英文名稱，在進行搜索時可以嘗試省略 mark 或 sign 等字詞。

詳細結果就自己嘗試看看吧！

| 記號 | 英文 | 中文 |
| --- | --- | --- |
| ! | exclamation mark<br>exclamation point | 驚嘆號 |
| @ | at sign<br>at symbol | 表示「在」的符號<br>又名小老鼠 |
| # | number sign<br>hash mark | 數字記號 |
| $ | dollar sign | 貨幣符號 |
| % | percent sign | 百分比符號 |
| ^ | circumflex accent<br>caret<br>hat | 抑揚符<br>脫字符 |
| & | ampersand | 表示「和」、「與」的符號 |
| * | asterisk | 星號 |
| / | slash | 斜線 |
| ? | question mark | 問號 |
| + | plus sign | 加號 |
| - | minus sign<br>hyphen-minus<br>hyphen | 減號 |
| " | double quotation mark | 雙引號 |
| ' | apostrophe<br>single quotation mark | 單引號 |
| , | comma | 逗號 |
| : | colon | 冒號 |
| ; | semicolon | 分號 |
| ~ | tilde | 波浪號 |
| _ | underscore<br>underline<br>low line | 下底線 |
| ` | grave accent<br>backquote | 重音符<br>反引號 |
| \ | backslash<br>reverse solidus | 反斜線 |
| ¥ | yen sign | 日圓符號 |
| < | left angle bracket<br>opening angle bracket<br>less-than sign | 左角括弧 |
| > | right angle bracket<br>closing angle bracket<br>greater-than sign | 右角括弧 |
| [ | left square bracket<br>opening square bracket | 左方括弧 |
| ] | right square bracket<br>closing square bracket | 右方括弧 |
| { | left curly bracket<br>opening curly bracket | 左花括弧 |
| } | right curly bracket<br>closing curly bracket | 右花括弧 |
| ( | left round bracket<br>left parenthesis<br>opening parenthesis | 左括弧 |
| ) | right round bracket<br>right parenthesis<br>closing parenthesis | 右括弧 |

參考網站：

- [英語の記号・マークの読み方 | 英語＠めもらんだむ](https://memotec.net/etc/mark.html)

### 搜尋 **ruby 的 `&:` 符號**

試著輸入 `ruby ampersand colon`，看看搜尋結果如何吧！

![](https://hackmd.io/_uploads/r1PlAsVyp.png)

## 使用 Google 搜尋已定義的符號和詞彙以提高搜尋準確性！

各位在進行搜尋時，是否只有輸入單字而已呢？

在 Google 搜尋中，有方法可以提高搜尋的精準度。這裡介紹幾個常被使用的主要功能。

詳細內容請參考官方網站：

- [ウェブ検索の精度を高める - Google 検索 ヘルプ](https://support.google.com/websearch/answer/2466433?hl=ja)
- 中文版：[修正 Google 搜尋結果範圍](https://support.google.com/websearch/answer/2466433?hl=)

### 排除含特定字詞的搜尋結果

Google 搜尋說明頁中寫道，使用 **-（減號）** 可排除特定字詞的搜尋結果。

> 在要排除的字詞前加上「-」。例如：Jaguar 速度 -汽車
> 

### 搜尋 Rails 的 resource

在 Rails 的路由管理中，包含 `resources` 和 `resource` 兩種設定。接下來試著搜尋有關 `resource` 的資訊吧。

![](https://hackmd.io/_uploads/rJZ80iVJT.png)

可惡，明明只輸入 `resource` 搜尋，結果卻同時包含了 `resources` 和 `resource` 啊。

這裡試著用 **-（減號）** 排除 `resources` 字詞搜尋看看。

![](https://hackmd.io/_uploads/H19LAj4ya.png)

成功排除 `resources`，只留下 `resource` 的搜尋結果。

## 搜尋完全相符的結果

Google 搜尋說明頁中寫道，使用 **"（雙引號）** 可搜尋完全匹配的結果。

> 將單字或詞句用引號括起來。例如："世界一高い建築物"

### 試試完全匹配的搜尋

試著比較看看 `"世界一高い建築物"` 和 `世界一高い建造物` 兩者的搜尋結果。

嘗試用 `世界一高い建造物` 進行搜尋，會發現即使輸入的是 `世界一高い建造物`，結果仍然出現了`世界で一番高い建物`。

![](https://hackmd.io/_uploads/r19PRoNkp.png)

而進行完全匹配的搜尋時，就只會顯示包含 "世界一高い建築物" 的結果。

![](https://hackmd.io/_uploads/rymdRoEya.png)

接下來會更具體解釋**如何使用這種完全匹配搜尋方法**。

## 在特定網站中搜尋

Google 搜尋說明頁中寫道，使用 **site:** 可在特定網站內進行搜尋。

> 在網站或域名前加上「site:」。例如：site:youtube.com 或 site:.gov
> 

### 試試在特定網站進行搜尋

試著只在 qiita 上自己的文章列表中進行搜尋。

```jsx
github site:https://qiita.com/dodonki1223
```

![](https://hackmd.io/_uploads/H1fYCoNya.png)

只會出現 URL 開頭為 `https://qiita.com/dodonki1223` 的搜尋結果

## 新增搜尋引擎的設定

在「搜尋英文網站」段落也曾提到，可透過在搜尋引擎頁面中設定以下 URL，接著只需要在網址列輸入關鍵字，即可從該網域進行搜尋，也可以在網站內進行搜尋。

### 網域搜尋

```jsx
javascript: (function () {
  window.open(
    `https://www.google.co.jp/search?q=${decodeURIComponent("%s")} site:${location.origin}`
  );
})();
```

### 網站中搜尋

```jsx
javascript: (function () {
  window.open(
    `https://www.google.co.jp/search?q=${decodeURIComponent("%s")} site:${location.href}`
  );
})();
```

## 搜尋錯誤時，利用排除搜尋和完全一致搜尋吧！

在日常業務中遇到**錯誤（Error）**時，我們可能會想直接搜索錯誤內容，這時使用完全一致搜尋可能會更方便。

但像這樣直接搜索錯誤內容，有時很容易被類似的內容所干擾。

在這種情況下，不妨試著用排除字詞或完全一致搜尋，藉此排除其他干擾的資訊，找到自己需要的內容。

### 使用完全一致搜尋的時機

在列舉常見字詞時，部分的詞彙可能導致包含類似詞的搜索結果。像這種情況就很適合完全一致搜尋。

使用完全一致搜尋時，會顯示**與錯誤內容一字不漏完全相符的結果**。

### 使用排除搜尋的時機

搜索結果也可能出現相同的錯誤，但是由不同的程式語言所產生。

在這種情況下，可利用**排除字詞的方法過濾掉不需要的程式語言**，只顯示要查詢的語言結果。

### 搜尋錯誤的技巧

接著介紹一些搜索問題的小技巧。在進行搜索時，釐清這是產品本身獨有的問題，還是與 Library、特定程式語言的問題有關。

直接搜索顯示的 Error 內容，**如果出現大量匹配的結果**，則可能與 **Library、特定程式語言的問題有關**。另一方面，**如果幾乎沒有相符的結果**，則可能是**產品獨有的問題**。

搜索結果多意味著世界上有許多人遇到相同的問題。相反地，搜索結果少則代表遇到同樣問題的人較少。換句話說，在**處理產品程式碼產生的錯誤訊息時，直接從程式碼內部搜索**可能會更有幫助。

以上只是提供一個參考指標，不一定適用於所有情況，但對大方向上的判斷應該會有所幫助。

## 如果網站沒有搜索功能，使用域名搜尋！

![](https://hackmd.io/_uploads/r1lq0i416.png)

在網站沒有內建搜索功能的情況下，可以通過域名搜索來實現簡單的搜索功能。

## 盡可能搜尋最新資訊！

由於技術日新月異，幾年前的文章可能已經過時並不再適用。

在搜尋資料時，需考慮內容更新的時間，養成以最新的資料為優先的習慣。

Google 搜尋也提供設定時間範圍的功能。如果在搜尋時發現許多舊文章，可透過調整**「工具 → 不限時間 → 自訂時間範圍」**設定搜索的時間範圍。

![](https://hackmd.io/_uploads/SkY5RsNyp.png)

## 比較 Service 或 Library 時，使用關鍵字 `vs`！

![](https://hackmd.io/_uploads/BJxsCj4kT.png)

在Service 或 Library 名稱後加上關鍵字 `vs`，會顯示相近的搜尋建議。內容包括自己尚不瞭解的技術，可以在評估技術時提供參考。

這是 @halo1kw さん提供的資訊！

此外，也能使用關鍵字 `alternative` 進行搜尋。

![](https://hackmd.io/_uploads/S1CjAo4J6.png)

## 引入 Library 卻無法運作的情況，使用關鍵字 `not working` 進行搜尋！

![](https://hackmd.io/_uploads/HJonCjNk6.png)

明明已經引入了函式庫，卻不曉得為何無法運作。你是否曾遇過這種情況呢？

這時可嘗試使用 not working 進行搜尋，即可在 GitHub 的 issue 頁面或者 stack overflow 上找到相關的結果。藉此找到在這個世界上和自己遇到相同問題的人，因此推薦這個方法。

## 遇到版本升級的情況，使用關鍵字 `upgrade` 和 `migration` 進行搜尋！

在升級 Library 或 Framework 版本時，使用關鍵字 `upgrade` 和 `migration` 進行搜尋，通常會找到相關的文件。官方的 Upgrade Guide 或 Migration Guide 通常會出現在搜尋結果中，建議先參考官方文件升級。

### 搜尋 upgrade

以 Next.js 為例，用 `upgrade` 進行搜尋時，Upgrade Guide 通常會出現在搜尋結果上方。

![](https://hackmd.io/_uploads/r1ta0sVyT.png)

### 搜尋 migration

以 Yarn 為例，用 `migration` 進行搜尋，Migration Guide 通常會出現在搜尋結果上方。

![](https://hackmd.io/_uploads/BklCAsN16.png)

## 如何搜尋多個 OSS 的程式碼！

> OSS: Open Source Software

在搜尋 Sample Code 時，建議擴展搜尋範圍至多個開源軟體。除了在 Google 搜尋以外，參考中意的開源軟體程式碼也是不錯的方向。然而，目前可能還沒有一個能夠搜尋多個開源軟體的機制。透過撰寫一個小腳本（OSS 搜尋工具）即可輕鬆地進行搜尋。

### OSS 搜尋

通過執行這個腳本，可自動將開源軟體的 repository clone 到本地端並更新，接著利用 Visual Studio Code 的工作區機制，橫跨這些 repository 進行程式碼搜尋。

### 製成腳本

首先建立所需的腳本。

![](https://hackmd.io/_uploads/BkGJJ2416.png)

執行下方所有指令：

```jsx
$ mkdir oss_sample
$ cd oss_sample
$ mkdir list
$ touch ./list/ssh
$ touch clone_and_update.bash
```

接著，將下方內容編寫到 bash 檔案。

```bash
#!/bin/bash

declare -a cloneList=($(cat ./list/ssh))

echo '{
	"folders": [' > oss_sample.code-workspace

for ((i = 0; i < ${#cloneList[@]}; i++)) {
  project_name=$(echo "${cloneList[i]}" | cut -d '/' -f2 | sed -e 's/.git//g')
  project_dir="./${project_name}"

  echo '		{
			"path": "'${project_name}'"
		},' >> oss_sample.code-workspace

  if [ ! -d $project_dir ]; then
    echo $project_name clone start...
    git clone ${cloneList[i]}
  else
    echo $project_name clone skip...
    echo $project_name update
    cd $project_name
    git fetch
    git pull
    cd ../
  fi
}

echo '	],
	"settings": {}
}' >> oss_sample.code-workspace
```

最後在 ssh 檔案中，分行輸入要 clone 的 repository。

```bash
git@github.com:hashicorp/terraform.git
git@github.com:go-gorm/gorm.git
git@github.com:beego/beego.git
```

### 實際執行

執行以下指令：

```bash
$ bash clone_and_update.bash
```

執行後，在 ssh 文件中輸入的 repository 將會被 clone 到本地端，並生成 code-workspace 檔案。

![](https://hackmd.io/_uploads/ByJgJ3NJp.png)

### 嘗試檢索

執行以下指令開啟工作區：

```bash
$ code oss_sample.code-workspace
```

開啟工作區後，即可橫跨已經 clone 的開源軟體搜尋程式碼。

![](https://hackmd.io/_uploads/r1Y-1h4kT.png)

### 閱讀開源軟體的好處

以前在 Zenn 上有篇關於閱讀開源軟體好處的文章，如果有興趣也可以參考閱讀。

- [OSSノススメ - Zenn](https://zenn.dev/dodonki1223/articles/6418df73713313)

## 屬於自己的簡易搜尋資料庫

這是不受限於 Google 搜尋的搜尋技巧。通過將多個資料來源集結到 Slack 中，以此為基礎進行搜尋的方式。下方截圖是「AppSync」的搜尋結果。

![](https://hackmd.io/_uploads/Hyymy241a.png)

### 如何打造屬於自己的簡易搜尋資料庫

首先，在 Slack 中創建自己的工作區。
接著在建立好的工作區設定 RSS 通知功能。RSS 程式可從下方 URL 進行安裝：

- [RSS | Slack App ディレクトリ](https://slack.com/apps/A0F81R7U7-rss?tab=more_info)

### RSS

屬於自己的簡易搜尋資料庫，基本上會以這些 RSS 作為主要資訊來源。可以將自己關注的部落格等網站進行註冊。

以下是我個人註冊的一些 RSS，提供參考。

| RSS | 説明 |
| --- | --- |
| https://b.hatena.ne.jp/hotentry/it.rss | 收集在日本受到關注的 IT 相關文章 |
| https://zenn.dev/feed | 收集 Zenn 上的熱門文章 |
| https://dev.classmethod.jp/feed/ | 收集 AWS 相關資訊 |
| https://aws.amazon.com/jp/blogs/news/feed/ | 收集 AWS 相關資訊 |
| https://go.dev/blog/feed.atom | 收集關於 Go 的資訊 |

將 podcast 也註冊到 RSS 中，如果未來搜尋時觸及到，可能會因此想起「對了，那個 podcast 中曾提過這件事情呢」，然後重聽一次。個人認為這非常有用。
如果有推薦的 RSS 或 podcast，請務必告訴我！

### 其他資料

因為有些資訊無法透過 RSS 獲得，在這裡提供其他的收集方法。

### 在 Slack 顯示 Qiita 趨勢通知

這是我自己製作的工具，使用 [qiita_trend_slack_notifier](https://github.com/dodonki1223/qiita_trend_slack_notifier) 在 Slack 顯示 Qiita 趨勢通知。

![](https://hackmd.io/_uploads/Sk2Ek2EkT.png)

### 使用 Pocket 顯示書籤的內容通知

使用 [pocket](https://getpocket.com/ja/) 和 [IFTTT](https://ifttt.com/)，將書籤頁面通知到 Slack。

透過 [IFTTT](https://ifttt.com/) 的以下設定，可以讓 pocket 儲存的內容顯示在 Slack：

![](https://hackmd.io/_uploads/HkQ4yhV16.png)

在 Chrome 瀏覽器的擴充功能，加入 [Save to Pocket](https://chrome.google.com/webstore/detail/save-to-pocket/niloccemoadcdkdjlinkgdfekeahmflj?hl=ja)，即可將感興趣的頁面存到 pocket，再彙整到 Slack 中。

## 結語

以上內容各位覺得如何呢？希望這些資訊能夠幫上忙。

也歡迎各位留言分享正在使用的搜索方法！

> 15th鐵人賽目錄傳送門：https://ithelp.ithome.com.tw/users/20135558/ironman/6290
