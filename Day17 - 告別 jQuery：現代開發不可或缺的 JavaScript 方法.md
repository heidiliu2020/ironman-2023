###### tags: `2023鐵人賽` `qiita` `jQuery` `JavaScript`
# [2023 15th鐵人賽] Day17 - 告別 jQuery：現代開發不可或缺的 JavaScript 方法

> 原文連結：[jQueryへの別れ：現代的な開発のための必須JavaScriptメソッド - Qiita](https://qiita.com/figueiredoluiz/items/0e51c1aec790f053fd9c)

有時在工作上，需要維護一些比較早期的專案，或開發小型不需使用到框架的案子，jQuery 提供的功能與便利性，通常能快速滿足各種需求。但自從 ES6 的出現，引入箭頭函數、模組化、非同步操作等語法功能，考慮到性能優化、行動裝置開發、可維護性等因素，原生 JavaScript 已逐漸取代 jQuery 。

透過這篇文章，除了複習 jQuery 中常用的方法，同時對照原生 JavaScript 對應的方法，以達成相同目的。

以下正文開始。

---

[toc]

## 前言

長期以來，我一直與遺留程式碼（Legacy Code）共事，但 jQuery 的重要性仍是經常被討論的話題之一。雖然這個 Library 本身依舊方便，完美地滿足不同時代的需求。
現今大多在談論的是 ES2023，但過去 jQuery 所涵蓋的大部分功能，早已被納入 2015 年發布的 ES6 版本中。

ES6 的標準已經得到廣泛支援，支援度達到 96％（來源：[caniuse.com](http://caniuse.com/)）。因此，針對像是元素選擇、樣式設定、動畫和數據取得等的基本任務，現在或許是重新審視使用這個 Library 的好時機。

以下主題將舉出一些標準的 jQuery 使用模式，以及相對應的原生 JavaScript 方法，希望能作為參考資料。

## 元素選取

透過 CSS Selector，能夠選取一個或多個 DOM 元素。

在 JavaScript 中，有許多方法可以用於選擇元素，其中一個常用的方法是 Query Selector。透過 Query Selector，可基於 CSS Selector 模式選取 Document 中的特定元素。

```jsx
// jQuery 和原生 JavaScript: 選擇所有具有 .item 的實例
$(".item");
document.querySelectorAll(".item");
```

上方程式碼，展示使用 jQuery 和原生 JavaScript 方法，選取具有 `.item` 類別的所有元素。在jQuery 中，使用 `$` 函數並將 CSS Selector 作為參數。在原生 JavaScript 中，使用 `document.querySelectorAll` 方法，返回與指定 Selector 匹配的元素集合。

以下是使用不同 Selector 來選取元素的範例：

```jsx
// 基於類別查詢
$(".item");
document.querySelectorAll(".item");
document.getElementsByClassName("item");

// 基於 ID 查詢
$("#item");
document.querySelector("#item");
document.getElementById("item");

// 基於屬性查詢
$('a[target=_blank]');
document.querySelectorAll('a[target=_blank]');
```

上述範例中，透過不同的 Selector，基於類別、ID 和屬性條件來選取元素。使用 jQuery 和原生 JavaScript 提供的方法，均得到相同的結果。

透過這些選取元素的技巧，能夠有效選取 DOM 中所需的元素，並進行更進一步操作和互動。

## 對元素執行函數的方法

在 jQuery 中，可以很容易對選取的所有元素執行某個函數，但原生 JavaScript 的步驟則略有不同。在原生 JavaScript 中，為了迭代處理 `NodeList` 中的元素，需要使用 `NodeList.forEach()` 方法。

以下程式碼，是使用 jQuery 和原生 JavaScript 來隱藏元素的範例：

```jsx
// jQuery: 隱藏所有 .item 的實例
$(".item").hide();

// JavaScript: 迭代處理 NodeList 中的元素，隱藏所有 .item 的實例
document.querySelectorAll(".item").forEach(item => {
  item.style.display = "none";
});
```

上述程式碼中，在 jQuery 使用 `hide()` 方法來隱藏所有 `.item` 的實例。另一方面，在原生 JavaScript 使用 `document.querySelectorAll(".item")` 來選取所有 `.item` 的實例，接著使用`NodeList.forEach()` 方法，在每個元素加上隱藏的樣式。

在原生 JavaScript 中，使用 `NodeList.forEach()` 方法，可以輕鬆對 NodeList 中的元素執行函數。透過這個步驟，即使是原生 JavaScript 也能對元素執行操作和處理。

## 選取元素內的元素的方法

當需要在特定範圍內選取元素時，在 jQuery 通常會使用 `.find()` 方法；而在 JavaScript 則可以使用 `querySelector` 或 `querySelectorAll` 方法選取元素的子元素，以達到相同的效果。

以下程式碼，示範如何在 jQuery 和 JavaScript 中選取 `.container` 內的第一個 `.item` 元素。在 jQuery 會先將 `.container` 元素儲存在變數中，接著使用 `.find(".item")` 來查找子元素。在 JavaScript 則是使用 `document.querySelector(".container")` 選取 `.container` 元素，接著使用 `querySelector(".item")` 來查找子元素。

```jsx
// jQuery: 選取 .container 內的第一個 .item
var container = $(".container");
container.find(".item");

// JavaScript: 選取 .container 內的第一個 .item
var container = document.querySelector(".container");
container.querySelector(".item");

// JavaScript: 選取 .container 內的所有 .link
var container = document.querySelector(".container");
container.querySelectorAll(".link");
```

## 父元素和相鄰元素的遍歷

接著介紹如何根據元素的階層結構，從目標元素選取父元素或相鄰元素。在 JavaScript 中，可以使用以下屬性：`nextElementSibling`、`previousElementSibling` 和 `parentElement`。

以下程式碼，示範如何使用 jQuery 和 JavaScript 來選取元素的相鄰元素或父元素。

```jsx
// jQuery: 選取 .item 的下一個元素、前一個元素、父元素
$(".item").next();
$(".item").prev();
$(".item").parent();

// JavaScript: 選取 .item 的下一個元素、前一個元素、父元素
var item = document.querySelector(".item");
item.nextElementSibling;
item.previousElementSibling;
item.parentElement;
```

這個範例，是以具有 `.item`  類別的元素作為目標。在 jQuery 中，使用 `.next()` 方法選取下一個元素，使用 `.prev()` 方法選取前一個元素，使用 `.parent()` 方法選取父元素。在 JavaScript 中，使用 `nextElementSibling` 屬性選取下一個元素，使用 `previousElementSibling` 屬性選取前一個元素，使用 `parentElement` 屬性選取父元素。

透過這些方法，使元素之間的遍歷成為可能，實現靈活的 DOM 操作。

## 事件處理

在 jQuery 可使用 `.on()`、`.bind()`、`.live()`、`.click()` 等多種方法來監聽事件，而在 JavaScript 則使用 `.addEventListener()` 方法來實現相同的功能。

```jsx
// jQuery: 處理 click、moustenter 和 keyup 事件
$(".button").click(function(e) { /* 處理 click 事件 */ });
$(".button").mouseenter(function(e) {  /* 處理 mouseenter 事件 */ });
$(document).keyup(function(e) {  /* 處理 keyup 事件 */  });

// JavaScript: 處理 click、moustenter 和 keyup 事件
document.querySelector(".button").addEventListener("click", (e) => { /* ... */ });
document.querySelector(".button").addEventListener("mouseenter", (e) => { /* ... */ });
document.addEventListener("keyup", (e) => { /* ... */ });
```

## Click 事件

使用 jQuery 的 `.on()` 方法，可以為動態新增的元素註冊事件處理（EventHandler）。在 JavaScript 中，想要實現事件委派（Delegation），可透過事件冒泡（Bubbling）在父元素上捕獲事件（Capture），並判別目標元素。

```jsx
// jQuery: 處理 .container 内 .active 元素的 click 事件
$(".container").on("click", ".active", handleClick);

// JavaScript: 處理 .container 内 .active 元素的 click 事件
document.querySelector(".container").addEventListener("click", function (event) {
  if (event.target.matches(".active")) {
    handleClick(event);
  }
});
```

## 動態新增元素的監聽事件

使用 jQuery 的 `.on()` 方法，可以為動態新增到 DOM 的元素進行事件處理。即使不使用 jQuery，也可以在將元素新增到 DOM 時，將事件處理新增到元素，以實現相同的功能。

```jsx
// jQuery: 處理動態新增的 .active 元素的 click 事件
$(".search-container").on("click", ".active", handleClick);

// JavaScript: 建立元素，放入 DOM 並加上 eventListener
var searchElement = document.createElement("div");
document.querySelector(".search-container").appendChild(searchElement);
searchElement.addEventListener("click", handleClick);
```

## 觸發和建立事件

觸發和建立事件，可使用 JavaScript 的 `dispatchEvent()` 方法。`dispatchEvent()` 方法可在任何元素上調用，並且以 `Event` 作為第一個參數。

```jsx
// jQuery: 在 document 以及 .item 上觸發 myEvent
$(document).trigger("myEvent");
$(".item").trigger("myEvent");

// JavaScript: 建立 myEvent 並 dispatch event
document.dispatchEvent(new Event("myEvent"));
document.querySelector(".item").dispatchEvent(new Event("myEvent"));
```

## 元素的樣式設定

在 jQuery 中，要改變元素的 Inline CSS，可使用 `.css()` 方法，而在 JavaScript 中，可使用 `.style` 將值分配給不同的屬性，以實現相同的效果。

```jsx
// jQuery: 將 .item 的文字顏色設為 #000
$(".item").css("color", "#000");

// JavaScript: 將第一個 .item 的文字顏色設為 #000
document.querySelector(".item").style.color = "#000";
```

若是想要設定多個屬性的情況：

```jsx
// jQuery: 設定多個樣式
$(".item").css({
  "color": "#000",
  "background-color": "red"
});

// JavaScript: 設定 color 為 #000，background 為 red
var item = document.querySelector(".item");
item.style.color = "#000";
item.style.backgroundColor = "red";

// 一次設定所有樣式（覆蓋現有樣式）
item.style.cssText = "color: #000; background-color: red";
```

## fadeIn() 與 fadeOut()

在 jQuery 中使用 `.fadeIn()` 方法，能使具有 `.item` 類別的元素實現淡入效果。

```jsx
// jQuery: 將 .item 淡入
$(".item").fadeIn();
```

為了在 JavaScript 中實現相同效果，這裡建立一個名為 `fadeIn()` 的函數，該函數以元素作為參數，透過修改元素樣式來實現淡入效果。

在函數中，設定 `transition` 屬性，並將 `opacity` 屬性改為 `1` 使元素可見，透過動態調整元素的不透明度，實現淡入效果。

```jsx
// JavaScript: 透過樣式實現 .item 淡入效果
function fadeIn(element) {
  element.style.transition = "opacity 1s";
  element.style.opacity = "1";
}

fadeIn(document.querySelector(".item"));
```

## hide() 與 show()

`.hide()` 和 `.show()`，可透過設定元素的 `display` 屬性為 `none` 和 `block` 的方法來實現。

```jsx
// jQuery: 隱藏或顯示元素
$(".item").hide();
$(".item").show();

// JavaScript: 隱藏或顯示元素（修改 display 屬性）
document.querySelector(".item").style.display = "none";
document.querySelector(".item").style.display = "block";
```

## 等待 DOM 完成加載

若需要等待 DOM 完全加載的情況（例如：要附加事件到 DOM 上的對象時），通常會使用 jQuery 的  `$(document).ready()` 或簡寫 `$()`。而在 JavaScript 中，可透過監聽 `DOMContentLoaded` 事件來實現相同的功能。

```jsx
// jQuery: 在 DOM 完全加載後執行某些操作
$(document).ready(function() {
  /* todo... */
});

// JavaScript: 在 DOM 完全加載後執行某些操作
document.addEventListener("DOMContentLoaded", (event) => {
  /* todo... */
});
```

## 操作類別

在 jQuery 中，可使用 `.addClass()`、`.removeClass()`、`.toggleClass()` 等方法來操作類別。在 JavaScript 中，可使用 `classList` 屬性來實現相同的功能。

```jsx
// jQuery: 新增、移除、切換 "active" 類別
$(".item").addClass("active");
$(".item").removeClass("active");
$(".item").toggleClass("active");

// JavaScript: 新增、移除、切換 "active" 類別
var item = document.querySelector(".item");
item.classList.add("active");
item.classList.remove("active");
item.classList.toggle("active");
```

若要新增或移除多個類別的情況：

```jsx
// 新增或移除 "active" 和 "highlighted" 類別
var item = document.querySelector(".item");
item.classList.add("active", "highlighted");
item.classList.remove("active", "highlighted");
```

當需要切換兩個不同類別時，可透過 `classList` 屬性並調用 `.replace()` 方法，將一個類別替換為另一個類別。

```jsx
// 刪除 "active1" 類別，並將其替換為 "active2"
document.querySelector(".item").classList.replace("active1", "active2");
```

## 檢查類別是否存在

若要檢查元素是否具有特定類別，可使用 JavaScript 的 `.classList.contains()` 方法。

```jsx
// jQuery: 檢查 .item 是否具有 "active" 類別，並執行某些操作
if ($(".item").hasClass("active")) {
  // 執行某些操作...
}

// JavaScript: 檢查 .item 是否具有 "active" 類別，並執行某些操作
if (document.querySelector(".item").classList.contains("active")) {
  // 執行某些操作...
}
```

## 透過 .get() 或 .ajax() 進行網路請求

在 jQuery 中，可使用 `.get()` 或 `.ajax()` 進行網路請求。在 JavaScript 中，可使用具有相似功能的 `fetch()`，這個方法將會返回 Promise 以處理 Response。

```jsx
// jQuery: 進行 AJAX 請求
$.ajax({
    url: "data.json"
  }).done(function(data) {
    // ...
  }).fail(function() {
    // 錯誤處理
  });

// JavaScript: 使用 fetch 進行網路請求
fetch("data.json")
  .then(data => {
    // 資料處理
  }).catch(error => {
    // 錯誤處理
  });
```

## 建立元素

若要在 JavaScript 動態建立元素，可使用 `document` 物件的 `createElement()` 方法。

```jsx
// jQuery: 建立 div 元素和 span 元素
$("<div/>");
$("<span/>");

// JavaScript: 建立 div 元素和 span 元素
document.createElement("div");
document.createElement("span");
```

## 更新 DOM

當需要更改元素的文字，或將新元素放到 DOM 時，通常會使用 `.innerHTML` 屬性，但這可能會面臨跨網站指令碼攻擊（XSS）的風險，以下介紹更安全的替代方法。

若要讀取或更新元素文字，可使用 `textContent` 屬性。

```jsx
// jQuery: 更新 .item 的文字
$(".item").text("新しいテキスト");
// 讀取 .item 的文字
$(".item").text(); // 返回 "新的文字"

// JavaScript: 更新 .item 的文字
document.querySelector(".item").textContent = "新しいテキスト";
// 讀取 .item 的文字
document.querySelector(".item").textContent; // 返回 "新的文字"
```

若要將元素新增到 DOM，可透過 `appendChild`：

```jsx
// jQuery: 建立 div 元素並新增到 .container
$(".container").append($("<div/>"));

// JavaScript: 建立 div 元素並新增到 .container
var element = document.createElement("div");
document.querySelector(".container").appendChild(element);
```

## 總結

以上只是概略介紹方法，未提及 jQuery 的負面影響，或轉移到原生 JavaScript 的好處。

可將本篇文章，作為轉移到原生 JavaScript 時的參考。此外，注意這並不是全面的指南，建議參考官方文件，並搭配這裡介紹的原生 JavaScript 方法。

## 參考資料

可閱讀 Mozilla Web 文檔，以更深入瞭解 JavaScript：

- https://developer.mozilla.org/ja/docs/Web/JavaScript

從 jQuery 轉移到原生 JavaScript 的相關資訊，可參考下方連結：

- https://youmightnotneedjquery.com/
- https://tobiasahlin.com/blog/move-from-jquery-to-vanilla-javascript/
- https://dev.to/rfornal/-replacing-jquery-with-vanilla-javascript-1k2g
