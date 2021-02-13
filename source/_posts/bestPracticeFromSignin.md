---
title: Best Practice From Sign-In Form
tags:
  - ux
  - frontend
  - 筆記
---

![](/images/bestPracticeFormSignin/cover.jpg "Cover")

### 前言
相信會員對於許多電商網站來說非常重要，甚至會影響到網站的 conversion rate。想像一下，當一個使用者透過連結或是廣吿來到你的網站，卻因為登入流程不順導致離開，這是非常可惜的。本篇整理了讀完 web.dev 發布的 [Best Practice From Sign-In Form](https://web.dev/sign-in-form-best-practices/) 後的一些心得。

在一開始前作者就有提到，最好的 Sign-In 就是不要有 Sign-In，這邊大意其實是在加入會員系統之前應該要先思考一下到底有沒有這個需要，例如只是單純的 Blog 加入會員系統可能就沒這麼必要。就來讓我們來看一下作者分享了哪些 tip 吧。

### HTML
<img width="80%" alt="Use form" src="/images/bestPracticeFormSignin/use-form.jpg">

* 盡可能使用最原始的 `<form/>` 來製作表單而不是其他 HTML tag (e.g., `<div/>`)。這樣除了具備 accessability 之外也對 screen reader 比較友善。另一種情形是當使用者 disable Javascript 的情況下也能正常操作。

</br>
</br>
<img width="80%" alt="Use label" src="/images/bestPracticeFormSignin/use-label.jpg">


* 善用 `<label/>` 標籤，這樣的好處是當使用者點擊 `<label/>`後，瀏覽器會自動 focus 到對應的 input。可以使用 `for` 或是直接將 `<input/>` 包起來。
* 垂直擺放 `<label/>` 和 `<input/>`，這樣做的好處是當使用者在螢幕寬度比較窄的情況下登入，不用擔心輸入框會變窄，甚至在 layout 上也不用糾結到底要不要統一 `label` 的長度（真的會在意ＸＤ）。
* 可以使用 `placeholder` 屬性，但不要拿來當 label 使用。原因是當使用者輸入完 `input` 之後，`placeholder` 便會消失，這會讓使用者搞不清楚現在有哪些 `input` 輸入完了。
* 在登入的時候不要有重複的欄位（不過這感覺在註冊比較常見）

</br>
</br>
<img width="80%" alt="Submit button" src="/images/bestPracticeFormSignin/submit-button.jpg">

* 按鈕要用 `<button/>` 而不是其他 HTML tag (e.g., `<div/>`)。而除了不要亂用 HTML tag 外，作者也有提到其他操作要注意的地方。例如送出按鈕要確實表明目的，不要用太含糊的文字、送出後要暫時 disabled 送出按鈕、

### 排版
<img width="80%" alt="Spaces between inputs" src="/images/bestPracticeFormSignin/spaces-between-inputs.jpg">

* 因為現在大部分的人還是用大拇指操作手機的，所以要注意欄位和欄位之間的間距，避免使用者有誤觸的可能，在視覺上也比較整潔。如果有錯誤提示的話也要能夠清楚分辨是哪個欄位的。

</br>
</br>
<img width="80%" alt="Input with border" src="/images/bestPracticeFormSignin/clearly-border.jpg">

* `<input/>` 本身的 border 要清晰
* 要注意在 Desktop 和 Mobile 上的字體是否太小，例如在 Desktop 上可能大小適中，但在 Mobile 上看就不太適合（作者也有提到 lighthouse 也會做相關的分析，有機會可以玩看看）

</br>
</br>
<img width="80%" alt="Amazon Sign-In" src="/images/bestPracticeFormSignin/amazon-signin.jpg">

* 避免手機裝置在顯示 keyboard 時擋住送出按鈕，這會增加使用者的困擾。作者就以 Amazon 來當例子，把輸入 email 和 password 分成兩個步驟，這也讓使用者一次只完成一件事

### 表單驗證
<img width="80%" alt="validate with CSS" src="/images/bestPracticeFormSignin/validate-with-css.jpg">

* 如果能用瀏覽器原生的表單驗證（例如：`<input/>` 加上 `required` 來表示必填欄位）加上 css 去滿足需求，可以考慮不要用 javascript。有興趣可以參考MDN寫的[這篇](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation)

</br>
</br>
<img width="80%" alt="Show error message correctly" src="/images/bestPracticeFormSignin/show-invalied-message.jpg">

* 如果真的需要客製化錯誤提示，盡量要能 realtime 的給使用者 feedback，而不是當使用者都填完並在送出的前一刻才知道原來有一堆欄位錯誤

### Input Attributes
* 在第一個 input 加上 `autofocus`，這確保使用者快速且清楚知道要從哪開始

</br>
</br>
<img width="80%" alt="Auto save and fill input value" src="/images/bestPracticeFormSignin/auto-save.jpg">

* `type=password` 協助瀏覽器在送出時詢問使用者是否要記住密碼，方便瀏覽器 autofill (下一段會提到)

</br>
</br>
<img width="80%" alt="Input with email type" src="/images/bestPracticeFormSignin/email-validation.jpg">

* `type=email` 協助手機裝置在使用者點擊後會開啟適當的 keyboard，瀏覽器也會做簡單的 validation

</br>
</br>
<img width="80%" alt="Input with tel type" src="/images/bestPracticeFormSignin/type-tel.jpg">

* `type=tel` 協助手機裝置在使用者點擊後開啟 telephone keyboard
* `inputmode=numeric` 協助手機裝置開啟 pin number keyboard

### Autofill
* `name=${name}` 搭配 `autocomplete="on"` 讓瀏覽器儲存和自動填入該欄位

</br>
</br>
<img width="80%" alt="New password" src="/images/bestPracticeFormSignin/new-password.jpg">

* 要避免在註冊表單和登入表單混用欄位名字。假設有 A 和 B 兩個使用者用同個裝置，A 登入成功且瀏覽器也存了 A 的密碼，幾天之後 B 也想註冊該網站，這時如果註冊表單和登入表單的密碼欄位用的都是 `type=password`，會導致瀏覽器意外地把 A 的密碼自動帶入到 B 的註冊表單。比較好的做法可以讓註冊表單的密碼為 `name=new-password` 而登入表單的密碼為 `name=current-password｀，或直接讓註冊表單的密碼欄位 `autocomplete="off"`

### 其他
* 不要讓使用者尋找 signup/signin button
* 在向使用者要求其他資訊（信用卡、地址）時，要向使用者說明用途
* 盡量讓使用者用電話來註冊而不是信箱
* 要讓重設密碼的連結容易被找到
* 清楚說明 link to terms and policies，讓使用者清楚知道他們的資料會被怎麼被使用
* 確保登入和註冊表單和品牌的的風格一致

### 總結
<img width="80%" alt="Conclusion" src="/images/bestPracticeFormSignin/conclusion.jpg">
最後有提到，雖然有很多工具能夠幫我們，但最重要的還是要進行 RUM (Real user measurement) or monitoring（例如：signup/signin view）, bounce rate, web performance, interaction analytics（例如：利用 goal funnels 了解使用者在 flow 的哪個階段放棄或是做了哪些 interaction）
