---
title: WHERE和HAVING
categories:
  - MySQL必知必会
toc: true 
---

- 需要查询出一个商品记录集，限定条件是单笔销售金额超过 50 元-->2者结果一样
  ![image-20211007164836324](C:\Users\chenjiaxi\AppData\Roaming\Typora\typora-user-images\image-20211007164836324.png)

  

- WHERE——先从数据表 demo.transactiondetails 中抽取满足条件“a.salesvalue>50，然后连接goodsmaster，再DISTINCT
  也就是先限定金额>50的流水，再把商品名字加过去

- ![image-20211007154747965](C:\Users\chenjiaxi\AppData\Roaming\Typora\typora-user-images\image-20211007154747965.png)

- HAVING查询过程——

- ![image-20211007165757837](C:\Users\chenjiaxi\AppData\Roaming\Typora\typora-user-images\image-20211007165757837.png)

  - 先把有关的信息从关联表都连接好
  - 对数据集进行分组，形成一个包含所有需要的信息的数据集合
  - 通过 HAVING 条件的对集合筛选，得到需要的数据

- WHERE和HAVING区别：如果需要通过连接从关联表中获取需要的数据，WHERE 是先筛选后连接，而 HAVING 是先连接后筛选。

  - WHERE 比 HAVING 更高效

  - HAVING 必须要与 GROUP BY 配合使用，特点是可以把分组计算的函数作为筛选条件，而WHERE运行在GROUP BY前，它无法做到这样的查询。

  - 2者不互斥——要查询“2020-12-10”和“2020-12-11”这两天收银金额超过 100 元的销售日期、收银员名称、销售数量和销售金额。

    ![image-20211007171731122](C:\Users\chenjiaxi\AppData\Roaming\Typora\typora-user-images\image-20211007171731122.png)

