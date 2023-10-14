###### tags: `2023鐵人賽` `qiita` `AWS` `Roadmap`
# [2023 15th鐵人賽] Day29 - AWS Engineer Roadmap 2023

> 原文連結：[AWSエンジニアロードマップ2023](https://qiita.com/KurokawaKouhei/items/3836802fc3a0286f668f)

終於來到了這篇，其實當初在決定要報名今年鐵人賽的時候，是想要從 AWS 主題著手，但一方面沒什麼自信能夠在三十天內寫出完整架構，一方面也還在摸索學習的步調。

本篇文章將會介紹 AWS 學習指標，部分圖解和影片以日文為主，但透過 Roadmap 還有每週主題，還是能夠參考並安排自己的學習進度，架構如下所示：

+ 第 1 週：AWS 基礎知識（AWS Basics）
+ 第 2～3 週：網路與內容傳遞（Networking and Content Delivery）
+ 第 4 週：運算服務（Compute Services）
+ 第 5 週：安全、身份和合規性（Security, Identity, and Compliance）
+ 第 6 週：資料庫（Database）
+ 第 7 週：儲存（Storage）
+ 第 8 週：管理和管控治理（Management and Governance）
+ 第 9 週：容器、無伺服器運算、應用程式整合（Containers and Serverless Computing, Application Integration）
+ 第 10 週：分析、遷移、其他（Analytics, Migrations）
+ 第 11〜12 週：SAA 認證模擬測驗
    + 練習 SAA 的注意事項

實際學習主要還是建議搭配 [AWS 官方文件](https://docs.aws.amazon.com/zh_tw/?nc2=h_ql_doc_do)，或是其他線上課程等管道來進行。此外，也給自己訂下目標，希望今年結束前能夠達成，有機會的話，到時候再來整理一篇更詳細的準備心得。

那麼，以下正文開始。

---

[toc]

![](https://i.imgur.com/gDb4iD0.png)

- 將 AWS 的學習路線統整後，以「路線圖風格」呈現。
- 黃色的圓圈代表重要的項目。
- 「完全沒有 AWS 經驗」的人來說，通常需要約「3 個月」的學習時間才能「通過 SAA 取得證照資格」。

（對於有經驗的人來說，可以在更短時間內通過考試。）

- 通過 SAA 測驗後，建議學習其他證照內容的同時，需搭配實際操作來學習。

即使是 ChatGPT，應該無法提供這樣的路線圖⛅️

## 第 1 週：[AWS 基礎知識（AWS Basics）](https://aws.amazon.com/tw/getting-started/)

首先，以下整理一下有關「AWS」和「傳統的 IT 基礎架構」的基本知識。
為什麼 AWS 會受到如此多的關注？瞭解 AWS 擁有哪些優勢非常重要。

<iframe width="734" height="413" src="https://www.youtube.com/embed/156B6cZ_2aQ" title="AWSが使われる理由、クラウドサービスのメリット、なぜ今AWSを学ぶべきなのか？【11:32】" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

就地部署軟體（On-Premises）的缺點如下：

- 需要大量的初期成本
- 需要預測容量（Capacity）
- 從購買到部署伺服器，通常需要約一個月的時間

等項目。

另一方面，AWS 能夠根據實際使用量來支付費用，因此不需預測容量。

可以立即使用、從任何地方連接，且應用標準化的技術。

基於上述幾項特點，可預期 AWS 的優勢將遠高於就地部署軟體，並且在成本、彈性和可訪問性等方面能夠得到提升。

![](https://hackmd.io/_uploads/Skq9SoSba.png)

<iframe width="708" height="315" src="https://www.youtube.com/embed/nNWdBqdbn9w" title="AWSグローバルインフラストラクチャ【4:50】" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

> [更多 AWS 相關基礎知識的影片可參考這裡](https://www.youtube.com/playlist?list=PL2nCE2iR-lpm7XFAJR0ngD1rkheHgX_0b)

## 第 2～3 週：[網路與內容傳遞（Networking and Content Delivery）](https://aws.amazon.com/tw/products/networking/)

[VPC](https://docs.aws.amazon.com/zh_tw/vpc/latest/userguide/what-is-amazon-vpc.html) 是最重要的項目。應具備網路知識，如果對[子網路遮罩](https://zh.wikipedia.org/zh-tw/%E5%AD%90%E7%BD%91)或[無類別域間路由（CIDR）](https://zh.wikipedia.org/zh-tw/%E6%97%A0%E7%B1%BB%E5%88%AB%E5%9F%9F%E9%97%B4%E8%B7%AF%E7%94%B1)計算不熟悉，則需要複習這部分內容。

<iframe width="781" height="439" src="https://www.youtube.com/embed/2317shavNoo" title="【VPC講座1】リージョン / アベイラビリティゾーン / サブネット【9:02】" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

對於 [Route 53](https://aws.amazon.com/tw/route53/)，只要能瞭解必備知識 DNS，與名稱解析相關的概念，就不會太困難。
由於 [CloudFront](https://aws.amazon.com/tw/cloudfront/) 設定項目較多，如果在初期階段過於深入研究，可能會因此感到挫折。

![](https://hackmd.io/_uploads/SyyLLsSZ6.png)

## 第 4 週：[運算服務（Compute Services）](https://docs.aws.amazon.com/zh_tw/whitepapers/latest/aws-overview/compute-services.html)

瞭解如何購買 [EC2](https://aws.amazon.com/tw/ec2/)，對於考試和實務都非常重要，這部分也須充分理解。
如果只是建立伺服器，可透過圖形使用介面（GUI）在一分鐘內搞定，而進一步架構和維護，瞭解 Linux 的基本知識和命令更為重要。

![](https://hackmd.io/_uploads/HyqIIiBZp.png)

[Auto Scaling](https://aws.amazon.com/tw/autoscaling/) 則需要瞭解各種擴展策略（Scaling Policies）的差異。

![](https://hackmd.io/_uploads/HJ_KUiBZa.png)

[Elastic Beanstalk](https://aws.amazon.com/tw/elasticbeanstalk/)
只需掌握服務概述，並試著實際運行即可（以下是 [Web 伺服器環境](https://docs.aws.amazon.com/zh_tw/elasticbeanstalk/latest/dg/concepts-webserver.html)，還有[工作者環境](https://docs.aws.amazon.com/zh_tw/elasticbeanstalk/latest/dg/concepts-worker.html)也需掌握）。

![](https://hackmd.io/_uploads/BJ6_LoSb6.png)

## 第 5 週：[安全、身份和合規性（Security, Identity, and Compliance）](https://aws.amazon.com/tw/architecture/security-identity-compliance/)

AWS 除了以一般的密碼方式，還使用[基於角色型的存取控制（RBAC）](https://docs.aws.amazon.com/zh_tw/redshift/latest/dg/t_Roles.html)功能進行權限管理。透過瞭解[角色的概念](https://docs.aws.amazon.com/zh_tw/IAM/latest/UserGuide/id.html)以及如何[建立 IAM 政策](https://docs.aws.amazon.com/zh_tw/IAM/latest/UserGuide/access_policies_create.html)，將能夠從容地處理權限錯誤等問題。

![](https://hackmd.io/_uploads/rkB9IoB-p.png)

[Cognito](https://docs.aws.amazon.com/zh_tw/cognito/latest/developerguide/what-is-amazon-cognito.html) 是一項受管服務，用於控制對 Web 和行動應用程式的存取，提供使用者註冊和登入的身份驗證功能。

![](https://hackmd.io/_uploads/HyE3LoBbT.png)

## 第 6 週：[資料庫（Database）](https://aws.amazon.com/tw/products/databases/)

瞭解如何區別 [Relational Database Service（RDS）](https://aws.amazon.com/tw/rds/) 的 [Multi AZ 部署](https://aws.amazon.com/tw/rds/features/multi-az/) 和[讀取複本（Read Replica）](https://aws.amazon.com/tw/rds/features/read-replicas/)非常重要。。

![](https://hackmd.io/_uploads/SyNTUiB-T.png)

此外，也需瞭解 [NoSQL 的 DynamoDB](https://aws.amazon.com/tw/dynamodb/) 和記憶體資料庫的 [ElastiCache](https://aws.amazon.com/tw/elasticache/) 等，以及與傳統的[關連式資料庫管理系統（RDBMS）](https://zh.wikipedia.org/zh-tw/%E9%97%9C%E8%81%AF%E5%BC%8F%E8%B3%87%E6%96%99%E5%BA%AB%E7%AE%A1%E7%90%86%E7%B3%BB%E7%B5%B1)的不同之處。

![](https://hackmd.io/_uploads/SydgRdvbp.png)

## 第 7 週：[儲存（Storage）](https://aws.amazon.com/tw/products/storage/)

需要理解 [Amazon Simple Storage Service（Amazon S3）儲存類別](https://aws.amazon.com/tw/s3/storage-classes/)，以及把握三種 [Glacier](https://aws.amazon.com/tw/s3/storage-classes/glacier/) 的特性。

![](https://hackmd.io/_uploads/r1IQDiHba.png)

## 第 8 週：[管理和管控治理（Management and Governance）](https://aws.amazon.com/tw/products/management-and-governance/)

在工作現場，通常需要設定 [Session Manager](https://docs.aws.amazon.com/zh_tw/systems-manager/latest/userguide/session-manager.html)，因此需要能夠在不查看文件的情況下進行設定。

儘管初學者可以透過 [Teraterm](https://zh.wikipedia.org/zh-tw/Tera_Term) 的 SSH 連接來理解如何運作，但目前這種連接方式已經有點過時。

![](https://hackmd.io/_uploads/S1CMwoSWa.png)

## 第 9 週：[容器](https://aws.amazon.com/tw/containers/)、[無伺服器運算](https://aws.amazon.com/tw/serverless/)、[應用程式整合](https://aws.amazon.com/tw/products/application-integration/)（Containers and Serverless Computing, Application Integration）

理解 [Elastic Container Service（ESC）](https://aws.amazon.com/tw/ecs/)的結構至關重要。特別是理解[任務定義（Task Definition）](https://docs.aws.amazon.com/zh_tw/AmazonECS/latest/developerguide/task_definitions.html)的必備知識 [Dockerfile](https://docs.docker.com/engine/reference/builder/)。

![](https://hackmd.io/_uploads/BJ2bwsrWa.png)

## 第 10 週：分析、遷移、其他（Analytics, Migrations）

需記住 [Kinesis Data Streams](https://aws.amazon.com/tw/kinesis/data-streams/) 是即時的，[Firehose](https://aws.amazon.com/tw/kinesis/data-firehose/) 則幾乎是即時的，熟記這點或許對考試得分有所幫助。

[Kinesis Data Streams](https://aws.amazon.com/tw/kinesis/data-streams/) 是即時的：

![](https://hackmd.io/_uploads/HywNvsSWT.png)

[Kinesis Data Firehose](https://aws.amazon.com/tw/kinesis/data-firehose/) 是幾乎即時的：

![](https://hackmd.io/_uploads/HJDrDoSZT.png)

## 第 11〜12 週：SAA 認證模擬測驗

最後，建議參加「[SAA - 解決方案架構師](https://aws.amazon.com/tw/certification/certified-solutions-architect-associate/)」認證考試，作為知識的客觀證明。

即使對完全沒有經驗的人來說，也能夠在三個月內取得認證資格。

然而，除了取得認證以外，透過實際操作來取得實作技能並加深理解，將能夠提高在該領域解決問題的能力以及適應力，成為更有價值的技術人員」。

測驗費用：16,500 日圓（含稅） = 150 USD
全年可以考試：可以線上或在最近的測試中心參加考試

### 練習 SAA 的注意事項

建議使用符合以下條件的練習問題集：

:::success
- 問題的質量是否達到正式考試水平

**解答大量質量低下的問題等同是在浪費時間**，應該避免花時間在不太重要的問題上。相對於盲目地解答大量質量低下的問題，透過多次解答正式考試水平的問題 3～4 次（大約 200 到 260 道問題），將能更有效地提高技能。
:::

:::success
- 解答是否易於理解

為了使初學者更容易理解，**除了文字以外，還應提供相關的圖片解說**。

這將有助於更深入理解概念，並提升學習效率。
:::

:::warning
- 是否有能夠提問的環境

如果在學習過程中，無法妥善解決疑問，可能會成為進入下一個主題的障礙，導致學習進度緩慢。透過有一個能夠提問的環境，將能迅速解決疑問，以順利推進學習不掉，還可以防止失去動力。
:::

## 最後

感謝您看到最後！希望這個路線圖對於學習指標或公司培訓有所幫助。

如果對路線圖有任何想法，請在 Qiita 的評論中，或透過 [Twitter](https://twitter.com/AwsskillC/status/1636877330244321280?s=20) 發送私訊給筆者，期待聽到建設性的回饋！

那麼！預祝擁有美好的 AWS Life！
