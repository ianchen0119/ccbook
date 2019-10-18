# 分離編譯與連結

至今為止，我們各用了一個C程式和 shell 腳本檔案的架構來進行開發。這樣的架構也沒有什麼問題，但是漸漸程式碼變得愈來愈長，差不多可以把C的部份分割成複數個檔案來改善程式的閱讀性了。在這一步，我們要把 9cc.c 這個檔案分割成以下5個檔案：

* `9cc.h`: 標頭檔
* `main.c`: `main`函式
* `parse.c`: 分析器
* `codegen.c`: 指令產生器
* `container.c`: 向量（vector）、對應（map），與所對應的測試程式碼

`main`函式很小，可以塞進別的C程式檔裡，但是從意義上來看並不屬於 parse.c 或 codegen.c 的任一個，所以獨立為1個檔案。

本章會介紹分離編譯的概念並說明其意義，然後會說明具體執行的步驟。
