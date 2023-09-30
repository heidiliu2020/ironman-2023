###### tags: `2023鐵人賽` `qiita` `Node.js`
# [2023 15th鐵人賽] Day16 - Node.js 是什麼？為什麼大家都在使用？

> 原文連結：[Node.jsとはなにか？なぜみんな使っているのか？ - Qiita](https://qiita.com/non_cal/items/a8fee0b7ad96e67713eb)

以下正文開始。

---

[toc]

這篇文章的目的，主要是為了解答以下疑問：

「我們在學習 JavaScript 時，總是以已經瞭解 Node.js 為前提。但 Node.js 不是 Web Server 嗎？為什麼必須安裝？又為什麼大家都在使用呢？」

## 基礎：JavaScript 的特點

首先，必須瞭解 JavaScript 與其他程式語言的差別。

**JavaScript** 是一種在 Chrome 或 Firefox 等「**瀏覽器上**」運行的程式語言；而一般的程式語言，例如 **Python** 和 **Ruby**，通常是在「**電腦上**」運行。[^1]

[^1]: 原本應該用「作業系統上」表達，為了更簡單明瞭，使用「電腦上」的表達方式。~~其實沒有這回事，單純是因為之前製作的圖中寫著「電腦」~~

![](https://imgur.com/6eP6NKJ.png)

執行環境的區別，在於**是否能夠訪問 OS（作業系統）的功能**。

「作業系統的功能」指的是檔案讀寫、以及網路通信等功能。在電腦上運行的應用程式（包括 Python 和 Ruby 等語言）就可以處理這些功能。[^2]

[^2]: 近年來，由於作業系統的安全性有所提升，即使是安裝的應用程式，也無法任意操作系統的所有功能，當應用程式嘗試使用特定功能時，通常需要經過使用者授權。

![](https://i.imgur.com/M1CR0Eg.png)

然而，如果在瀏覽器上運行的程式（JavaScript），擁有作業系統的功能權限，這將存在安全風險。[^3] 舉例來說，只要進到某個網站，就可能被人未經允許讀寫電腦上的檔案，或刪除部分檔案內容，這會是很嚴重的問題。 [^4]

[^3]: ActiveX 這類的技術能夠實現這一點。
[^4]: 雖然與 JavaScript 無關，但我想起很久以前某個遊戲更新，導致包括作業系統等無關數據也被刪除的 HDD BURST 事件，瞭解到程式在某種程度上是能夠任意操作的。

也因為如此，在瀏覽器上運行的 JavaScript，被設計成沒有權限使用作業系統的功能。

但如果完全沒有權限，還是會有些不便，因此瀏覽器會限制性允許 JavaScript 請求作業系統的功能權限。[^5] 近年來，瀏覽器也允許 JavaScript 對相機和麥克風的權限，這讓在瀏覽器上進行網路會議變得更加方便。

[^5]: 瀏覽器是經由安裝的應用程式，因此當然有作業系統的功能權限。

![](https://i.imgur.com/6M0deBc.png)

> 關於前端與瀏覽器之間的關係，推薦閱讀 Huli 撰寫的資安系列文章：[[Day2] 瀏覽器的安全模型](https://ithelp.ithome.com.tw/articles/10314125)

## Node.js 是什麼？

「**Node.js**」是能夠讓 JavaScript 在電腦上運行的工具，就像 Python 或 Ruby 一樣，而不只受限於瀏覽器環境。

![](https://i.imgur.com/bwSylYh.png)

儘管受到許多誤解，但 Node.js 既不是 Web Server，也不是像 Rails 或 Django 的 Web 框架，而是 **JavaScript 的執行環境**。

在 Windows 安裝 Python 時，會得到「python.exe」；同樣地，在安裝 Node.js 時，也會得到「node.exe」。
就像「python.exe」是用於執行 Python 程式碼的應用程式，「node.exe」是用於執行 JavaScript 程式碼的應用程式 = JavaScript 的執行環境。

在 Node.js 中，可編寫 JavaScript 程式來請求作業系統的功能權限。[^6] 意即能夠處理在瀏覽器上無法執行的操作，像是自由讀寫檔案，以及網路通信等作業系統功能。

[^6]: 我曾寫過「JavaScript 有操作作業系統的功能權限」，但這其實是很微妙的表達方式，要實際獲得操作系統的功能權限，必須透過 C++ 編寫 Node.js 的擴充功能，通常會提供 Standard Library 或 Third party Library 使用。

![](https://i.imgur.com/hu0sgZY.png)

因此，Node.js 能夠像使用 Python 或 Ruby 一樣建立 Web 應用程式，但 Node.js 也可用於各種其他用途。

### Node.js 是伺服器端的 JavaScript 執行環境嗎？

在與 Node.js 相關的文章中，經常會看到 Node.js 被描述為「伺服器端的 JavaScript 執行環境」。這是 Node.js 的設計目標，是為了**構築能夠處理大量同時連線的網路應用程式**，而被設計出的 JavaScript 環境。[^7]

[^7]: 有一種名為 CommonJS（ServerJS）用於伺服器端的規範，設計在瀏覽器之外的環境中運行 JavaScript，Node.js 從初期就遵循此規範。

因為具備「可使用 JavaScript 建立 Web 應用程式（Web Server）」的特點，因此經常被描述「Node.js 是伺服器端的 JavaScript 執行環境」。

而在當今的 Web 業界中，Node.js 也廣泛用於**客戶端 JavaScript 的開發環境**。此外，Node.js 也經常用於在本地端電腦上開發「在瀏覽器中運行的 JavaScript」的環境。

這是因為開發者發現，Node.js 具備「能夠在電腦（作業系統）上運行 JavaScript」的特點，因此出現越來越多方便客戶端 JavaScript 進行開發的 Library，這部分稍後也會詳細說明。

**不論其歷史發展如何，目前實際的情況是「Node.js 作為伺服器端的 JavaScript 執行環境，也應用於客戶端 JavaScript 的開發環境」。**

## npm 是什麼？

稍微偏離主題，這裡先解釋一下什麼是 **npm**。

npm 是 Node.js 的套件管理工具。大致如同 Python 中的 pip、Ruby 中的 gem（RubyGems）、Debian 中的 apt、Mac 中的 Homebrew、Rust 中的 cargo。

偶爾會出現 **yarn**，但不必擔心，yarn 基本上可以和 npm 做相同的事情。

這裡的「套件」是指 Library 或 Framework，例如 Vue、React、webpack、jQuery 等等。如果想要在 Node.js 中使用某個 Library，可透過 npm 來安裝，而不需手動下載 js 檔案，並加上 `<script src="xxx.js"></script>` 標籤。

## 為什麼大家都在使用 Node.js？

Node.js 解放 JavaScript 的束縛，使其能夠做到許多事情。

雖然有各式各樣的用途，但目前使用 Node.js 的人，基本上依照目的可歸納為以下三種（至少筆者是這麼認為）：

1. 想要使用**新的 JavaScript 或 TypeScript 規範**來編寫客戶端程式
2. 想要建立 **Web 應用程式**
3. 想要建立 **Mobile/Desktop 應用程式**

### 目標 1.  想要使用新的 JavaScript 或 TypeScript 規範來編寫客戶端程式

![](https://i.imgur.com/fEvrqwL.png)

JavaScript 的新規範（ES2015以後），有關詳細內容與發展的介紹已經隨處可見，因此這裡只會簡短說明。對於 TypeScript，這裡將不會進行探討。

JavaScript每年都會更新規範，不斷加入新功能。特別是在 **ES2015** 版本中，加入許多以往沒有的實用功能。

然而，即使JavaScript更新了規範，也可能發生現有的瀏覽器無法跟上這些規範的問題。為了解決這個問題，出現一種將「以新規範編寫的 JavaScript 檔案」自動轉換（編譯）為「舊規範（ES5）的 JavaScript 檔案」的方法。

目前的主流，用來執行轉換的工具（編譯器）是 **Babel**，而經常用來執行的**環境**則是選擇 **Node.js**。

### 目標 2. 想要建立 Web 應用程式

就像 Ruby + Rails 或 Python + Django 等工具一樣，同樣能使用 Node.js 建立 **Web 應用程式**。

以下是對應的項目列表：

| 執行環境 | 語言 | Web 框架 |
| --- | --- | --- |
| Ruby | Ruby | Ruby on Rails 等 |
| Python | Python | Django 等 |
| Node.js | JavaScript | Express, Next.js 等 |

此外，Node.js 的特點之一是「Node.js 能夠擔任 Web Server 的角色」。（以 Node.js 的設計目的來說，主要就是作為 Web Server）

最初 Node.js 的設計，是用來**構建能夠處理大量同時連接的網路應用程式**，因此同時擔任 Web Server 的功能，能夠有效率的處理請求。

總歸而言，不同於 **Apache** 或 **Nginx** 這類常規的 Web Server，Node.js  能直接接收並處理 HTTP 請求。（實際上，單獨使用 Node.js 作為 Web Server 功能稍嫌不足，因此通常會搭配 Apache 或 Nginx 作為反向代理。）

### **目標 3.**  想要建立 Mobile/Desktop 應用程式

Node.js 可用於開發 **Mobile 或 Desktop 應用程式**。Mobile 應用程式通常會使用 **React Native**，而 Desktop 應用程式，則較多使用 **Electron**。因為沒有使用過 React Native 所以知識有限，這部分只介紹 Electron，還請見諒。

**Electron** 是個使用 **JavaScript + HTML + CSS** 開發 Desktop 應用程式的框架。

**Electron**

https://www.electronjs.org/

![](https://i.imgur.com/r9NnL0p.png)

JavaScript 最初是為網頁設計的語言，常用於處理使用者介面（UI），擁有許多經過洗鍊且成熟的 Library 和 Framework。利用這些資源，可以像 Web 網站一樣，快速建立使用者界面，這是一大優勢。

由 Electron ****建立的應用程式，具備作業系統的功能權限，與瀏覽器中的 JavaScript 相比，能夠更廣泛的應用。此外，Electron 具備跨平台開發（Cross-Platform）的特性，能夠以相同的程式碼，在 Windows、Mac 和 Linux 建立應用程式。

許多像是 Visual Studio Code、Slack、Discord、Twitch、Skype 等的 Desktop 應用程式，均是使用 **Electron** 開發。

### 目標 4. 其他

此外，Node.js 也用於各種用途，例如**打包網頁的 assets**（webpack），**將 Sass 轉換為 CSS**（node-sass），使用**測試工具**（Jest）和**程式碼規範檢查工具**（ESLint），在本地端建立**開發用的簡易 Web Server**（webpack-dev-server），以及**建置靜態網頁**（Gatsby）等功能。

## 最後

Node.js 將會像其他程式語言一樣，為 JavaScript 帶來巨大的潛力。（這也歸功於 V8 JavaScript 引擎的貢獻，由於話題可能變得復雜，因此本文避免提及相關內容）

正如人們所言，與其他語言相比，JavaScript 確實有些設計上的不足（部分原因在於其起源），即使在相同條件下也會有所質疑⋯⋯但我能理解這些看法。然而，沒有哪種程式語言能夠像 JavaScript 一樣，擁有如此眾多的年輕用戶，包含 Library 等在內，以驚人的速度發展，趨勢變化莫測。

jQuery 等技術現今已被當作歷史文物，但這些卻是在 Rails 和 Django 之後才誕生的（雖然比較起來有點微妙），發展節奏極為快速。我認為，在這個時代誕生，能夠參與並享受像這樣激動人心的 JavaScript 演進浪潮，是非常令人興奮且愉快的事情。

最後，如開頭所述，希望能在本文中解答一些常見疑問，像是「Node.js 不是 Web Server 嗎？只是想用 ES2015 編寫程式碼，為什麼必須安裝呢？」等問題。
