###### tags: `2023鐵人賽` `qiita` `WebAPI`
# [2023 15th鐵人賽] Day20 - 馬上就能使用的免費 Web API 總覽【2023年最新版】

> 原文連結：[今すぐ使える無料WebAPIまとめ【2023年最新版】 - Qiita](https://qiita.com/kazuki_tachikawa/items/7b2fead2a9698d1c15e8)

---

這篇文章整理五十幾項可免費使用的 Web API，種類也是百百種，包括常見的 Google 相關服務、線上支付、識別服務等，依照功能分類如下：

- 工作效率化
- 資料管理
- 翻譯
- 辭典
- 支付服務
- 認證
- 圖像識別
- 語音識別
- 聊天機器人
- 社交軟體
- 音樂
- 天氣
- 線上購物
- 圖像與影像作品
- 書籍
- 位置與交通
- 金融服務
- 狂熱取向

在現代軟體中，Web API 扮演極其重要的角色。如文中所言，光是瞭解到有這些 API 提供的功能存在，或許未來能夠拓展不同的可能性和選擇，在個人開發也能夠發揮其用。

那麼，以下正文開始。

---

[toc]

WebAPI 是將軟體的一部分公開，以 Web 服務的形式，與其他軟體共享功能。通常使用 HTTP 協議進行通訊，通常使用 JSON 或 XML 作為資料交換格式。

因此透過 WebAPI，能夠輕易將所需的功能和資料，編入應用程式或系統中，而不需自己從頭開始開發，即可透過現有的 Web 服務，提供新的功能和服務。

本文介紹一些免費可用的 WebAPI 及其功能，也包括一些有限制的 API，並與其他服務或付費版本進行比較。此外，也提供相關的日文參考資料連結，希望即使是初次使用，也能夠順利引入這些 API。

## 工作效率化

### [Google Sheets API](https://developers.google.com/sheets/api/reference/rest?hl=zh-tw)

- Google Sheets API 可用於讀取和寫入 Google 試算表中的資料
- 可以更改表格格式，或使用 ID 進行管理

> ＜ 參考＞[Google Sheets API を使ってスプレッドシートを操作（使用 Google Sheets API 操作試算表）](https://japan.appeon.com/technical/techblog/technicalblog019/)

### [Google Calendar API](https://developers.google.com/calendar/api/guides/overview?hl=ja)

- 可以用 JSON 格式取得日曆中的事件
- 也可以從外部工具新增預定事件

> ＜參考＞ [Python で Google Calendar API を使ってみた（在 Python 使用 Google Calendar API）](https://www.coppla-note.net/posts/tutorial/google-calendar-api/)

### [Gmail API](https://developers.google.com/gmail/api/guides?hl=ja)

- 可以使用郵件搜索功能以及各種自動化等功能
- 可以根據需求管理大量資料

> ＜參考＞ [Gmail API を用いてメールの送受信を行うAndroidアプリケーションの実装例（使用 Gmail API 在 Android 應用程式中發送和接收郵件的實作範例）](https://www.alpha.co.jp/blog/202211_02)

### [Notion API](https://developers.notion.com/)

- 可以擴展多功能工作區
- 輕鬆新增或刪除資料庫項目

> ＜參考＞ [Notion APIとは？Notion APIを使ってできることや使い方を解説（什麼是 Notion API？解說 Notion API 的功能和使用方法）](https://n-v-l.co/blog/what-is-notion-api)

## 資料管理

### [Evernote API](https://dev.evernote.com/doc/)

- 有 Local 和 Cloud 兩種版本。
- 可以在任何地方編輯已保存的筆記本。

> ＜參考＞ [Evernote API を使ってみる（試著使用 Evernote API）](https://www.antun.net/tips/api/evernote.html)

### [Dropbox API](https://www.dropbox.com/developers/documentation/http/overview)

- 可以統一管理 PDF、音檔、影片等各種內容。
- 使用者管理也非常簡單。

> ＜參考＞ [Dropbox APIで便利ツールを開発してみた（使用 Dropbox API 開發實用工具）](https://blog.usize-tech.com/dropbox-toolbox/)

### [Airtable API](https://airtable.com/developers/web/api/introduction)

- 可以自由操作雲資料庫。
- 無程式碼工具在開發上容易上手。

|  | Free | Team | Business | Enterprise Scale |
| --- | --- | --- | --- | --- |
| 價格（每月） | 無料 | $20/人 | $45/人 | 請洽詢 |
| 記錄 | 1,000 行 | 50,000 行 | 125,000 行 | 500,000 行 |
| 自動執行 | 100 次 | 25,000 次 | 100,000 次 | 500,000 次 |
| 附件 | 1GB | 10GB | 100GB | 1,000GB |

> ＜參考＞ [【Airtableの使い方】ノーコードでデータベース管理をしよう【Airtable 的使用方法】無程式碼管理資料庫](https://nocodejapan.org/media/how-to-use-airtable/#you_liaopuranno_ke_jin_xing_tai)

### [Google Drive API](https://developers.google.com/drive/api/guides/about-sdk?hl=zh-tw)

- 經過驗證後，可以取得 Google Drive 中的訊息。
- 操作共享 Google Drive 非常方便。

> ＜參考＞ [Google Drive API で Google ドライブへアクセス（使用 Google Drive API 取得 Google Drive 權限）](https://japan.appeon.com/technical/techblog/access-google-drive/)

## 翻譯

### [DeepL](https://www.deepl.com/en/pro-api)

- 可以輕鬆使用高精度的翻譯功能。
- 每月最多可免費使用 50 萬個字元。

|  | Free Plan | Pro Plan |
| --- | --- | --- |
| 費用 | 免費 | 基本費用 630 日幣 + 每個字元 0.0025 日幣 |
| 文字數上限 | 50 萬個字元 | 無限制 |
| 安全性 | 標準 | 翻譯後立即刪除文本 |
| 優先處理 | 無 | 有 |

> ＜參考＞ 【[DeepL】APIの登録とサンプルコード実装（【DeepL】註冊 API 和 Sample Code 實作）](https://chigusa-web.com/blog/deepl-api/)

### [Google Translation API](https://cloud.google.com/translate/docs/reference/rest)

- 可以自由操作 Google 翻譯服務。
- 不僅限於文字格式，語音和影片檔案也可以輕鬆進行翻譯。
- 每月最多也可免費使用 50 萬個字元，之後每 1,000,000 個字元將收取 20 美元的費用。（若 1 美元 = 135日幣，則每個字元為 0.0027 日幣）

> ＜參考＞ [Google Translate APIを使って翻訳ボタンを作る（使用 Google Translate API 建立翻譯按鈕）](https://developer.a-blogcms.jp/document/javascript/google-translate-api.html)

### [Translator Text API](https://www.microsoft.com/en-us/translator/business/translator-api/)

- 可以使用 Microsoft 的翻譯服務進行多語言翻譯。
- 免費方案每日可處理 200 萬個字元，與其他服務相比非常吸引人。

> ＜參考＞ [Microsoft Translator テキスト API で、日本語を英語に翻訳するサンプル（使用 Microsoft Translator Text API 將日語翻譯為英語的範例）](https://qiita.com/TakeshiNickOsanai/items/a8039ba8d558f7c8a05e)

## 辭典

### [Words API](https://www.wordsapi.com/)

- 可以取得超過 325,000 個英文單字的意思、類別、用法等資訊。
- 每日免費處理 ~~1000 次~~（2500 次）的請求。

> ＜參考＞ [150,000以上の英単語の意味、類義語などの情報が取得できる「Words API」が公開（可以取得 150,000 個以上英文單字的意思、同義詞等資的「Words API」）](https://codezine.jp/article/detail/8404)

### [Oxford Dictionaries API](https://developer.oxforddictionaries.com/)

- 這是由牛津大學提供支持 35 種語言的 API。
- 可以搜索同義詞及進行翻譯。
- 每日免費處理 1000 次的請求。

> ＜參考＞ [Oxford Dictionaries APIの使い方（Oxford Dictionaries API 的使用方法）](https://qiita.com/Tommyyyyyyy/items/26bf7aae9f464217ad72)

### [COTOHA API](https://api.ce-cotoha.com/contents/about.html)

- 使用大規模的日語辭典，可以取得經詞意分類的單詞資訊。
- 可以應用於文本分析等工具。

|  | Developers | Enterprise |
| --- | --- | --- |
| 費用 | 免費 | 130,000 日幣/月 |
| 使用限制 | 各 API 每日可請求 1000 次 | 無限制 |
| 辭典 | 基本用語辭典 | 基本用語辭典/專業用語辭典 |

> ＜參考＞ [Cotoha API を使ってみた（試著用了 Cotoha API）](https://withcation.com/2019/10/28/post-957)

## 支付服務

### [Stripe API](https://stripe.com/docs/payments/tour)

- 可輕鬆實作線上支付服務。
- 支援 47 個國家，並支援 135 種以上的貨幣和支付方式。
- 交易手續費為 3.6 ％。

> ＜參考＞ [オンライン決済Stripe(ストライプ)を導入するための組み込み方法の基礎（如何實作線上支付 Stripe 的基礎知識）](https://reffect.co.jp/html/stripe/)

### [LINE Pay API](https://pay.line.me/jp/developers/apis/onlineApis?locale=zh_TW)

- 使用者的所有購物行為均在 LINE 上完成。
- 交易手續費為 2.45％。

> ＜參考＞ [LINE Pay APIを使ってアプリに決済を組み込む方法（如何使用 LINE Pay API 將付款合併到應用程式中）](https://qiita.com/nkjm/items/b4f70b4daaf343a2bedc)

### [PayPal API](https://developer.paypal.com/home)

- 可以透過全球使用者眾多的 PayPal 進行支付處理。
- 交易手續費為 2.9％。

> ＜參考＞ [PayPal 決済の実装方法（實作 PayPal 支付的方法）](https://qiita.com/PPJP/items/db5c57991c2c3fe80ac7)

## 認證

### [Github REST API v3](https://docs.github.com/en/rest/overview/about-githubs-apis?apiVersion=2022-11-28)

- 可以取得 Repository 訊息，並進行 Pull Request 等管理。
- 可以使用 GitHub Account 進行使用者身份驗證。

> ＜餐拗＞ [GitHub REST API を使用する - まくまくGitノート（使用 GitHub REST API - まくまく的 Git 筆記）](https://maku77.github.io/git/github/github-rest-api.html)

### [LinkedIn API](https://developer.linkedin.com/product-catalog)

- 可以在 LinkedIn 上，取得主要與職業相關的個人資料資訊。
- 也可以使用 Account 進行身份驗證。

> ＜參考＞ [LinkedIn APIの使い方について（PythonでAPIコール疎通させるまで）（如何使用 LinkedIn API（到使用 Python 呼叫 API））](https://rainbow-engine.com/linkedin-api-howto/)

### [Zoom API](https://developers.zoom.us/docs/api/rest/zoom-api/)

- 可以建立會議，並與外部工具整合管理。
- 也可以取得會議後相關的訊息。

> ＜參考＞ [Zoom APIの設定をしてみよう（如何設定 Zoom API）](https://www.techpit.jp/courses/98/curriculums/101/sections/759/parts/2656)

## 圖像識別

### [Cloud Vision API](https://cloud.google.com/vision?hl=zh-tw)

- 可以使用 Google 的圖像識別 AI。
- 功能包括檢測物體和臉部等多種功能。
- 適用於圖像的功能以「單位」作為計算，每月最多可免費使用 1000 個單位。

> ＜參考＞ [入門ガイド | Cloud Vision API（入門指南 | Cloud Vision API）](https://cloud.google.com/vision/docs/how-to?hl=ja)

### [A3RT](https://a3rt.recruit.co.jp/)

- 由 Recruit 公司提供的機器學習服務，已經在商業上使用。
- 可以使用總共 9 種 API，包括允許圖像和文字互相搜尋的「Image Search API」，以及基於已購買商品進行推薦的「Listing API」。

> ＜參考＞ [リクルートのAI「A3RT」の使い方と活用方法とは？（Recruit 的 AI  「A3RT」的使用方法以及如何應用？）](https://www.pi-pe.co.jp/solution/article/machine-learning/214/)

### [Microsoft Face API](https://azure.microsoft.com/zh-tw/products/ai-services/ai-vision/)

- 可以使用臉部影像進行情感辨識等各種功能，且隱私受到嚴格保護。
- 每月最多免費提供 3 萬筆資料庫交易。

> ＜參考＞ [Face API を使用した感情認識（使用 Face API 進行情感辨識）](https://learn.microsoft.com/ja-jp/xamarin/xamarin-forms/data-cloud/azure-cognitive-services/emotion-recognition)

## 語音識別

### [Google Cloud Speech-to-Text API](https://cloud.google.com/speech-to-text?hl=zh-TW)

- 可以將語音資料轉換為文字逐字稿。
- 例如，在影片加上字幕時非常有用。
- 每月最多可免費使用 60 分鐘。

> ＜參考＞ [Google Cloud Speech-to-Text APIをいろいろ調査してみる（對 Google Cloud Speech-to-Text API 進行各種調查）](https://tech-blog.optim.co.jp/entry/2020/02/21/163000)

### [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)
- 支援多種語言也是一項優勢。
- 由於是瀏覽器的 Native API，因此不需要驗證金鑰。

> ＜參考＞ [Web Speech API（ウェブ音声API）の説明と使い方とサンプルコード【2023】（Web Speech API 的說明、使用方法和範例程式碼【2023】）](https://tech-blog.optim.co.jp/entry/2020/02/21/163000)

## 聊天機器人

### [IBM Watson Assistant](https://www.ibm.com/products/watson-assistant)
- 也提供免費但有限制的使用方案。

|  | Lite | Plus | Enterprise |
| --- | --- | --- | --- |
| 價格 | 免費 | 140 美元/月 | 請直接諮詢 |
| Assistant 數量 | 3 | 10 | 30 |
| 分析資料保存期限 | 7 天 | 30 天 | 最多 90 天 |
| Session Timeout 限制 | 5 分鐘 | 24 小時 | 7 天 |

> ＜參考＞ [Watson Assistantとは？IBMのAIチャットボット開発ツール！メリット・事例を紹介！（什麼是 Watson Assistant？ IBM 的 AI 聊天機器人開發工具！優勢和範例介紹！）](https://aismiley.co.jp/ai_news/ibm-watson-assistant/)

### [LINE Messaging API](https://developers.line.biz/zh-hant/services/messaging-api/)
- 也支援發送圖片、影片、音頻等多媒體內容。
- 在免費方案中，每月可以發送 200 條消息。

|  | Communication Plan | Lite Plan | Standard plan |
| --- | --- | --- | --- |
| 月額固定費（税別） | 0 日幣 | 5,000 日幣 | 15,000 日幣 |
| 免費消息數量（每月） | 200 條 | 5,000 條 | 30,000 條 |
| 額外消息費用（不含稅） | 不適用 | 不適用 | ～3 日幣/條 |

> ＜參考＞ [LINEでメッセージの送受信を行おう！ Messaging APIの基本的な使い方から解説（在 LINE 上接收與發送訊息！解說 Messaging API 的基本使用方式）](https://codezine.jp/article/detail/17654)

### [Discord API](https://discord.com/developers/docs/intro)

- 可以自由實作觸發事件及其處理。
- 可以建立具有各種功能的聊天機器人。

> ＜參考＞  [Pythonで実用Discord Bot(discordpy解説)（使用 Python 的實用 Discord Bot（discordpy 解說））](https://qiita.com/1ntegrale9/items/9d570ef8175cf178468f)

### [Slack API](https://api.slack.com/)

- 可以將自訂的聊天機器人加到頻道中。
- 可以輕鬆與外部工具整合，並用來發布訊息。

> ＜參考＞ [Slack API を使用してメッセージを投稿する（使用 Slack API 發布訊息）](https://zenn.dev/kou_pg_0131/articles/slack-api-post-message)

## SNS 社交軟體

### [Qiita API](https://qiita.com/api/v2/docs)

- 可以使用 API 管理熟悉的 Qiita 文章。
- 這在分析存取資料和趨勢分析等工作時不可或缺。

> ＜參考＞ [Qiita APIとPythonを用いてQiitaのデータを取得してみる（試著用 Qiita API 和 Python 取得 Qiita 資料）](https://harinez2.hateblo.jp/entry/qiita_api_by_python)

### [Instagram API](https://developers.facebook.com/products/instagram/apis/)

[Instagram APIs | Facebook for Developers](https://developers.facebook.com/products/instagram/apis/)

- 使用基本顯示 API，可以取得個人資料訊息，有助於簡化登入流程等。
- 使用需要 Business Account 的 Graph API，可以自動發布內容和建立聊天機器人。

> ＜參考＞ [Instagram Graph APIの使い方・認証手順｜アクセストークン・アプリ・インスタビジネスアカウントID取得（Instagram Graph API 的使用方式和身份驗證步驟｜取得 Access Token、APP、Instagram Business Account ID）](https://di-acc2.com/system/rpa/19280/#index_id1)

### [YouTube Data API](https://developers.google.com/youtube/v3)

[YouTube Data API  |  Google for Developers](https://developers.google.com/youtube/v3)

- 可以取得觀看次數和高評分等與影片相關的資訊。
- 可以分析自己發布的內容。
- 如果想要增加每天的使用上限，則需要透過表格提交申請。

> ＜參考＞ [YouTube APIの使い方とブラウザだけでデータ取得する方法（YouTube API 的使用方法，以及只透過瀏覽器取得資料的方法）](https://diy-programming.site/tools/movie-matome-site-3/)

### [Twitch API](https://dev.twitch.tv/docs/api/)

- 可以取得與 Twitch 上正在直播的內容相關的資訊。
- 可以輕鬆掌握正流行的遊戲。

> ＜參考＞ [Twitch API をPythonで使うメモ（以 Python 使用 Twitch API 的筆記）](https://vatchlog.com/twitchapi-python-memo/)

## 音樂

### [Spotify Web API](https://developer.spotify.com/documentation/web-api)

- 提供使用者查詢音樂庫中的歌曲和播放清單等相關資料。
- 喜歡的歌曲可以用毫秒為單位分析。

> ＜參考＞ [Spotify APIで楽曲の分析データを取得する方法（使用 Spotify API 取得音樂分析資料的方法）](https://gaaaon.jp/blog/spotify)

### [Apple Music API](https://developer.apple.com/documentation/applemusicapi/)

- 可以搜尋與再生歌曲。
- 將有助於開發 IOS 應用程式。

> ＜參考＞ [[iOS 11] Apple Music APIを使用してアルバム検索アプリを作る（[iOS 11] 使用 Apple Music API 建立專輯搜尋應用程式）](https://dev.classmethod.jp/articles/ios-11-apple-music-api-search/)

## 天氣

### [OpenWeatherMap API](https://openweathermap.org/api)

- 可以取得未來 5 天的天氣預報。
- 在付費方案中，可以取得詳細的降雨預測圖像。

> ＜參考＞ [世界の天気API「OpenWeatherMap」の無料APIキー発行・取得、リクエスト方法（取得世界各地的天氣 API「OpenWeatherMap」的免費 API 密鑰和請求方法）](https://auto-worker.com/blog/?p=1612#)

### [Free Weather API](https://www.weatherapi.com/)

- 可以取得全即時天氣資料和天氣預報。
- 每月可免費執行 100 萬次。

> ＜參考＞ [無料で使える天気API「Free Weather API」の利用登録とキー発行手順（可免費使用的天氣 API「Free Weather API」的註冊和密鑰生成流程）](https://hibi-update.org/other/openweathermap-api/)

## 線上購物

### [Rakuten API](https://webservice.rakuten.co.jp/documentation)

- 可以取得與樂天網站有關的各種資訊。
- 涵蓋樂天市場的商品資訊、旅行計劃和食譜等各種方面。

> ＜參考＞ [無料で使える、楽天APIを使ってみよう！（試試免費的樂天 API！）](https://blog.frankul.net/2022/03/30/rakuten-api/)

### [Amazon Product Advertising API](https://affiliate.amazon.co.jp/?isLanguagePreferenceFailed=false)

- 這是用於聯盟式營銷的 API。
- 可以訪問 Amazon 大量的商品資訊。

> ＜參考＞ [【初心者向け】Amazon Product Advertising API（PA-API v5）の使い方と必要な作業（【初學者指南】Amazon Product Advertising API（PA-API v5）的使用方法和所需步驟）](https://wporz.com/amazon-product-advertising-api-pa-api-5-0/)

### [Yahoo Shopping API](https://developer.yahoo.co.jp/webapi/shopping/)

- 可以取得 Yahoo 網站上的商品訊息。
- 可以輕鬆參考日語的商品評論是一大優勢。

> ＜參考＞ [【プログラミング初心者でも大丈夫】Yahoo APIを使ってみよう（【程式初學者也可以】試試使用 Yahoo API）](https://blog.codecamp.jp/yahoo-api-programming)

## 圖像・影片作品

### [Pinterest API](https://developers.pinterest.com/)

- 可以自動建立與圖像相關的 Pin 和 Board。
- 也提供用於連結產品資訊用的購物 API。

> [＜參考＞ わずか数行のコードで利用できちゃう！Pinterest APIを活用してみた。（只需幾行程式碼即可使用！試著用了 Pinterest API。）](https://liginc.co.jp/349973)

### [Tmdb API](https://developer.themoviedb.org/docs)

- 可以取得已公開電影的相關資訊，包括劇情簡介和海報圖片。
- 作品可依類別分類，非常方便。

> ＜參考＞ [TMDb API を利用して映画のポスターやあらすじを自分のサイトに表示する（利用 TMDb API 在自己的網站上顯示電影海報和劇情簡介）](https://chocolat5.com/ja/tips/tmdb-api/)

### [NHK 節目表 API](https://api-portal.nhk.or.jp/)

- 透過指定地區、服務和日期，可以取得符合條件的節目列表。
- 可以自動抓取關鍵字，找出觀眾感興趣的相關節目資訊。

> ＜參考＞ [NHK番組表APIを使ってキーワード監視と通知（使用 NHK 節目表 API 監視關鍵詞和通知）](https://edgeknocker.blogspot.com/2019/06/nhkapi.html)

## 書籍

### [Google Books API](https://developers.google.com/books)

- 除了作者、書名等書籍資訊，也能取得論文的相關資料。
- 每日請求上限為 1000 次。

> ＜參考＞ [書籍検索APIのGoogle Books APIsの使い方（PHPでのサンプルコードあり）（使用 Google Books API 檢索書籍的方法（附有 PHP 範例程式碼））](https://edgeknocker.blogspot.com/2019/06/nhkapi.html)

### [國立國會圖書館檢索 API](https://iss.ndl.go.jp/information/api/riyou/)

- 能夠查詢國立國會圖書館所藏圖書的訊息。
- 國內書籍基本上都有相關資訊。

> ＜參考＞ [国立国会図書館サーチ APIを使ってみる（試著用了國立國會圖書館搜尋 API）](https://qiita.com/saoyagi2/items/5c23550b0a00933386a6)

### [圖書館 API](https://calil.jp/doc/api.html)

- 透過指定經度和緯度，可以取得距離該地點最近的圖書館資料。
- 此外，也可以查看有無藏書和借閱狀況的資訊。

> ＜參考＞ [【python】カーリルAPIで図書蔵書情報を取得する（使用 Python 透過 Calil API 取得圖書館藏書資訊）](https://boook24.com/?p=1562)

## 位置・交通

### [郵遞區號檢索 API](http://zipcloud.ibsnet.co.jp/doc/api)

- 可以透過郵遞區號搜索地址。
- 可以應用於 EC 網站等自動填寫功能。

> ＜參考＞ [【JavaScript】郵便番号検索APIで住所検索を実装する（【JavaScript】實作郵遞區號檢索 API 來搜索地址）](https://into-the-program.com/javascript-get-address-zipcode-search-api/)

### [Google Maps API](https://developers.google.com/maps/)

- 可以在瀏覽器中顯示 Google 地圖。
- 有許多日語的文件，有助於順利實作。

> ＜參考＞ [Google Maps API を使ってみた（嘗試使用Google Maps API）](https://qiita.com/Haruka-Ogawa/items/997401a2edcd20e61037)

### [駅すぱあとWeb 服務](https://docs.ekispert.com/v1/api/)

- 可以取得與公共交通資訊和轉乘指南有關訊息。
- 對於查詢最近的車站，或搜尋通往目的地的路線都不可或缺。

> ＜參考＞ [駅すぱあとWebサービスフリープランを利用する（使用駅すぱあと Web 服務的免費方案）]()

### [NAVITIME API](https://api-sdk.navitime.co.jp/api/)

- 搜索車輛導航路線非常方便。

|  | BASIC | PRO |
| --- | --- | --- |
| 月費金額 | 免費 | $200 |
| 請求限制 | 50次/分 | 100次/分 |

### [Hot Pepper API](https://webservice.recruit.co.jp/doc/hotpepper/reference.html)

- 可以取得餐廳的名稱和 URL 資訊。
- 可以搜索位置資訊等詳細資料。

> ＜參考＞ [pythonでホットペッパーのAPIを叩いてみた（使用 Python 串接 Hot Pepper API）](https://web-tweets.com/python/hotpepper-api/)

## 金融服務

### [Yahoo Finance API](https://developer.yahoo.com/api/?guccounter=1)

- 可以取得開盤價、最高價、最低價和收盤價等股票相關資料。
- 也可以輕鬆指定日本的股票。

> ＜參考＞ [yfinance API を使って株のデータを取得する（使用 yfinance API 取得股票相關資料）](https://web-tweets.com/python/hotpepper-api/)

### [交易所 API](https://coincheck.com/ja/documents/exchange/api)

- 在不需身份驗證的 Public API，可以取得交易所的訂單狀態和歷史記錄等資訊。
- 若使用 Private API，可以使用查詢訂單等自動交易的功能。

> ＜參考＞ [【Python】コインチェックAPIの取得と自動売買の実践手順｜Coincheck仮想通貨・ビットコイン取引機能入門（【Python】使用 Coincheck API 實際進行交易的步驟｜Coincheck 虛擬貨幣和比特幣交易功能入門）](https://di-acc2.com/programming/python/15316/)

## 狂熱取向

### [Poke API](https://pokeapi.co/)

- 可以取得寶可夢的名稱、類型、可學技能以及遊戲內物品相關的資訊。
- 需注意所有內容都以英語表示。

> ＜參考＞ [PokeAPIの使い方【初心者向け】（PokeAPI 的使用方法【初學者專用】）](https://taiyosite.com/pokeapi-elementary/)

### [Official Joke API](https://github.com/15Dkatz/official_joke_api)

- 隨機取得笑話。
- 由紮實的鋪墊和結尾組成。 
- 也就是所謂的美式笑話。

> ＜參考＞ [【随時更新】一風変わったWeb APIをまとめてみた（【定期更新】整理一些不同尋常的 Web API）](https://qiita.com/danishi/items/42d8adf6291515e62284)

### [Marvel API](https://developer.marvel.com/)

- 可以取得 Marvel 相關漫畫角色的圖像和故事內容。
- 可以輕鬆建立簡單的測驗網站等。

> ＜參考＞ [【アメコミ】マーベルAPIでカッコいいサイトを作ろう！（【美漫】使用 Marvel API 建立酷炫網站！）](https://webdev-bodymake.com/marvel-api/)

### [NASA API](https://api.nasa.gov/)

- 主要可以取得行星資訊和衛星圖像。
- 在考慮遷居太空時，或許派得上用場。

> ＜參考＞ [NASAのAPIを使ってみる（嘗試用了 NASA 的 API）](https://note.com/sk_game_theory/n/ne8461ef4dc8d)

## 總結

在現代軟體中，Web API 扮演極其重要的角色。僅僅瞭解這些存在和功能，或許就能擴大的可能性和選擇。

以上介紹的大多數 API 都適用於個人開發。對於希望建立新服務的人來說，這些 API 將成為極具質量和便利性的有力幫手。

在弊公司 Nuco，也發布了各種實用文章。如果感興趣，請隨時查看 [Organization](https://qiita.com/organizations/nuco-inc) 頁面。此外，Nuco 也正在招募志同道合的夥伴！請[參閱這裡](https://www.recruit.nuco.co.jp/?qiita_item_id=7b2fead2a9698d1c15e8)。
