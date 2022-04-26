## Part 1 Framework

credit: 以下節錄自[現在的前端都在用 JavaScript「框架」？前端框架的功能與優點](https://tw.alphacamp.co/blog/why-use-front-end-framework)

- What is a framework? What does it do?(functionalities and advantages)
  現今的「框架」其實就是一種提升開發效率、降低維護難度的開發架構。
  大都具有以下特性：

  1. 資料與 UI 分離：使 code 有較高的可讀性與可維護性，且由資料決定畫面的呈現，
     例如：
     ![code][./code/code_1.png]

     以下為 JavaScript 以 DOM 套入資料：
     ![code][./code/code_2.png]

     再來看看 Vue 的：
     ![code][./code/code_3.png]

  2. 模組化的 UI：一個網站總是會有一些重複出現的元素（例如按鈕、輸入表單、表格、對話框），我們會把這些重複出現的元素稱為 組件（Components），每個組件內包含了組件自己需要用的結構、樣式、邏輯。
     例如前述的例子，我們可以將 .card 這個元素抽成單獨的組件：
     ![code][./code/code_4.png]

     再從外部組件引入它：
     ![code][./code/code_5.png]

     這樣一來，各組件只需要處理組件內的事，外部引用的組件來決定怎麼使用、提供什麼資料給組件，藉由簡單的切分權責，加上前述的由資料決定畫面，就能讓各個組件的任務單一，並且能被重複使用。

  3. 提升效能：如同前述，在複雜的頁面中，如果頻繁透過操作 DOM 的方式改變畫面，可能會造成全頁面的 Reflow 及 Repaint；不過在使用框架時，開發者不用太擔心這個問題。

  原因是在各主流框架的實作中，幾乎都包含了 Virtual Dom 的概念，也就是用 JavaScript 物件來表達當前的頁面結構；藉由與 UI 分離的資料及 Virtual Dom 之間的關係，當資料變動時，事先計算好這次畫面需要變動的地方，如此一來便能抵銷掉無意義的更動，並重複利用已存在的 DOM 元素；當真的要進行 DOM 更新時，也會一次將所有需要更新的局部組件更新，讓效能的耗損盡可能降低。

  4. 豐富的開發者生態圈

  簡圖：
  ![picture][./pictures/what_is_framework.png]
  from [What is a JavaScript Framework? (in detail)](https://www.youtube.com/watch?v=Ka77djMkSwg&ab_channel=SuperSimpleDev)

- Some examples of framework?

  1. Django(python)
  2. Rails(Ruby)
  3. Laravel(php)
  4. spring(Java)
  5. Angular(JavaScript)
  6. Vue(JavaScript)
  7. React(JavaScript)
  8. Ember(JavaScript)
  9. Backbone(JavaScript)
     the list goes on...

- How to choose a framework?
  Choose the framework according to language, features/functionality, efficiency, personal preference.

## Part 2 Library

- What is a Library?
  Libraries in programming languages are collections of prewritten code that users can use to optimize tasks.

- Some examples of library?
  1. jQuery(JavaScript)
  2. Lodash(JavaScript)

p.s. 我覺得 framework 和 Library 的定義還蠻模糊的，只能做大概的區分...
