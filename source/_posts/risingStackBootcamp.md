---
title: RisingStack bootcamp - 一個精實的 Nodejs 練習專案
tags:
  - training
  - nodejs
---

### 前言
相信大部前端工程師都和我一下，在一開始踏入後端領域會先從 Nodejs 開始。一來是學習成本小很多，二來是現在網路上能找到關於 Nodejs 的教學資源真的很多，例如大家可能非常熟悉的 **MEAN**  stack (MongoDB, Express, Angular, Nodejs) 或是 **MERN** stack (Angular 換成 React)。可是大部分的學習資源還是會以基礎為主，畢竟這對初學者而言會比較容易吸收，那在這些基礎概念都掌握之後，如果想學習更進階的概念或是系統性的學習後端呢？

### About this Bootcamp
前陣子發現了 RisingStack 提供給給 newcomer 的 [bootcamp](https://github.com/RisingStack/risingstack-bootcamp)。相信平常有在看 Nodejs 技術文章的人應該對 RisingStack 不陌生，許多文章也都蠻值得一看。而他們主要是從事 consulting 的服務，包括 fullstack development 到 devop, SRE 應有竟有。而這個 bootcamp 也是協助 newcomer 更系統性的學習 Nodejs，這裡剛好有篇內部工程師分享一些完成 bootcamp 之後的[心得](https://blog.risingstack.com/node-js-bootcamp/)。

要注意的是 Bootcamp 有些功能是階段性的，代表進到下一個階段之前一定要確定上個階段的功能都有完成，建議 checkbox 盡量都完成啦ＸＤ。而我覺的這個 bootcamp 很讚的地方是每個階段都會提供詳細的 spec 和參考的資源，像是 [12 factor](https://12factor.net/processes)的文章就出現蠻多次的，其他像是[這篇](https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)討論到該如何設計實用的 APIs 也很值得一讀，這讓初學者不會在毫無概念的情況下不知道該從何做起。

而內容會從最基本的 web server 到最後會需要處理正式環境會遇到的問題，這裡就來簡單說明一下會接觸到的部分：
1. web server (Koa)
2. 串接 Github 的服務 (Restful or GraphQL)
3. RDBMS (postgresql)
4. Workers (Redis)
5. RESTFul Apis
6. Graceful shutdown server
7. Docker (這我自己補的ＸＤ)

而開始的方式也很簡單，Repo 拉下來後會發現解答都已經被 commit 了，只要把 commit reset 最原始的版本，完成之後再來參考解法，畢竟要自已動手做過才能真正吸收進去。

### 結論
有沒有發現其實會接觸到的概念並不少（對初學者來說），建議可以在看完參考資源後先不要急著開始動手做，可以多花些時間了解相關的知識後在開始。我自已大概花了幾個週末來完成這個 bootcamp，期間也都是邊做邊複習以前學過的知識，也有微調一些作法，例如 DB 的操作我就直接用 `knex.raw` 而不是用 knex 提供的 methods。之後也會不定期分享一些不錯的學習資源

