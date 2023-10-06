###### tags: `2023鐵人賽` `qiita` `Design` `Front-End`
# [2023 15th鐵人賽] Day21 - 日本數位廳的網站太扯了www

> 原文連結：[デジタル庁のサイトやばすぎるwww - Qiita](https://qiita.com/mu_tomoya/items/f78f1fad3a8b57ac7dc3)

> [デジタル庁（數位廳 ）](https://zh.wikipedia.org/zh-tw/%E6%95%B8%E4%BD%8D%E5%BB%B3)：因應 COVID-19 疫情，日本政府於 2021 年 9 月 1 日成立數位廳（Digital Agency），欲將政府陳舊的服務系統與記錄保存進行技術升級，並訂定相關組織、法規與政策，致力打造數位社會（デジタル社会）與產業的數位轉型（DX，Digital Transformation）。

其實第一點看到標題的****やばすぎ****，也就是各位熟知「超牙敗」（？），現代常用來表示「感覺不妙、意外地驚喜」等含義，本來以為這篇文章應該是想 diss 政府網站，畢竟やばい其實有點貶義的意味，沒想到實則驚嘆網站使用的是 Modern 技術與設計，以及進行分析。

關於具前衛風格的網站設計在日本的接受度，之前翻譯的這篇討論也有稍微提到：[[Day12] 外國「為什麼日本無法像硬體時代一樣在軟體方面表現出色？」](https://heidiliu2020.github.io/ironman-2023-day-12/) 

簡單來說，日本普遍消費者的喜好偏保守，導致許多日本網站，至今仍維持包含大量文本與閃爍橫幅的傳統設計，因此對於數位廳網頁的簡約風設計，評價還是很兩極。

也因此，不管是在這篇文章底下的討論串，還是在推特上，同樣有持兩派不同意見的人存在。不論是對於本篇文章的聳動標題，或對數位廳的極簡約設計，儘管為了爭取關注與討論度，還是採用新的技術與設計改革，得到的評價仍褒貶不一。但能肯定的是，透過這些方式，能夠確切體會到政府網站的變革。

那麼，以下正文開始！

---

[toc]

## 前言

各位是否已經看過數位廳的網站了？這是近期成為討論話題的[數位廳（デジタル庁）](https://www.digital.go.jp/)：


![](https://hackmd.io/_uploads/Bybv2B9ea.png)

這是截至 2023 年 6 月的數位廳網站。這不會太扯了嗎？當我第一眼看到時，忍不住心想「哇靠w」。接下來，我想談談這個網站究竟是哪裡令人感到驚訝。

## 俐落的簡潔性，以及設計

當我第一次看到網站時，感到非常驚訝。 「太簡單易讀了吧！」這是政府網站吧？提到政府機構的網站時，多數人可能會有這樣的印象，排滿難以閱讀的小字，但數位廳的網站竟如此貫徹簡潔性且易於閱讀。使用的字體是容易閱讀的 Noto Sans JP。黑色也不再是 `#000`，而是一種好看的顏色。這也太讚了吧。
接下來，當我看到這個佈局時，我認為因為有留白，所以能夠更容易閱讀。使用 Chrome Dev Tool 來查看佈局時，發現到：

![](https://hackmd.io/_uploads/SJGs6Sqe6.png)

竟然採用 **12-Column [Grid Design](https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout)（ 12 列[格線設計](https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout)）**！ ！ ！而且是 CSS Grid！這是我第一次看到像這樣漂亮使用 12 列格線設計的網站。 

有關 Grid Design 的詳細資訊可以參考：

[最新版、レスポンシブ対応のレイアウト・グリッドデザイン徹底解説](https://coliss.com/articles/build-websites/operation/work/responsive-grid-design-ultimate-guide.html)

再進一步觀察設計時，發現配色簡單，再加上清晰的對比，對於色弱的使用者而言較為友善的設計。
繼續仔細研究，發現數位廳發布了一個設計系統（Design System），而該設計系統也有發佈在 Figma 上：

[デザインシステム｜デジタル庁](https://www.digital.go.jp/policies/servicedesign/designsystem/)

![](https://hackmd.io/_uploads/r1SlRScgp.png)

我認為設計被大量地用語言表達是很容易理解的。

內容非常詳盡且易於理解，還可以免費閱讀。當中解釋為什麼這樣設計，這對於任何從事 Web Design 的人來說都很值得一讀。比起飽讀許多設計書籍，或許閱讀這個設計系統更能夠提升設計能力。將設計相關的內容大篇幅以語言表達這點，非常有助於理解。

在閱讀過程中，可以發現在如何減輕使用者負擔方面，花費許多心思，看到這裡實在抬不起頭來。雖然這麼說可能有點失禮，但確實讓我意識到，這個網站是由專業的 Web Designer 所設計的。

除此之外，在其他頁面有介紹到 [Web Accessibility（無障礙網頁）](https://developer.mozilla.org/zh-TW/docs/Web/Accessibility)：

[ウェブアクセシビリティ｜デジタル庁](https://www.digital.go.jp/accessibility-statement/)

[「誰一人取り残されない」を高い水準で叶えるために。ウェブサイトのアクセシビリティ検証結果と、その後｜デジタル庁](https://digital-gov.note.jp/n/nb2da6ba21829)

網站的 Web Accessibility 似乎符合 [JIS（日本產業規格）](https://zh.wikipedia.org/zh-tw/%E6%97%A5%E6%9C%AC%E7%94%A2%E6%A5%AD%E8%A6%8F%E6%A0%BC) 標準，也有發佈檢驗結果。老實說，如果必須考慮到這個程度，可能會對這個網站感到反感，但數位廳的網站在這點卻做得非常徹底。

> 數位廳的目標是「實現一個不讓任何人落後，且人性化的數位社會」。

是很棒的想法，而這正是體現這個說法的 Web Design。此外，網站還有提供 Web Accessibility 功能實現指南，數位廳太慷慨了⋯⋯

[ウェブアクセシビリティ導入ガイドブック｜デジタル庁](https://www.digital.go.jp/resources/introduction-to-web-accessibility-guidebook/)

共計 56 頁的[超豐富 PDF](https://www.digital.go.jp/assets/contents/node/basic_page/field_ref_resources/08ed88e1-d622-43cb-900b-84957ab87826/590253d4/20230124_introduction_to_weba11y.pdf)。這些內容都是可以免費閱讀的喔？

## 採用現代前端開發技術

![](https://hackmd.io/_uploads/r1jTavhep.png)

透過可以大略檢查 Web 網站使用何種技術的工具 [wappalyzer](https://chrome.google.com/webstore/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg) 查看時，忍不住懷疑這真的是政府機關的網站嗎，使用的竟然是現代技術。

值得關注的技術棧採用 Next.js、S3、CloudFront。在眾多使用 jQuery 或 WordPress 製作的網站當中，使用 Next.js 技術開發的政府網站實在令人驚訝。

<!-- ![](https://hackmd.io/_uploads/BJpqAw2gT.png =400x) -->

<img src="https://hackmd.io/_uploads/BJpqAw2gT.png " width="400">

<!-- ![](https://hackmd.io/_uploads/rkz2Av2e6.png =400x) -->

<img src="https://hackmd.io/_uploads/rkz2Av2e6.png" width="400">

> [推文連結](https://twitter.com/chibicode/status/1629307668568633344)

或許是使用 Next.js 的 [SSG（Static Site Generation）](https://nextjs.org/docs/pages/building-your-application/rendering/static-site-generation) 功能，將靜態網站部署到 S3，並透過 CDN [CloudFront](https://aws.amazon.com/tw/cloudfront/) 服務以快速交付網站，因此**網頁顯示速度非常快**。這真的不簡單，我認為甚至比[阿部寬的個人官方網站](https://news.gamme.com.tw/1693973)還要快，因為頁面轉換非常流暢，能夠在點擊之前就顯示完成。

![](https://hackmd.io/_uploads/ryzA0B9eT.png)

[PageSpeed Insights](https://pagespeed.web.dev/)（測試網站速度的工具）的結果也相當不錯。能夠有具備紮實前端相關知識的人在數位廳任職真是太好了。

## 最後

<!-- ![](https://hackmd.io/_uploads/S191LR2e6.png =400x) -->

<img src="https://hackmd.io/_uploads/S191LR2e6.png" width="400">

> [推文連結](https://twitter.com/333mimina/status/1667276026064392195)

之所以會撰寫這篇文章，原因是有些人明明對技術一無所知，卻嘲笑說「這種東西就算是業餘的也能做到w」，讓我感到非常惱火。

確實最近數位廳在 My Number 相關事務上有些混亂，能夠理解會對河野大臣感到憤怒。然而，若因此憎其人而及其物，**連同嘲笑那些在數位廳工作的人，那可就大錯特錯**。數位廳的網站是如此追求極簡風格和通用性，透過閱讀設計相關的內容也受益匪淺，看似簡單的外表，實則隱藏相當多的技術。

就我個人而言，我非常支持數位廳的努力。強烈希望藉由數位廳的力量，能夠讓日本成為全國工程師辛勤工作能夠得到回報的地方。

## 後記

6/29 更新
看來數位廳的網站預計更新，並且已經發布了試用版。已經新增一篇相關文章，有興趣的話可以在這閱讀：**[またまたデジタル庁(試行版)のサイトが見やすすぎな件について](https://qiita.com/mu_tomoya/items/dd05c2906ee18a041111)。**

6/14 更新
原本希望在這篇文章傳播之前就寫下來，雖然可能已經晚了，但我會將更多觀察到的內容補足。

以下是數位廳充實的 note（類似日本版的方格子）：

[デジタル庁](https://digital-gov.note.jp/)

[デジタル庁Data strategy team: Digital Agency, Gov of JP](https://data-gov.note.jp/)

[デジタル庁 ガバメントクラウド](https://cloud-gov.note.jp/)

「數位廳」的 note 非常詳細地介紹數位廳的組成。

「數位廳  Data strategy team」撰寫與資料管理以及國外資料策略有關的文章。雖然我自己本身不是這方面的專家，但內容解釋非常清楚，有時間的話也請閱讀看看。

接下來，這裡是對於 **Web 工程師的初學者、後端、前端、基礎設施等而言必看的內容**「**ガバメントクラウド（政府雲端）**」。為了瞭解政府雲端是什麼，閱讀內容時發現這是一個與 Web 相關的技術部落格，我心想「哇，寫得這麼詳細啊？」，每篇文章都解釋得非常詳細且容易理解

這裡舉出其中一個例子：

[マネージドサービス、コンテナ、サーバレス｜デジタル庁 ガバメントクラウド](https://cloud-gov.note.jp/n/n1493ba81131f)

除此之外，也應該閱讀過所有文章，特別是對於即將成為工程師的初學者。不，說真的，對於目前的趨勢 IaC（Infrastructure as Code = 基礎設施即為程式碼）、容器、Serverless、Web API、前端靜態站點生成架構、基礎設施配置、監控運維等技術主題，均有進行深入淺出的講解。 忍不住想吐槽這些人是在超酷炫的新創公司上班的程度，對技術是如此真誠，數位廳也傳達著這樣的訊息，這點真的很厲害。

這篇政府雲端，文章結構真的很不錯，不僅是介紹技術相關的知識，還徹底講解其優缺點，該如何應用政府雲端，未來需要改進的部分，內容撰寫非常透徹。

如果對數位廳的 note 內容有認同感，請務必在 SNS 上分享 note，或是在 note 上點讚。這些是有價值的技術知識，應該傳播給更多的工程師，甚至還包含使用範例，真的超讚。

## 來源

デジタル庁 [https://www.digital.go.jp](https://www.digital.go.jp/)
