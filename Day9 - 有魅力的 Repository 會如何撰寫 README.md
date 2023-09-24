###### tags: `2023鐵人賽` `qiita` `GitHub`
# [2023 15th鐵人賽] Day9 - 有魅力的 Repository 會如何撰寫 README.md

> 原文連結：[イケてるレポジトリのREADME.mdには何を書くべきか - Qiita](https://qiita.com/autotaker1984/items/bce70c8c67a8f6fb1b9d)

---

[toc]

## 前言

在 GitHub 新建 Repository 時，首先會建立 `README.md` 這個檔案。您是否會將文件維持預設狀態，而不做任何修改呢？

`README.md` 是 Repository 的門面。通過編輯這份文件，能夠大幅提升 Repository 的質量。然而，可能有許多人不知道應該在 `README.md` 中寫些什麼。

本文將會整理一些建議的架構內容。

## `README.md` 的讀者是誰？

首先，需要考慮這份 `README.md` 是為誰而寫開始。

`README.md` 的讀者主要分為兩大類：使用者和開發人員。根據預期 Repository 的瀏覽對象主要是使用者或開發人員，決定以哪一方為主體來撰寫。

### `README.md`必須用英文撰寫嗎？

由於知名的 OSS（開源軟體）通常以英文撰寫 `README.md`，因此可能產生應該要使用英文撰寫的認知。然而，如果主要觀眾是懂日語的人，那 `README.md` 就應該以日語撰寫。

此外，若堅持用英文撰寫使內容變得薄弱，反而得不償失。近年來，因為翻譯技術有飛躍的進步，可嘗試先使用自己擅長的語言撰寫，然後再進行翻譯，也是另一種方法。

## 使用者想知道的事情

### Getting Started 入門指南

首先介紹使用者在試用工具所需的前置作業。基本架構如下：

- 安裝步驟
- 工具的基本使用方法

如果缺少這些內容，使用者將不知道該如何使用工具。因此請務必寫上說明。

此外，Getting Started 的長度通常反應使用該工具的門檻高低。理想情況下，安裝應該能透過一行指令完成，使用步驟也應該盡量簡化。

若撰寫時發現步驟太長，試著思考如何簡化；若難以簡化安裝步驟，可以考慮準備 Web 環境的 Playground，或建立 Docker Image。

## Manual 使用手冊

在 `README.md` 中，提供 Manual 和 API Reference 相關連結將對使用者非常有幫助。

需注意這些文件包括 **Tutorial** 和 **Reference** 兩種類型，請盡可能使其保持平衡。

### Tutorial 教程

描述工具典型的使用範例。盡可能附上使用截圖，以 Step By Step 的方式詳細說明。推薦使用 [Read the Docs](https://readthedocs.org/) 等工具來撰寫。

#### Reference 參考資料

詳細且全面性描述工具的規格。

若是在建立 Library 的情況，多數程式語言都附帶自動生成 Reference 的功能，因此建議透過工具從 Source Code 中的文檔註釋自動生成 Reference。

可搭配使用 [Read the Docs](https://readthedocs.org/) 等工具，盡量透過自動生成，以確保 Reference 和 Source Code 之間的一致性。

### Release Note 發版紀錄

撰寫發版紀錄，可在使用者升級工具版本時提供幫助。

雖然這在 Beta 版本或其他預發布版本並非必要，但在版本 1.0 以後發布的版本，請務必留下紀錄。由於回溯過去的版本以查找資訊並不容易，請務必在每次發布後追加紀錄。

發版紀錄應該放在 `CHANGELOG.md` 或 GitHub Releases 等地方，而非直接寫在 `README.md` 中，並且應該附上相關鏈接。

建議依照以下網站的格式撰寫發版紀錄：

+ [如何維護更新日誌](https://keepachangelog.com/zh-TW/1.0.0/)

在撰寫發版紀錄時，可能會希望詳細介紹新發布的功能，但需注意一點，發版紀錄是用於版本更新的文檔，若寫得過於詳細，**對於實際閱讀這些文檔的人來說，可能不是那麼感興趣**。

至於新功能，可另外在 Release Highlights 或 Blog 等地方進行宣傳。

在發版紀錄中，請確保提供以下兩點信息：

- 需要升級到哪個版本？
    - 哪個版本修復了安全漏洞？
    - 支援的 Runtime 和 Middleware 是否有變更？
- 升級版本時需要採取哪些措施？
    - 是否存在破壞性變更？（請遵循[語義版本控制](https://semver.org/lang/zh-TW/)）
    - 哪些功能被標記為不推薦，並提供了替代方案？

### 支援窗口・錯誤回報方式

在 `README.md` 中明確列出支援窗口，有助於收集到使用者的反饋。支援和錯誤管理雖然有些類似，實際上是不同的東西。兩者皆可在 Issues 中進行管理，但支援包含使用郵件列表、Slack、Discord 等方法。此外，透過舉出常見問題，提供疑難排解的文件也是不錯的做法。

無論使用哪種方法，重要的是明確列出支援窗口。
使用者在提問之前，應該先仔細閱讀提問方法，並依循相關的規範。

## 開發者想知道的事情

開發者文件可以寫在 `CONTRIBUTING.md` 中，但也經常會記錄在 README。若寫在 `CONTRIBUTING.md` 時，請確保能夠從 README 連結到相關內容。

### 開發環境設定指南

開發者文件的 Getting Started。

- 安裝所需工具的方法
- 如何 Build
- （如有需要）取得和設定驗證資訊的方法
- 在 Local 端執行的方法

同樣的，這裡也請盡量簡化步驟，讓開發者可以輕鬆建立開發環境。
也可提供 `devcontainer.json` 或雲端開發環境進行開發，但必須寫下需安裝的工具清單，避免環境設定成為一個[黑盒子](https://en.wikipedia.org/wiki/Blackboxing)。

## 測試方法

在開發者文件中，最重要的部分是測試方法。至少需記錄 Unit Testi 和 [Smoke Test](https://zh.wikipedia.org/zh-tw/%E5%86%92%E7%83%9F%E6%B5%8B%E8%AF%95_(%E8%BD%AF%E4%BB%B6)) 的執行方法。有了這些資訊，開發者即可在自己的環境設定發生問題時進行分析。

測試環境的連接訊息和驗證資訊，雖然無法直接在 Repository 中進行管理，但可在過程中記錄取得方式和位置。

### 部署・發布方法

接著是記錄在 Local 端開發後需要執行的步驟。舉例來說，若開發的是服務器端應用，則會記錄如何在 Staging 環境部署並進行整合測試。另一方面，若開發的是客戶端應用，則會記錄如何打包並建立 Release Candidates 以進行整合測試。

在文件中正確記錄這些步驟非常重要，否則可能導致過度依賴特定人員或缺漏工作步驟的問題。即使使用 CI/CD 自動化，也應該記錄哪些地方執行什麼操作，以及如何檢查結果。

### 設計資料・編碼規範等連結

建議製作像是伺服器架構圖與程式碼封裝架構，能夠總覽整體系統架構的資料（例如   `ARCHITECTURE.md`），這些資料將有助於開發人員進行除錯及思考如何修正。同樣的，編碼規範將有助於確保程式碼品質。

### 開發流程

最後是記錄程式碼以外的開發規則，像是如何提出工作項目、分支策略、建立 PR 的方法等等。

透過整合開發流程，將有助於提升該 Repository 的「秩序」。若缺乏規則管理如何提出工作項目，將使編寫開發技術路線和發版紀錄變得困難。若缺乏明確的分支策略，將使得開發分支變得不穩定，進而降低開發速度。此外，若不為 PR 制定規則，將會增加會經過測試的程式碼數量，降低程式碼品質，或導致使用手冊過時。

# 如何使 `README.md` 更吸引人

前面已經介紹該如何充實 `README.md` 的內容，但外觀也同樣重要。
通過調整 `README.md` 的外觀，能夠讓整個 Repository 看起來更具有吸引力。

### 建立 LOGO

在 README 中加入專案的 LOGO 可以使 `README.md` 更加引人注目。有了 LOGO 之後，除了能夠幫助識別該 Repository，也能提升親和力。
一開始可以先選擇使用簡單的 LOGO，選定 LOGO 將會有所幫助。

### 新增 Badge

許多知名開源軟體的 README 都有附上像是 `build: passing`, `npm: 2.7.3` 這類的 Badge。

透過查看程式碼，可以瞭解到這些 Badge 實際上只是圖片連結，是使用根據 Repository 狀態來動態生成圖片的服務。對於 Public Repository，經常會使用 [shields.io](https://shields.io/) 等的服務，使 Badge 看起來更加吸引人。

對於 Private Repository，可能就不適用這種服務，但 GitHub 本身就會根據 Work Flow 的成功與否生成 Badge，像這樣簡單的 Badge 就很足夠使用了。

* [Adding a workflow status badge - GitHub Docs](https://docs.github.com/en/actions/monitoring-and-troubleshooting-workflows/adding-a-workflow-status-badge)

## 總結

本文介紹了應該記錄在 `README.md` 中的內容。

透過充實 `README.md` 內容，能夠讓 Repository 更易於使用和開發。當然，撰寫程式碼也同樣重要，但也記得時常更新自己 Repository 的 `README.md` 吧。
