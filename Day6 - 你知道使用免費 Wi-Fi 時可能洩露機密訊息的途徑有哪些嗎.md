###### tags: `2023鐵人賽` `qiita` `Security`
# [2023 15th鐵人賽] Day6 - 你知道使用免費 Wi-Fi 時可能洩露機密訊息的途徑有哪些嗎

> 原文連結：[フリーWi-Fiを使ったら秘密情報を抜かれる経路にはどのようなものがあるか - Qiita](https://qiita.com/ockeghem/items/c6a3602d2c2409f89fbb)

常聽聞免費 Wi-Fi 可能暗藏資安危機，究竟原理是如何、可能造成什麼影響，又該如何預防等等，本文將針對這個主題進行介紹。

以下正文開始！

---

[toc]

這是在黃金週的開始（4月29日）發布的推文，截至 5 月 7 日晚上 8 點，已經累積 1938.8 萬次觀看次數，顯然引起很大的關注。

![](https://imgur.com/Y6fmxhU.png)
> 我叫阿席達卡！我在星巴克使用免費 Wi-Fi 處理公司的機密資訊時，結果訊息全部外洩了。我該怎麼辦才好！（[原推文連結](https://twitter.com/MacopeninSUTABA/status/1652315366373363712?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1652315366373363712%7Ctwgr%5E2c16a5f2b4ce1e803944ce9626b5cd01872c2696%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fpublish.twitter.com%2F%3Fquery%3Dhttps3A2F2Ftwitter.com2FMacopeninSUTABA2Fstatus2F1652315366373363712widget%3DTweet)）

對此，我發布了以下的推文，同樣也吸引不少關注，累積 124.1 萬次的觀看次數。雖然收到了許多反饋，但卻是出乎意料的難題，我打算在黃金週結束後，接著介紹幾種可能的訊息洩漏途徑。

![](https://imgur.com/HfFt9JH.jpg)
> 應該把這當作入職考試題目嗎？請說明「在星巴克使用免費 Wi-Fi 處理公司機密資訊時，導致所有訊息外洩的情況」在現實中可能導致的威脅。我認為這問題相當具有挑戰性。（[原推文連結](https://twitter.com/ockeghem/status/1652673176852381696?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1652673176852381696%7Ctwgr%5E93dbce41dc3f650fa633b1ba21c2c42cd022baa3%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fqiita.com%2Fockeghem%2Fitems%2Fc6a3602d2c2409f89fbb)）

## 針對無線區域網路的攻擊

由於背景是以「在星巴克使用免費 Wi-Fi 時」為前提，這裡會解釋有關無線區域網路（Wireless LAN）所帶來的威脅。一般來說，當提到無線 LAN 的威脅時，多數人會先想到「未加密的無線 LAN」，然而實際上，許多免費 Wi-Fi 也存在「即使有加密也能被竊聽」的問題。原因是無線 LAN 的密碼（預共享金鑰 PSK、密碼短語 Passphrase）已經被公開。以下文章可作為參考：

[パスワードが公開された公衆無線LAN、暗号化されていても盗聴できる？ | 日経クロステック（xTECH）](https://xtech.nikkei.com/it/atcl/column/17/090600370/091100008/)

此外，還存在偽造存取點（Fake Access Point）的威脅，意即攻擊者偽裝成咖啡廳的 Wi-Fi 存取點。設置與真正存取點相同的 SSID 和密碼的偽造存取點，被稱作孿生惡魔（Evil Twin, [英語版WikiPedia](https://en.wikipedia.org/wiki/Evil_twin_(wireless_networks))），對使用者來說難以區分真偽，因此構成嚴重的威脅。以下是以咖啡廳 Wi-Fi 為例，說明偽造存取點帶來的威脅（見下圖）。

![Fake AP](https://imgur.com/7jip5n8.png)

在偽造存取點的情況，可在上圖中的有線 LAN 區段進行竊聽，因此與無線加密無關。此外，也可能出現[中間人攻擊](https://zh.wikipedia.org/zh-tw/%E4%B8%AD%E9%97%B4%E4%BA%BA%E6%94%BB%E5%87%BB)（man-in-the-middle attack; MITM），使攻擊的種類更加多樣。

在任何情況下，如果通訊路徑是透過 HTTPS（TLS）加密的話，通訊內容就不容易被竊聽。但如果網站存在漏洞，或使用者的使用方式不正確，仍有可能會洩露通訊內容。

## 未使用 HTTPS 進行連線

如果使用的網站不支援 HTTPS，或即便網站支援 HTTPS，但使用者仍使用 HTTP 進行連線，那通訊內容還是會透過上述方法被全部竊聽。

現今已經很少有網站不使用 HTTPS，但仍有可能被引導至 HTTP 以進行中間人攻擊。在下方影片中，展示了某家[巨型銀行](https://zh.wikipedia.org/zh-tw/%E5%B7%A8%E5%9E%8B%E9%8A%80%E8%A1%8C)的線上銀行網站，被進行中間人攻擊漏洩了通訊內容。雖然該網站將 HTTP 通訊重新轉向至 HTTPS，但攻擊者仍避開並進行攻擊。即使網站關閉了 TCP 80 port，仍有機會進行此攻擊。詳細內容請信請參考下方影片。

<iframe width="560" height="315" src="https://www.youtube.com/embed/k0xBCjWPqcU?si=B_eV6MZo-8uELjAG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

針對這種攻擊的防範措施，如下所示：

- 網站端：通過設定 [HSTS（Strict-Transport-Security）](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security)以強制使用HTTPS
- 使用者端：確認使用 HTTPS 進行連線

## 已連接 https URL 卻忽略瀏覽器的警告

即便使用者透過 HTTPS 進行連線，如果攻擊者使用類似 [Burp Suite](https://zh.wikipedia.org/zh-tw/Burp_suite) 的 MITM Proxy 的情況，則可透過 Burp Suite 將 HTTPS 解密再重新加密，藉此盜取通訊內容。但在這種情況下，瀏覽器將會顯示錯誤，除非使用者強制忽略警告，否則通訊無法進行。在上述影片中，也展示了這種情況。 

針對這種攻擊的防範措施，如下所示：

- 網站端：透過設定 [HSTS（Strict-Transport-Security）](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security)使憑證錯誤無法被忽略
- 使用者端：當瀏覽器出現憑證錯誤時即停止使用

在上述影片所介紹的巨型銀行就未設定 HSTS。

![](https://imgur.com/R6Q9t8C.jpg)

## 使用特定 APP 而非瀏覽器，但該 APP 存在漏洞並且未經過憑證授權

在透過手機 APP 而非瀏覽器使用服務的情況，檢驗憑證將成為 APP 方的責任。有時 APP 方檢驗憑證不夠嚴謹，可能導致訊息被竊取。以下是筆者發現的一個例子。

[Android版KindleにおけるSSLサーバ証明書の検証不備の脆弱性CVE-2014-3908 | 徳丸浩の日記](https://blog.tokumaru.org/2014/09/androidkindlesslcve-2014-3908.html)

針對這種情況的防範措施，如下所示：

- 提供者端：透過對手機 APP 掃描是否存在漏洞，確保檢驗憑證
- 使用者端：使用可信賴的 APP，或在使用 APP 時改用行動數據通訊

## 在伺服器允許使用脆弱的加密演算法可能造成漏洞

TLS/SSL 的規格或實作上有時存在著脆弱性。其中代表性的例子是 POODLE 弱點。詳細請參考はるぷさん的文章說明。

[SSL v3.0の脆弱性「POODLE」ってかわいい名前だけど何？？ | BLOG - DeNA Engineering](https://engineering.dena.com/blog/2014/10/poodle/)

正如這篇文章提及，POODLE 攻擊是藉由 MITM，透過咖啡廳的偽造存取點攻擊是典型案例。換句話說，在沒有 MITM 風險的環境中，就不存在 POODLE 的實際威脅，因此針對 POODLE 的威脅，SSL 協議已被停用。

以下是應對措施：

- 網站端：僅允許 TLS 1.2 以上版本，實作 SSL （OpenSSL 等）並隨時更新至最新狀態
- 使用者端：使用最新版的瀏覽器（最新的瀏覽器已停用 SSL）

## Cookie 缺少 Secure 屬性

由於 Web 應用程式的存在弱點，可能在通訊過程中被竊取內容。其中代表性的例子是 Cookie 缺少的 Secure 屬性的情況。換句話說，若 Set-Cookie 未添加 Secure 屬性，可能會使 Cookie 在明文通訊時被竊聽。

詳細內容請參考下方部落格文章和影片：

[HTTPSを使ってもCookieの改変は防げないことを実験で試してみた | 徳丸浩の日記](https://blog.tokumaru.org/2013/09/cookie-manipulation-is-possible-even-on-ssl.html)

<iframe width="560" height="315" src="https://www.youtube.com/embed/yXNOJE9kGK8?si=UXFoHFJWZoBDWaal" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

網站端的應對措施如下，Cookie 缺少的 Secure 屬性經常在弱點檢測中被診斷出。

- 在 Cookie 設定 Secure 屬性（根本解決方案）
- 設定 HSTS（緩解措施）

使用者端的應對措施較為困難，以下提供一些可用措施：

- 使用可信任的網站
- 避免使用公共無線網絡

## Session ID 固定攻擊（Session Fixation）

有一種攻擊手法被稱為「Session ID 固定攻擊」。詳細內容請參考下方文章：

- [安全なウェブサイトの作り方 - 1.4 セッション管理の不備 | 情報セキュリティ | IPA](https://www.ipa.go.jp/security/vuln/websecurity/session-management.html)
- [とくまるひろしのSession Fixation攻撃入門 | 徳丸浩の日記](https://blog.tokumaru.org/2009/01/introduction-to-session-fixation-attack.html)

在這種攻擊中，必須達成「攻擊者預先透過某種方法，將準備好的 Session ID 傳送給使用者」這項步驟。也就是說，攻擊者必須將準備好的 Cookie 傳給使用者。可能有不少人會認為「這種事有可能嗎」，透過 MITM 是有可能實現的。以下文章和影片將會進行說明：

[HTTPSを使ってもCookieの改変は防げないことを実験で試してみた | 徳丸浩の日記](https://blog.tokumaru.org/2013/09/cookie-manipulation-is-possible-even-on-ssl.html)（再發表）

<iframe width="560" height="315" src="https://www.youtube.com/embed/GP1eEit1quY?si=8MYCJXMnPYxe6Z3z" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

網站端的應對措施如下：

- 為防止 Session ID 固定，可在登入後立即更改 Session ID（根本解決方案）
- 使用 Cookie 的前綴詞（參考 [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)）（緩解措施）
- 設定 HSTS（緩解措施）

另一方面，一般使用者較難發現 Session ID 固定這項弱點，因此使用者端的應對措施較為有限：

- 使用可信任的網站
- 避免使用公共無線網絡

雖然 Session ID 固定這項弱點近來較少見，但在弱點分析中偶爾會被診斷出。

## 設定檔案共享

Windows 有項名為 [Network Profile（網路配置文件）](https://support.microsoft.com/zh-tw/windows/%E5%9C%A8-windows-%E4%B8%AD%E5%B0%87-wi-fi-%E7%B6%B2%E8%B7%AF%E8%A8%AD%E7%82%BA%E5%85%AC%E7%94%A8%E6%88%96%E7%A7%81%E4%BA%BA-0460117d-8d3e-a7ac-f003-7a0da607448d)的功能，可設定為 Public 或 Private。在使用公共無線網絡時，必須將其設定為 Public。若誤設為 Private，可能存在以下威脅：

> 在公共場所使用無線網絡時，如果啟用這個檔案共享功能，電腦或智慧型手機內的檔案就有可能被他人讀取，或被發送病毒等惡意檔案。因此在公共場所使用無線網絡時，請務必停用檔案共享功能。
引用自[無線LANの安全な利用｜基本的な対策｜一般利用者の対策｜国民のための情報セキュリティサイト](https://www.soumu.go.jp/main_sosiki/joho_tsusin/security/enduser/security01/07.html)

雖然感染病毒不一定是經由公共無線網絡這條途徑，但透過連接偽造的存取點，就有機會提高感染病毒的可能性。有個典型的例子是 [WannaCry](https://zh.wikipedia.org/zh-tw/WannaCry)。WannaCry 透過 tcp/445 port 進行攻擊，受到防火牆保護的網路通常不會受到感染，但如果連接到偽造的存取點，並將網路配置文件設定為 Private 時，就可能增加被感染的可能性。

在以下影片中，模擬使用偽造的存取點，展示 WannaCry 利用 Windows 的漏洞 MS17-010 進行攻擊，以及透過文件共享洩露資訊的情況。

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMbB9DUkz-k?si=Fd4IhdCYhBUNKrxB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

使用者的防護措施如下：

- 連接到公共無線網絡時，將網路配置文件設定為 Public
- 保持軟體更新至最新狀態

此外，這類攻擊通常無法透過 VPN 來預防（已在 Norton Secure VPN 驗證），即便使用 VPN，也不能忽略上述的防護措施。

## 肩窺攻擊

肩窺攻擊（Shoulder Hacking）是指旁人在附近窺視螢幕或鍵盤操作的行為，在這種情況，給人「越過肩膀偷看」的感覺，因此被稱作肩窺攻擊，實際上不一定侷限於越過肩膀偷看。

可參考： [ソーシャルエンジニアリングの対策｜社員・職員全般の情報セキュリティ対策｜企業・組織の対策｜国民のための情報セキュリティサイト](https://www.soumu.go.jp/main_sosiki/joho_tsusin/security/business/staff/12.html)

防範措施如下：

- 使用防窺螢幕保護貼
- 當周圍有人時，避免輸入密碼或信用卡資訊

肩窺攻擊與原始推文中的 「在星巴克使用免費 Wi-Fi」無關，因此可能稍微偏離了主題。

## 離席時的攻擊

在咖啡廳等場所，有些人會把筆記型電腦放在座位上然後離席一陣子。在咖啡廳如果想去廁所，即使隨身攜帶貴重物品和筆電，飲料還是會留在原位，畢竟不太會想帶著飲料去廁所，這的確是有點棘手的問題。像我這樣比較膽小的人，可能會選擇「在咖啡廳忍住不去廁所」，但這麽做對健康（可能）不太好。

那麼，如果把筆電留在座位上離開，除了筆電可能被偷走，如果畫面還繼續開著，很容易被偷偷瀏覽已登入的網站或筆電中的文件。

此外，即使筆電沒有被偷，也可能在離席這段時間，在筆電安裝「[鍵盤側錄（Keylogger）](https://zh.wikipedia.org/zh-tw/%E9%94%AE%E7%9B%98%E8%AE%B0%E5%BD%95)」或其他惡意軟體⋯⋯但這種情況非常可疑，直接把整台筆電偷走還比較乾脆省事。
這種攻擊方式也和「使用星巴克的免費 Wi-Fi」主題無關，因此可能稍微偏離了主題。

防範對策如下所示：

- 在咖啡廳等地，不要把筆電留在座位上離開

## 那該怎麼做呢

近來工作型態改變，傾向推薦在咖啡廳等開放空間工作，又因為裝載 Apple 晶片的 MacBook 電池使用時間非常長，因此想在咖啡廳使用的心情也能夠理解。但由於存在上述的威脅，在使用時應該注意以下事項較為妥當：

- 確認是否使用 HTTPS 連線
- 透過預先加入的書籤使用網站
- 不忽視 TLS 憑證的錯誤訊息
- 軟體隨時更新至最新版本
- 在使用 Windows 作業系統時，將網路配置文件設定為 Public
- 在咖啡廳等地點，避免使用高度機密的網站
- 使用可信賴的（已針對漏洞進行防範）網站
- 使用網路共享等其他通訊方式
- 使用防窺螢幕保護貼
- 在咖啡廳等地點，避免輸入密碼或信用卡號碼
- 不把筆電等物品留在座位上離席
