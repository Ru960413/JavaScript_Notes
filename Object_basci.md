# JavaScript Object 基礎篇
這是我在讀完JavaScript.info的“Object: the basic”這個章節後的重點整理

## 什麼是Object?
不同於七個原始型態（primitive data type），Object 屬於複合型的資料型態（composite data type），可以儲存不定數量的鍵值對 (key-value paris)，而一組鍵值對我們稱做物件的一個屬性 (property)。一個屬性的值 (value) 可以是任何資料型態（也可以是function或boolean），而屬性的名稱 (key / name) 是一個字串型態。

## 如何宣告物件
宣告物件的方式有兩種：
![](https://i.imgur.com/yBDF3VG.png)

## 關於物件的屬性（property）
我們會在物件的大括弧內加入物件的屬性：
![](https://i.imgur.com/7LHSEsA.png)
在這個例子中user為一個物件，而其中包括了name和age這兩個屬性，而name有“John”的值，而age則有“30”的值。

可以想像成在user的這個抽屜中有name和age這兩個小資料夾![](https://i.imgur.com/KiSgbtZ.png)

### 物件屬性的存取

利用dot notation:
![](https://i.imgur.com/b2GWxUQ.png)

或者我們也可以用[] (Square Bracket):

不同於dot notation，sqaure bracket中可以是字串、變數，例如：

![](https://i.imgur.com/3HEsxcM.png)
![](https://i.imgur.com/W71ZnQu.png)

注意：此處的字串需要正確的使用引號。

我們也可以利用它獲取物件的屬性：
![](https://i.imgur.com/U2oxpRG.png)


### 屬性的移除

若我們要移除屬性可以利用delete operator：
![](https://i.imgur.com/0k8qoh7.png)

### 屬性名稱

在物件的屬性名稱也可以使用 language-reserved words 像是 “for”, “let”, “return” etc.
例如：
![](https://i.imgur.com/WKzs7mB.png)

### "in" operator
可被用來解讀一個屬性是否存在，若屬性不存在則會return undefined

![](https://i.imgur.com/OBX6fPZ.png)

物件屬性會置於 in operator前面。

當value為undefined時，也可以用in operator讀取：
![](https://i.imgur.com/Kl8HFlh.png)

## The "for...in" loop
他協助我們瀏覽物件內的所有key，可以表示成：
![](https://i.imgur.com/RoEAICB.png)
此處也可用“prop”代替“key”

例如：
![](https://i.imgur.com/jY3l5Eq.png)
可以讓我們得到物件的所有屬性。

## 如何依照加入的順序獲取物件屬性？
答案是：用特別的方式取得屬性。

舉個例子，以下是一個含有國際區碼的物件：
![](https://i.imgur.com/pF5Fr7j.png)

此處的區碼會依數字的順序排列（即美國第一位），但如果我們想將德國的區碼放在第一位呢？

只要將數字轉為字串的形式（在區碼前加入“＋”）就可以了！

![](https://i.imgur.com/ro1vn4h.png)

//基礎篇完














