###### tags: `2023鐵人賽` `qiita` `Security`
# [2023 15th鐵人賽] Day8 - 鹽加密的鹽通常會存放在哪裡

> 原文連結：[ソルト付きハッシュのソルトはどこに保存するのが一般的か - Qiita](https://qiita.com/ockeghem/items/d7324d383fb7c104af58?utm_source=Qiitaニュース&utm_campaign=38b649377c-Qiita_newsletter_580_08_23&utm_medium=email&utm_term=0_e44feaa081-38b649377c-62820449)

---

[toc]

對於 pictBLand 和 pictSQUARE 受到非法訪問，且將密碼儲存在未加鹽的 MD5 Hash 中的事件，近來已成話題。

> 2023 年 8 月 16 日，有篇投稿聲稱持有從 pictSQUARE 竊取的數據，並將這些資料銷售給外部論壇（部分略）。該投稿指出，雖然密碼已進行 MD5 HASH，由於未進行加鹽，因此已取得 29 萬 4512 組簡單密碼的原始字串（剩餘 26 萬 8172 組仍保持 MD5 HASH 值）。
內容引用自 [不正アクセスによるpictBLand、pictSQUAREの情報流出の可能性についてまとめてみた - piyolog](https://piyolog.hatenadiary.jp/entry/2023/08/17/030141)

在這段期間，觀察有關 MD5 HASH 和 salt 的推文（post），似乎有許多人對 salt 的理解是錯誤的。因此，我提出了以下的「測試問題」。收到許多回答，對此十分感謝。

![](https://imgur.com/57Y0JjG.png)
> 【問題】在儲存密碼 HASH 值時，通常會將鹽存放在哪裡呢？
> (1) 將鹽儲存在高度機密的文件中，並透過環境變數傳遞
> (2) 與 HASH 值一起存放在資料庫中
> (3) 儲存在硬體安全模組（HSM）中
> (4) 不進行儲存，每次都生成隨機的鹽
>（ [原推文連結](https://twitter.com/ockeghem/status/1691966966117122462?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1691966966117122462%7Ctwgr%5E65e8aaf5b94813177ea3debfa5293b39e1c5072e%7Ctwcon%5Es1_c10&ref_url=https%3A%2F%2Fqiita.com%2Fockeghem%2Fitems%2Fd7324d383fb7c104af58)）

正確答案是「與 HASH 值一起存放在資料庫中」，結果發現正確率非常低，只有 33.9%。我的「擔憂」似乎已成現實。

那麼，讓我們來檢討答案吧。

## 使用 HASH 值保存密碼的原因

首先來談談，使用 HASH 值保存密碼的目的：

- 即使密碼訊息外洩，仍希望盡量延遲密碼的濫用
- 即使是管理員，若知道用戶的密碼也會提高被濫用的可能性
- 若伺服器遭受入侵，加密密鑰也可能會被竊取

基於上述理由，通常會以 HASH 值保存密碼，而非採用可解密的加密密鑰管理。如同 Unix/Linux/Windows 等系統，也是將用戶的密碼以 HASH 值的形式保存，網頁應用程序也會要求避免以明碼形式，而是使用 HASH 值保存。

## 加鹽的目的

- 若僅使用單純的 HASH 值，那麼設定相同密碼的用戶之間，其 HASH 值也會相同，這種情況將會提高風險
- 透過[彩虹表](https://zh.wikipedia.org/wiki/%E5%BD%A9%E8%99%B9%E8%A1%A8)等方法，對於約 8 個字符的英數字密碼，可在幾秒～幾分鐘內還原成明碼，因此加鹽是為了使「看起來的密碼長度」更長

下圖是以 SHA-256 保存密碼的範例，顯示設定相同密碼「password」的用戶，其 HASH 值將完全一致的情況。一旦被發現擁有相同密碼，將成為非法登錄的途徑。即使計算雜湊公式（Hash Function）為未知，一旦被發現「擁有相同的密碼，很有可能是簡單的密碼」，並且攻擊者能夠遠程進行[字典攻擊](https://zh.wikipedia.org/zh-tw/%E5%AD%97%E5%85%B8%E6%94%BB%E6%93%8A)，或是透過故意註冊簡單的密碼，從而一網打盡這些用戶的密碼。

![](https://imgur.com/iVxqlvU.png)

為了避免這種情況，通常會生成一個稱為鹽的短字串，並附加到密碼的前後來計算 HASH 值。由於每個使用者的鹽都不同，即使是密碼相同，也會產生不同的 HASH 值。

## 鹽通常會存放在哪

如上文所述，即使在 Unix 中，也曾使用 HASH 值儲存密碼，但由於每個系統和版本會有不同的 HASH 值儲存格式，因此存在互通性問題。為了解決這個問題，設計出 Modular Crypt Format（MCF，模組加密格式），並廣泛應用於現今的 Linux 等系統（[參考](https://passlib.readthedocs.io/en/stable/modular_crypt_format.html)）。以下是以鹽 = = SALT（實際是用隨機字串），密碼 = pokemon，以 SHA-512 格式計算密碼 HASH 值的結果：

```jsx
$ openssl passwd -6 -salt=SALT pokemon
$6$SALT$ULXzhDaWogf6Q3KHTtpYdqKKEIaFPML8gl5wpHpvPJVkGgiKGubqkogwvqoVn3eDsrJuRB22w.RPWzAdEu1xD.
```

這是 Linux 的 /etc/shadow 儲存密碼 HASH 值的格式。上方內容有以下含義：

```bash
$6$  雜湊方式（在這個範例是用 SHA-512）
SALT 鹽（在實際操作中使用隨機字串）
ULX..以下是 HASH 值
```

HASH 值、鹽和雜湊方式會「一起」儲存在文件的一行中。由於密碼驗證需要這些訊息，因此會需要儲存在一起。

MCF 最初是為 Unix/Linux 的密碼儲存而設計的，但目前在 Web 應用程式中也被廣泛使用於需要儲存密碼的情況。以下是使用 PHP 的 password_hash 函數，將密碼 = pokemon 轉換的範例：

```jsx
$ php -r "echo password_hash('pokemon', PASSWORD_DEFAULT), PHP_EOL;"
$2y$10$5MLO1PPVHzUiW/mggn8kAOkF/aoRk0RaLBSH3CwU47jmacYoGtrFa
```

上述範例代表的涵意如下：

```jsx
2y algorithm=bcrypt
10 Steching 次數的指標（不代表 10 次）
5MLO1PPVHzUiW/mggn8kAO Salt
kF/aoRk0RaLBSH3CwU47jmacYoGtrFa HASH 值
```

不只是 PHP，主要的 Library 和 Framework 都使用 MCF 格式，應用程序通常會將密碼資訊以 MCF 格式儲存在資料庫中。

因此，對於上述問題的解答是（鹽）「應該與 HASH 值一起保存在資料庫中」。透過使用MCF，即可在 PHP 開發的 Web 應用程式移植到 Ruby on Rails 等框架的情況，仍保持同樣的密碼資訊直接移植。

## 若 HASH 值和鹽一起儲存，是否會在洩露時被濫用？

這裡許多人會抱持著疑問，若把 HASH 值和鹽一起儲存，那麼密碼在洩露後是否會輕易被破解？

確實「若花費足夠的時間，是可以被破解的」，但這並不容易。由於雜湊函數是單向的，因此無法從 HASH 值和鹽，透過數學公式等方式計算出明文密碼，而需使用字典攻擊或暴力破解。在儲存密碼時，應使用避免使用常見的高速雜湊函數（如 MD5 或 SHA-2），而是為密碼保護而設計出「緩慢的」算法，如 bcrypt、scrypt、Argon2 等。除了改良算法，還包括重複進行雜湊計算的延伸步驟（Stretching，Linux 用來保存密碼的 `$6$` 格式也有執行延伸）。透過這些措施，能夠使密碼的 HASH 值在短時間內無法被濫用，為密碼變更提供緩衝時間。

另一方面，若原始密碼本身就很簡單，像是 password 或 123456 等，容易被字典攻擊破解。這是使用 HASH 值儲存密碼時的限制，為了解決這個問題，開始出現了所謂的胡椒（pepper）。pepper 是一個單一的秘密字串，通過與密碼進行混合，可提升密碼的機密性。pepper 若是外洩，那將失去其意義，因此建議將 pepper 儲存在具高度機密性的[硬體安全模組（HSM）](https://zh.wikipedia.org/zh-tw/%E7%A1%AC%E4%BB%B6%E5%AE%89%E5%85%A8%E6%A8%A1%E5%9D%97)等儲存設備中。”

## 錯誤的答案有何問題

以下是有關錯誤答案的重點解釋：

### 將鹽儲存在高度機密的文件中，並透過環境變數傳遞

這種實作方式無法滿足鹽的要求，因為必須達到「每個使用者都不同」。雖然這種方法可能適用於 [Pepper](https://en.wikipedia.org/wiki/Pepper_(cryptography))，但若以可能被入侵為前提，透過環境變數傳遞並不安全。

### 儲存在[硬體安全模組（HSM）](https://zh.wikipedia.org/zh-tw/%E7%A1%AC%E4%BB%B6%E5%AE%89%E5%85%A8%E6%A8%A1%E5%9D%97)中

這種實作也難以滿足「每個使用者都不同」的需求，特別是考慮到使用者數量可能超過數十萬的情況。另一方面，這種方法更適用於儲存 pepper。但如果已經選擇使用 HSM，就不應該把加密金鑰移出 HSM，而是善用 HSM 的特性，直接在內部加密密碼 HASH 值。

### 不進行儲存，每次都生成隨機的鹽

雖然可以在每次都生成隨機的鹽，但若不儲存鹽，將無法進行密碼驗證。

## 總結

本文首先以問答形式，提出有關如何儲存鹽的問題，並進行了解說。目前主流儲存鹽的方法，是透過 Modular Crypt Format（MCF），被廣泛使用於 Linux 和 Web 應用程式的密碼儲存。但即使不知道這一點，只要使用高安全性的密碼儲存 Library，也非常有機會在未知的部分使用到 MCF 格式。
通常情況下，鹽會和 HASH 一起儲存，如前文所述，但如果不放心，則可以考慮使用 pepper（有時稱作 Secret Salt）。在這種情況下，如何安全管理 pepper 將是一項挑戰，例如考慮使用 HSM 或 Cloud HSM 作為選項。

## 宣傳

更多內容可參考作者的 YouTube 頻道，提供許多有關密碼保護的影片說明。

<iframe width="560" height="315" src="https://www.youtube.com/embed/p_2tiP0qclQ?si=-vF4yboyoc4jwH1n" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

[エッセンシャルコース詳細 | Security Campus](https://www.security-campus.com/essential)
