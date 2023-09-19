[![hackmd-github-sync-badge](https://hackmd.io/xkiov09zQeaL3RvPnYTE4A/badge)](https://hackmd.io/xkiov09zQeaL3RvPnYTE4A)
###### tags: `2023鐵人賽` `qiita` `naming`
# [2023 15th鐵人賽] Day4 - 寫給菜鳥工程師有關變數/函數/方法的英文命名規則

> 原文連結：[初心者プログラマーのための変数/関数/メソッドの英語命名規則 - Qiita](https://qiita.com/YutaManaka/items/62dda256bb7ba6c08399)

這篇文章是介紹英文命名規則，根據命名對象、使用情境、狀態等進行分類，並舉出使用範例。

以下是正文。

---

[toc]

## 前言

「每次 review 的時候，好像總是被指正變數名稱⋯⋯」
「作為日本人，用英文命名還是有點困難⋯⋯」

您有這樣的煩惱嗎？

本文將以流程圖的形式，說明「當工程師在英文命名遇到困難時該怎麼辦」！學成後也許就能從菜鳥工程師畢業了！？

※本文根據 Laravel, Vue.js 專案規則為基礎進行解說。內容也包括專案的內部規則，請注意這點。

## 適用對象

本文適合以下對象：

- 菜鳥工程師
- 程式語言初學者
- 對 PHP(Laravel), JavaScript(Vue.js) 英文命名陷入苦戰

## 必備知識

以下內容是基於瞭解中學和高中學習內容的前提下進行說明。請知悉。

- 三單現（第三人稱單數現在式）的 s 是什麼？
- 五大句型(SV/SVC/SVO/SVOO/SVOC)是什麼？
- 詞性（名詞/形容詞/動詞）是什麼？
- 什麼是以 ~ing 或 ~ed 結尾的形容詞？

## 總覽

可參考下方流程圖進行命名：

![](https://hackmd.io/_uploads/Hyy5k-81a.png)

上圖流程意思大致如下：

+ 變數、常數、Table、Column 命名
    + 是否顯示日期 => 是：(A) 動詞+at/on
    + 是否為布林值 => 是：(B) 形容詞+名詞
    + 是否為切換顯示/隱藏的 flag => 是：(C) show+名詞
    + 是否為功能ON/OFF的 flag => 是：(D) 名詞+enabled
    + 是否為表示存在的 flag => 是：(E) 名詞+exists
    + 是否擁有/包含某物的 flag => 是：(F) has/contains+名詞
    + => 否：(G) is+形容詞
+ 函數、類別命名
    + 是否為事件函數 => 是：(H) on+名詞+形容詞
    + 是否表示轉換某物 => 是：(I) to+名詞
    + 是否想改變什麼狀態 => 是：(J) 動詞+受詞+形容詞
    + => 否：(K) 動詞+受詞

接下來會依序介紹各種命名使用情境與範例。

## (A)動詞+at/on

表示日期和時間時，參照以下方式：

```jsx
// 使用 at 表示時日
updatedAt  // 更新時日
importedAt // 匯入時日

// 使用 on 表示時日
deletedOn // 刪除時日
```

## (B)形容詞+名詞

當賦予非 boolean 值的變數時，通常會依照以下規則：

```jsx
// 例

// 形容詞+名詞
specialCategory // 特殊類別

// 形容詞可以是動詞的被動式(~ed)或 ing 形式
importedPlayerNames // 匯入的多個選手名稱
deletedPlayers // 刪除的多個選手
payingPlayer   // 付款的選手

// 若沒有形容詞，僅使用名詞或「名詞+名詞」表示也可以
errorCode // 錯誤代碼
centerImageFilePath // 中央圖片檔案路徑
terminalIdsArray    // 包含多個終端 ID 的陣列

// 也可使用 名詞+without/before/after~ 的結構
userWithoutPermission // 無權限的使用者
itemTypeBeforeUpdate  // 更新前的商品類型
quantityAfterOrder    // 訂單的數量
```

更多詳細內容請參閱[形容詞](https://qiita.com/YutaManaka/items/62dda256bb7ba6c08399#%E5%BD%A2%E5%AE%B9%E8%A9%9E%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%86%E3%82%AF%E3%83%8B%E3%83%83%E3%82%AF)、[名詞的技巧](https://qiita.com/YutaManaka/items/62dda256bb7ba6c08399#%E5%90%8D%E8%A9%9E%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%86%E3%82%AF%E3%83%8B%E3%83%83%E3%82%AF)。

## (C)show+名詞

需要切換顯示/隱藏的 flag 時，可依照以下方式：

```jsx
// 例
showConfirmationModal
// true: 顯示確認視窗
// false: 隱藏確認視窗
```

名詞的部分也可放入形容詞+名詞，如(A)所示。

## (D)名詞+enabled

當需要切換某個功能ON/OFF 的 flag 時，可依照以下方式：

```jsx
// 例
autoScrollEnabled
// true: 自動滾動 ON
// false: 自動滾動 OFF
```

雖然也可以使用 disabled，但雙重否定可能較不容易理解，因此最好避免使用。

名詞的部分也可放入形容詞+名詞，如(A)所示。

## (E)名詞+exists

當需要表示存在與否的 flag 時，可按以下方式，需注意詞序的不同：

```jsx
// 例
soldOutItemExists
// true: 完售的商品存在
// false: 完售的商品不存在
```

名詞的部分也可放入形容詞+名詞，如(A)所示。

## (F)has/contains+名詞

當需要表示是否擁有/包含某物的 flag 時，可依照以下方式：

```jsx
// 例
containsCheckedOutPlayers
// true: 包含已經 checkout 的選手
// false: 不包含已經 checkout 的選手
```

名詞的部分也可放入形容詞+名詞，如(A)所示。

## (G)is+形容詞

以下是表示 boolean flag 的基本形式：

```jsx
// 例
isNew
isImported  // 是否已經匯入。動詞的被動式(~ed)也是形容詞的一種
isOrderable // 是否可訂購。也可使用 動詞+able
```

### is~ 的 is 前綴可以省略嗎？

由於形容詞本身即可表達意義，因此也有人認為 is 應該可以被省略，這取決於專案內統一的慣例。

```jsx
// 例
imported // 是否已匯入
deleted  // 是否已刪除
updated  // 是否已更新
```

## (H)on+名詞+形容詞

這種命名方式在前端開發中較頻繁使用，常用於事件相關的函數命名。

```jsx
onRowClicked // 當行被點擊時
onPaginationChanged   // 當分頁改變時
onDeleteButtonClicked // 當刪除按鈕被點擊時
onItemDisabled // 當物品被禁用時

// 對象明確的情況，也可使用「on+動詞」的被動式(~ed)
onClicked   // 當被點擊時
onSubmitted // 當提交時

// 也有一派認為使用「on+動詞」更好
onClick  // 當被點擊時
onSubmit // 當提交時
```

## (I)to+名詞

當需要表示轉換某物時，也可以簡化命名：

```jsx
// NG...雖然不是不行，但太長了... 
const convertTimeFromSecondsToMinutes = (time) => {...}

// OK. 由於參數明確指定為秒數，因此能夠理解這是一個轉換秒→分鐘的函數。
const toMinutes = (seconds) => {...}
```

## (J)動詞+受詞+形容詞

當需要表示改變對象狀態的函數時使用：

```jsx
// 設定收據已印刷
// 表示 receipt = printed
setReceiptPrinted
```

## (K)動詞+受詞

最常見的函數命名方式：

```jsx
joinStrings // 串接字串
switchTableWidth // 切換表格寬度
sortCategories   // 排序類別
toggleArchivedItems // 切換在庫商品
```

受詞可以是名詞、名詞+名詞、形容詞+名詞，與(A)相似。

## 按詞性的技巧

接下來，將根據詞性提供一些命名技巧。

### 名詞相關的技巧

### 名詞+名詞

儘管文法上應該以「名詞 of 名詞」方式書寫才對，但這會讓名稱變得過於冗長。

只需將名詞以 2 到 3 個單詞的方式聯接，同樣也能夠傳達意思。

```jsx
// 雖然不算 NG 但太長了...
codeOfError
pathOfFileOfCenterImage

// OK
errorCode
centerImageFilePath
```

建議將 id, name, code, response, request, path, url 等單詞放在句尾，開頭接別的名詞，這是很常見的命名方式！

### 注意單數和複數形式

光是單數或複數形式的名詞，就能傳達不同的名稱含義。

```jsx
// 例1
getSystemConfigs   // 取得多個系統設定
updateSystemConfig // 更新一個系統設定

// 例2
playerCount   // 玩家數量固定為 1，是常數嗎？
playersCount  // 玩家數量以整數存取，代表一個玩家人數
playersCounts // 玩家數量以數組形式存取，代表多個玩家人數，是物件嗎？
```

### 盡量避免使用不可數名詞

由於單數型和複數型有助於名詞的表達，因此不建議使用沒有複數型的名詞（不可數名詞）。

請儘量替換為可數名詞。

```jsx
// 不可數名詞
data, code, information, software

getData // NG. 無法確定取得的資料是一個還是多個。
getTexts // OK. 明確表示可取得多個資料，且能夠知道資料類型
```

### 使用資料型別表示

使用 ~Array, ~Object, ~String, ~Collection 等表示資料型別的名詞，也是推薦的做法。

```jsx
terminalIdsArray // 包含多個終端 ID 的陣列
```

### 避免太過詳細

您是否曾經為了更容易理解，使命名變得過長呢？

使用名詞的單數/複數型已經能充分傳達訊息，因此也可以省略部分名稱。

```jsx
// 雖然不算 NG，但太長了...
someItems
allItems
individualItem

// OK. 使用單數/複數型即可表達
items
item
```

### 善用 **without, before, after**

透過在名詞後加上這些詞語，能夠更詳細地表達情境或條件。

能夠掌握這些原則，基本上就已經沒問題了。

```jsx
userWithoutPermission  // 「沒有權限的」用戶
itemTypeBeforeUpdate   // 「更新前的」項目類型
itemQuantityAfterOrder // 「下單後的」庫存數量
```

### 形容詞相關的技巧

### 用動詞的被動式 (~ed) 表示形容詞也 OK

表達「被～」、「已經完成～」的情況時，使用動詞的被動式 (~ed) 作為形容詞是個不錯的做法。

```jsx
importedPlayerNames // 被導入的玩家名稱 = 已導入的玩家名稱
deletedPlayers // 被刪除的玩家 = 已刪除的玩家
disabledItem   // 被禁用的商品 = 已禁用的商品
limitedQuantity // 被限定的數量 = 已限定數量
```

### ing 形也屬於形容詞的一種

表達「正在做～」的情況時，使用動詞的 ing 形作為形容詞是個不錯的做法。

```jsx
payingPlayer // 正在支付的玩家 = 付費者
```

### ~ing 和 ~ed 之間的差異

~ing 的情況，表示「名詞正在做某個動作」或「即將進行某事」。

~ed 的情況，表示「名詞已經被做了某事」或「已經完成某事」。

```jsx
payingPlayer // 支付 = 付款的玩家 or 即將付款的玩家
PaidPlayer   // 被支付 = 被付款的玩家 or 已付款的玩家
```

### 善用否定型的形容詞

```jsx
// NG (不建議在開頭接 Not)
notCategorized
notCompleted

// OK (搜尋即可找到相關資訊)
uncategorized
incomplete
```

## 避免使用雙重否定

否定形容詞通常容易理解，但如果和 if 語句結合使用，可能導致程式碼變得難以理解。

當否定形容詞和否定條件組合在一起時，容易混淆 true 和 false，使程式碼變得不易閱讀且容易造成誤解。

```jsx
// NG
if (!disabled) {...}

// OK
if (enabled) {...}
```

請根據下方表格中形容詞的肯定型/否定型，試著撰寫 if 語句。

| 肯定型 | 否定型 |
| --- | --- |
| visible | hidden |
| public | secret |
| active | inactive |
| enabled | disabled |
| ~ | in~ |
| ~ | im~ |
| ~ | dis~ |
| ~ | un~ |

### 動詞相關的技巧

### 動詞只有一個！

Be 動詞不會和普通動詞一起使用。

請注意像是「isExists~」的寫法並不正確！

### PHP 和 JS 的常見動詞

經常使用的動詞(PHP)

- delete(刪除)
- filter(篩選)
- get(取得)
- store(保存)
- update(更新)

偶爾使用的動詞(PHP)

- archive(歸檔)
- bulkUpdate(批量更新)
- cancel(取消)
- count(計數)
- download(下載)
- duplicate(複製)
- export(匯出)
- hide(隱藏)
- import(匯入)
- reset(重置)
- start(開始)
- set(改變狀態。動詞+形容詞：setDisabled。動詞+受詞+形容詞：setReceiptPrinted)

經常使用的動詞(JS)

- change(改變狀態)
- click(點擊)
- join(連接字串)
- show(表示)
- sort(分類)
- submit(提交)
- switch(改變狀態)
- toggle(切換 ON↔︎OFF)

## 結語

以上總結程式語言初學者常見的英文命名規則。

## 參考文章

- [英語できない人が変数名の命名を完璧にできるようになる方法を教えようと思ったけどめんどくさくて途中で投げ出すも結構長々といいこと書いてる記事](https://zenn.dev/ccccc/articles/5a60336f54f429)
- [真偽値を返す関数のネーミング](https://qiita.com/yskszk/items/5a7f99c974773f03a82a)
