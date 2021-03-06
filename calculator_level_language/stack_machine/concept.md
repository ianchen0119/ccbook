# 堆疊機的概念

堆疊機是指有堆疊資料儲存空間的電腦。所以堆疊機會有「推入堆疊」（stack push）和「從堆疊裡彈出」（stack pop）這兩個基本操作。推入就是在堆疊的最上面放上新的元素，彈出則是從堆疊的最上方取出元素。（譯註：堆疊是具有 LIFO 特性的一種資料結構。LIFO：Last-In-First-Out，最後放進的東西會最先被取出。）

堆疊機的運算，只對堆疊頂端的元素作用。舉例來說，堆疊機的`ADD`指令，會從堆疊頂端彈出兩個元素，將其加起來後把結果推入回堆疊（為了避免和 x86-64 指令混淆，假想堆疊機指令以大寫文字方式表示）。換句話說，`ADD`指令就是把堆疊頂端的2個元素，換成1個他們相加結果的元素的指令。

`SUB`、`MUL`、`DIV`指令也和`ADD`一樣，是把堆疊頂端的2個元素，作減法、乘法和除法計算，用1個元素來取代的指令。

`PUSH`指令是把引數上的元素放到堆疊上的指令。還有現在不會用到的，從堆疊頂端取出1個元素的`POP`指令。

接下來，利用這些指令，我們來考慮一下`2*3+4*5`的計算。使用上述定義的堆疊機，我們應該可以如下列程式來計算`2*3+4*5`：

```text
// 計算2*3
PUSH 2
PUSH 3
MUL

// 計算4*5
PUSH 4
PUSH 5
MUL

// 計算2*3 + 4*5
ADD
```

來仔細看一下這段程式。假設堆疊裡已經放了某些值，這些值並不重要我們以「`⋯`」來表示。堆疊成長的方向是由上往下。

開始的`PUSH`把2和3給推入堆疊裡，所以在執行`MUL`時堆疊裡的狀態是：

| ⋯ |
| :---: |
| 2 |
| 3 |

`MUL`從堆疊頂部取出2個元素，也就是`3`和`2`，相乘之後把其結果，也就是6給推進堆疊。底下是`MUL`執行後堆疊的狀態：

| ⋯ |
| :---: |
| 6 |

接著`PUSH`把4和5推進堆疊，所以在第2個`MUL`執行前堆疊變成下面這樣：

| ⋯ |
| :---: |
| 6 |
| 4 |
| 5 |

在這邊執行`MUL`，`4`和`5`會被取出，被換成其相乘結果的`20`。底下是`MUL`執行後的狀態

| ⋯ |
| :---: |
| 6 |
| 20 |

可以發現現在堆疊裏面已經放好了`2*3`和`4*5`的結果。在這個狀態下執行`ADD`就會計算`20+6`，然後該結果被推進堆疊，最終堆疊會長這樣：

| ⋯ |
| :---: |
| 26 |

堆疊機的計算結果就是堆疊裡最後留下的值，而`26`就是`2*3+4*5`的答案，所以算式的計算結果是正確無誤的。

堆疊機不僅限於此式，而可以計算任意有暫時要紀錄答案的算式。使用堆疊機，任意算式的一部份，只要遵守將其執行結果放在堆疊的規定，按照上述的方法都能正確編譯出來。

{% hint style="info" %}
#### 小知識：CISC 和 RISC

x86-64是由1978年發售的8086逐步發展而成的指令集，也就是俗稱「CISC」派的處理器。CISC 處理器的特徵，是機械語言的計算不只可以對暫存器進行，也可以用在記憶體位址；還有機械語言的的指令長度可變；還有許多對組合語言的程式設計師來說很方便的，有許多把複雜的操作用1條指令來完成的指令。

而相對於 CISC 的，就是在1980年代發明的「RISC」。RISC 處理器的特徵，是運算只能對暫存器進行；對記憶體的操作只有讀取到暫存器、和從暫存器寫入記憶體2種；所有機械語言指令長度都一樣；不具有給組合語言的程式設計師方便的複合命令，只有讓編譯器使用的簡單指令等等。

x86-64是 CISC 少數活到今天的一支，除了x86-64以外幾乎都是以 RISC 為基礎設計的。具體來說像是 ARM、PowerPC、SPARC、MIPS、RISC-V 都是 RISC 處理器。

RISC 並沒有像是 CISC 那像可以在記憶體和暫存器之間進行運算的指令，暫存器也沒有別名（alias），更沒有特定整數暫存器有特別使用方法的規定。從這類指令集成為主流的今天看來，x86-64指令集看起來可能特別老舊。

RISC 處理器因為其單純的設計而容易加速，因而席捲業界。那位什麼x86-64能活下來呢？那是因為有著想要利用現有的軟體資產、追求高速x86處理器的大量市場需求，和 Intel 或 Intel 相容晶片廠商回應了這些需求所做的的技術革新。Intel 把CPU指令解碼，在x86指令在處理器內部轉換成某種 RISC 指令，把x86的內部架構改成 RISC 處理器，讓把 RISC 高速化的技術變成可以應用在x86之上。
{% endhint %}

