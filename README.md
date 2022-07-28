# learning-aws-scs-c01

[AWS Certified Security - Specialty](https://aws.amazon.com/jp/certification/certified-security-specialty/) の試験勉強用のリポジトリです。

- [learning-aws-scs-c01](#learning-aws-scs-c01)
  - [試験ガイド](#試験ガイド)
  - [学習用コンテンツ](#学習用コンテンツ)
    - [サンプル問題](#サンプル問題)
    - [AWS Certified Security - Specialty 公式練習問題集(Official Practice Question Set)](#aws-certified-security---specialty-公式練習問題集official-practice-question-set)
    - [公式トレーニング](#公式トレーニング)
      - [インシデントへの対応](#インシデントへの対応)
      - [ログと監視](#ログと監視)
      - [インフラストラクチャのセキュリティ](#インフラストラクチャのセキュリティ)
      - [ID 及びアクセス管理](#id-及びアクセス管理)
      - [データ保護](#データ保護)

## [試験ガイド](https://d1.awsstatic.com/ja_JP/training-and-certification/docs-security-spec/AWS-Certified-Security-Specialty_Exam-Guide.pdf)

- 対象者
  - IT セキュリティに関してセキュリティソリューションの設計と実装における 5 年以上の経験
  - AWS ワークロードのセキュリティ保護における 2 年以上の実務経験
- 推奨される AWS に関する知識
  - AWS の責任共有モデルとそのアプリケーション
  - AWS のワークロードのセキュリティ管理
  - ログ記録戦略とモニタリング戦略
  - クラウドセキュリティの脅威モデル
  - パッチ管理とセキュリティの自動化
  - サードパーティーのツールやサービスで AWS セキュリティサービスを強化する方法
  - BCP とバックアップを含む災害対策管理
  - 暗号化
  - アクセスコントロール
  - データ保持

- 試験内容の概要
  - 第 1 分野: インシデントへの対応 12%
  - 第 2 分野: ログ記録とモニタリング 20%
  - 第 3 分野: インフラストラクチャのセキュリティ 26%
  - 第 4 分野: アイデンティティ管理とアクセス管理 20%
  - 第 5 分野: データ保護 22%

## 学習用コンテンツ

### 書籍による学習

[要点整理から攻略する『AWS認定 セキュリティ-専門知識』](https://www.amazon.co.jp/dp/B08DCLRHC7/ref=dp-kindle-redirect?_encoding=UTF8&btkr=1)を購入。  
ただし2020年の本なので、直近2年にリリースされたサービスや変更点はカバーされていない。  
コントロールタワーなども対応していないので、新しいサービスは個別に公式ドキュメントを読み込む必要がある。

### [サンプル問題](https://d1.awsstatic.com/ja_JP/training-and-certification/docs-security-spec/AWS-Certified-Security-Speciality_Sample-Questions.pdf)

- 腕試しには以下の Official Practice Question Set を使用した方が良い
- 初見で7割解けたが、Official Practice Question Set の方が問題の難易度は遥かに高い

### [AWS Certified Security - Specialty 公式練習問題集(Official Practice Question Set)](https://explore.skillbuilder.aws/learn/course/external/view/elearning/12551/aws-certified-security-specialty-practice-question-set-scs-c01-japanese?ss=sec&sec=prep)

### [公式トレーニング](https://explore.skillbuilder.aws/learn/course/762/exam-readiness-aws-certified-security-specialty-japanese)

#### インシデントへの対応

- 以下の方法を知っている必要がある
  - AWS への不正使用の通知に応じて、侵害されたインスタンスや漏洩したアクセスキーの特定
  - インシデント対応計画に適切な AWS サービスが含まれていることを確認
  - 自動アラートの設定内容を評価し、セキュリティ関連のインシデントや問題への対策を講じる
- インシデント発生時、特定のインスタンスをネットワークから切り離す時はセキュリティ・グループの変更で対応する
  - インスタンスを終了することで影響を止めることはできるが、調査ができなくなる
- インシデント対応向けのサービス
  - AWS Trusted Advisor
  - AWS CloudFormation
  - AWS ServiceCatalog
  - VPC フローログ
    - 送信元と送信先の IP アドレス、ポート、プロトコル、開始時刻と終了時刻、パケット数とバイト数、アクションをキャプチャする個々のレコードで構成されるログ
  - AWS Config
  - Amazon API Gateway
  - AWS CloudTrail
  - Amazon CloudWatch
- インシデントの兆候
  - ログとモニタリング
  - 請求の記録
  - 脅威インテリジェンス
  - AWS サポート
  - パブリックレスポンス
- IAM アクセスキーが漏洩した場合
  - 認証情報を無効化する
  - 侵害された認証情報がアタッチされたユーザーに、IAM を拒否するポリシーをアタッチする
    - さらに、残っているセッションを全て取り消す
  - アクセスキーが関連づけられているユーザーを確認する
    - アクセスキーに関連づけられているポリシーの範囲を調べる
  - CloudTrail と AWS Config を使用して何か変更していないかを確認する
    - 他のキーや認証情報が漏洩していないかを最後に確認する
- AWS GuardDuty
  - CloudTrail, DNS log, VPC flow log からデータを収集する
  - 悪意のある操作や不正な動作を継続的にモニタリングし、AWS アカウントとワークロードを保護
  - 脅威の可能性が検出されると、GuardDuty コンソールと CloudWacth にセキュリティ・アラートを配信

#### ログと監視

- 以下の方法を知っている必要がある
  - セキュリティモニタリングとアラートの設計と実装
  - セキュリティモニタリングとアラートのトラブルシューティング
  - ロギングソリューションの設計と実装
  - ロギングソリューションのトラブルシューティング
- モニタリング用の AWS サービス
  - Amazon CloudWatch
    - [How Amazon CloudWatch works](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_architecture.html)
    - AWS 組み込みメトリクスとカスタムメトリクスをモニタリングする
    - サービスとアプリケーションのログファイルを収集して処理する
    - イベントを検出し、通知または自動応答により応答する
  - AWS Config
    - リソースの全設定変更について詳細情報を継続的にキャプチャする
    - コンプライアンス分析とセキュリティ分析を有効化
    - セキュリティを侵害するような設定変更を特定し、影響を軽減できる
  - AWS Inspector
    - 以下を含むサポートされているベースラインに基づいてスキャンを実行
      - CVE
      - CIS ベンチマーク
      - セキュリティのベストプラクティス
      - Network reachability
  - AWS CloudTrail
- Amazon Kinesis
  - リアルタイムのストリーミングデータを収集、処理、分析する
    - 取り込み
      - Amazon Kinesis Data Streams
      - Amazon Kinesis Data Firehose
        - コンテンツを直接ストレージに格納する
    - 解析
      - Amazon Kinesis Data Analytics
- Amazon Athena
  - S3 内のデータを標準 SQL で分析できるインタラクティブなクエリサービスを提供

#### インフラストラクチャのセキュリティ

- 以下の方法を知っている必要がある
  - AWS のエッジセキュリティの設計
  - セキュアなネットワークインフラストラクチャの設計と実装
  - セキュアなネットワークインフラストラクチャのトラブルシューティング
  - ホストベースのセキュリティの設計と実装
- エッジセキュリティ用の AWS ツール
  - [Amazon Route 53](https://aws.amazon.com/jp/route53/)
    - DNS サービス
    - 他の AWS サービスと連携するように設計できる
  - [AWS WAF](https://aws.amazon.com/jp/waf/)
  - [Amazon CloudFront](https://aws.amazon.com/jp/cloudfront/)
    - CDN
  - [AWS Shield](https://aws.amazon.com/jp/shield/)
    - ネットワークおよびトランスポートレイヤーを防御
- AWS WAF の条件
  - SQLi や XSS のような一般的な攻撃パターンをブロックするカスタムルールや、特定のアプリケーションのために設計されるルールを作成できる
  - リクエストを許可またはブロックする基準
    - クロスサイトスクリプティングの一致
    - IP の一致
    - 地理的な一致
    - サイズの制約
    - SQL インジェクションの一致
    - 文字列の一致
    - 正規表現の一致
- DDoS 攻撃を軽減するための AWS ツール
  - Amazon Route 53
  - Amazon CloudWatch
  - AWS WAF
  - [Elastic Load Balancing](https://aws.amazon.com/jp/elasticloadbalancing/)
  - Amazon CloudFront
  - Amazon API Gateway
  - [AWS Shield](https://aws.amazon.com/jp/shield/)
  - [Amazon EC2 Auto Scaling](https://aws.amazon.com/jp/ec2/autoscaling/)
- ネットワーク ACL
  - サブネットレベルで作成、管理される
  - ステートレスなトラフィックフィルター
  - リストを拒否、または許可するためのルール
- セキュリティグループ
  - インスタンスの仮装 Fire Wall として機能
  - ステートフルな防御
  - Ingress ルールと egress ルールのみを許可する
  - 通信を許可するには設定が必要
- AMI のセキュリティに関する考慮事項
  - 安全でないアプリケーションを無効化
    - クリアテキストによる認証を使用したサービスとプロトコルを無効化
  - 漏えいを最小化
    - 必須でないネットワークサービスを起動時に無効化
    - 必要がない場合は、ファイル共有、Print Spooler、RPC などのデフォルトのサービスを無効化
  - AMI の作成時に認証情報を保護
    - ディスクと設定ファイルから AWS とサードパーティのすべての認証情報を削除
    - すべてのユーザー SSH パブリックキーペアとプライベートキーペアを削除
    - すべてのユーザーアカウントのパスワードを削除および無効化

#### ID 及びアクセス管理

- 以下の方法を知っている必要がある
  - AWS リソースにアクセスするためのスケーラブルな認証および認可システムの設計と実装
  - AWS リソースにアクセスするための許可および認証システムのトラブルシューティング
- AWS ではインバウンドおよびアウトバウンドの通信とネットワークトラフィックをより包括的にモニタリングできるよう、クラウドへのアクセスポイント数を制限しており、これらのユーザーアクセスポイントは API エンドポイントと呼ばれる
- API の保護
  - 署名によってアイデンティティを確認し、改ざん、リプレイ攻撃を防止している（署名にはタイムスタンプが含まれる）
- アクセスポリシーの種類
  - AWS 管理
  - カスタマー管理
  - インライン
- IAM アクセス許可の決定方法
  - ポリシーは AWS のエンティティであり、アイデンティティやリソースにアタッチして、これらのアクセス許可を定義する
  - AWS はユーザーなどのプリンシパルがリクエストを行ったときに、それらのポリシーを評価する
  - 複数の条件を指定したり、単一の条件に複数のキーを指定したりすると、IAM は論理 AND 演算を使用してそれらを評価する
    - 1 つのキーに複数の値を使用して単一の条件を指定すると、IAM は論理 OR 演算を使用して条件を評価する
  - アクセス許可が付与されるには、すべての条件を満たしている必要がある
- ポリシーエレメント
  - JSON ポリシードキュメントはエレメントで構成されており、エレメントには次の 5 つの主要な種類がある
    - Effect: ステートメントの結果を許可または明示的な拒否のどちらにするかを指定する
    - Action: 許可または拒否される動作を指定する
    - Resource: Action の対象となるリソースを指定する
    - Condition: 実行する際に満たす必要のある条件を指定する
    - Principle: ポリシーがアタッチされたリソースにアクセス可能なリソースを指定するリソースベースのポリシーや信頼ポリシーに使用する
- ポリシー管理におけるセキュリティの考慮事項
  - 必要なユーザーにのみアカウントを作成し、それ以外の場合はロールとフェデレーションを利用する
  - インラインポリシーではなくカスタマー管理ポリシーを使用する
  - 各 IAM エンティティには最小限の権限のみを付与する
  - さまざまなエレメントを使用してポリシーサイズを削減する
- AWS Directory Service
  - Microsoft Active Directory を AWS のサービスから使用するために利用できる方法が複数ある
    - AWS Managed Microsoft AD
      - Microsoft AD が AWS クラウド内に必要なケース
    - AD Connector
      - オンプレミスのユーザーが AD を介して AWS のサービスにアクセスする必要があるケース
    - Simple AD
      - 小規模で低コストな基本的な AD の機能を提供する

#### データ保護

- 以下の方法を知っている必要がある
  - キーの管理の設計と実装
  - キー管理のトラブルシューティング
  - 保管中のデータおよび転送中のデータのためのデータ暗号化ソリューションの設計と実装
- データ保護のための AWS サービス
  - Amazon RDS
  - Amazon DynamoDB
  - [AWS Secrets Manager](https://aws.amazon.com/jp/secrets-manager/)
  - [Amazon S3 Glacier](https://aws.amazon.com/jp/s3/storage-classes/glacier/)
  - [Amazon S3 Glacier Vault](https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html)
- AWS Key Management Service
  - エンベロープ暗号化を使用した２層のキー階層
  - キーを一元的に管理し、セキュリティを保護
  - キーを使用できるユーザーを使用ポリシーで決定
  - 以下のことができる
    - ユニークなエイリアスと説明をつけたマスターキーを作成
    - マスターキーを自動的にローテート
    - キーの無効化、削除
    - CloudTrail を使用してキーの使用を監査
    - キーのインポート
  - キーの保護
    - リソースベースの権限
      - 一時的なアクセス権限、またはより詳細なアクセス権限
    - IAM ポリシーと類似した構文
      - カスタマーマスターキー (CMK) をプログラムで委任する
    - キーの管理、および暗号化/復号を行えるユーザーを指定
      - アクセスを許可するのに使用
- 転送中のデータ保護
  - クライアントとサービスエンドポイント間は TLS
  - パブリックキーインフラストラクチャ内で X.509 を使用
  - 証明書よりサーバーのアイデンティティを検証し、改ざんや偽造を防止
- AWS Certificate Manager
  - パブリックとプライベート両方の証明書を管理
  - 証明書のデプロイや自動更新を容易にする
- クライアント側の暗号化とサーバー側の暗号化
  - CSE 暗号
    - AWS に送信する前にユーザーがデータを暗号化する
    - データは暗号化された状態で保存
    - ユーザーのみが知っているキーとアルゴリズム。
  - SSE 暗号
    - 受信した後に AWS がユーザーに代わってデータを暗号化する
    - エンドユーザーに対して透過的
    - AWS は定期的にマスターキーをローテーションする
- Amazon S3 のデータアクセス保護
  - オブジェクト ACL
    - 個々のオブジェクトへのアクセス権限を付与
    - 別のアカウントが所有するオブジェクトにアクセスする
  - バケット ACL
    - ログ配信グループにバケットへの書き込みアクセスを付与する
  - バケットポリシー
    - バケット ACL よりも幅広いアクセス権限を付与する
    - バケットへのクロスアカウントアクセスを許可する
  - IAM ユーザーポリシー
    - ユーザーとグループを作成し、ポリシーをアタッチすることでアクセス権限を管理する
- ブロックパブリックアクセス
  - [Blocking public access to your Amazon S3 storage](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html)
  - 任意のアクセスコントロールリスト (ACL) を介して許可されたバケットとオブジェクトへのパブリックアクセスをブロックする
- Amazon RDS のデータ保護
  - 転送中の保護
    - TLS とネイティブ暗号化クライアントを使用
    - Amazon RDS がアクセス認証を処理
  - 保管中の保護
    - AES-256
    - DB 作成時に有効にする必要がある（後から有効化はできない）
    - 特定の DB エンジンで TDE をサポート
- Amazon  DynamoDB のデータ保護
  - 転送中の保護
    - TLS で暗号化されたエンドポイントを使用
    - HMAC-SHA256 署名つきのリクエストのみを許可
  - 保管中の保護
    - CSE または SSE 暗号化オプションをサポート
      - SSE だと AES-256
    - テーブルとインデックスを暗号化
- Amazon S3 Gracier
  - デフォルトで暗号化
  - S3 のライフサイクルルールでも転送できる
  - データ取得後24時間使用が可能
  - データは一括、またはセグメント単位で取得が可能
  - ボールトロック
    - 時間ベースの保持
    - MFA 認証のサポート
    - ロック後はポリシーの変更不可
    - Write Once Read Many のサポート
- AWS Secrets Manager
  - シークレットの安全なローテート
  - アクセスの管理
  - 一元的なセキュリティと監査
  - 従量課金制

## 模擬テストで補足する知見

- [DDoS シミュレーションテストポリシー](https://aws.amazon.com/jp/security/ddos-simulation-testing/)
- [Managing the AWS accounts in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts.html)
  - SCP や OU
