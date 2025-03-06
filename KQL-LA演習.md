---
title: 🔎Log AnalyticsのワークスペースでKQLを練習する🔍 
permalink: index.html
layout: home
---
# 🔎KQLとLog Analyticsについて☁️

## KQL
Kusto クエリ言語 (KQL) は、データの探索やパターンの検出、異常や外れ値の特定、統計モデリングの作成などを行う強力なツールです。 KQL は、構造化データ、半構造化データ、非構造化データに対してクエリを実行するための、シンプルでありながら強力な言語です。 この言語は表現力があり、読みやすく、クエリの意図を理解しやすく、作成エクスペリエンス用に最適化されています。 Kusto クエリ言語は、テキスト検索と解析、時系列演算子と関数、分析と集計、地理空間、ベクトル類似性検索、およびデータ分析に最適な言語を提供するその他の多くの言語コンストラクトを深くサポートするテレメトリ、メトリック、ログのクエリに最適です。 このクエリでは、SQL に似た階層 (データベース、テーブル、列) に編成されたスキーマ エンティティが使用されます。


## Log Analyticsワークスペース
Log Analytics ワークスペースは、すべての Azure および Azure 以外のリソースとアプリケーションから任意の種類のログ データを収集できるデータ ストアです。 ワークスペース構成オプションを使用すると、次の方法で、すべてのログ データを 1 つのワークスペースで管理し、組織内のさまざまな担当者の操作、分析、監査のニーズを満たすことができます。

<table>
  <tr>
    <th>⭐注目⭐</th>
  </tr>
  <tr>
    <td>Microsoft Sentinel では、"Microsoft Sentinel ワークスペース" という用語が使用されています。 このワークスペースは、Log Analytics ワークスペースと同じですが、Microsoft Sentinel で使用できるようになっています。 ワークスペース内のすべてのデータには、Microsoft Sentinel の価格が適用されます。</td>
  </tr>
</table>  


# ☁️Azureのアカウント作成☁️
❗既にアカウントをお持ちの方は次のセクションに進んでください。

まずは以下のリンクにアクセスしてください

<a href="https://azure.microsoft.com/ja-jp/pricing/purchase-options/azure-account" target="_blank">https://azure.microsoft.com/ja-jp/pricing/purchase-options/azure-account</a>

左側にある無料アカウントのオプションを選択

<img src="images/KQL1.png" alt="Azureアカウント" style="width:950px; height:500px;">

プロファイル情報を入力する

<img src="images/KQL2.png" alt="Azureアカウント" style="width:950px; height:500px;">

クレジットカードの情報を入力する
アカウント登録してから、1回アカウントに１００円ぐらいの料金が発生します。これはカードが有効か確認するためにあって、すぐ同じ金額が自動的に返されます。

<table>
  <tr>
    <th>ℹ️自動請求なし</th>
  </tr>
  <tr>
    <td>「お客様のクレジットが終了後、従量課金制を続行するかどうかお尋ねします。続行する場合、サービスの無料分を超えて使用した場合にのみ支払うことになります。」</td>
  </tr>
</table> 

<img src="images/KQL3.png" alt="Azureアカウント" style="width:950px; height:500px;">


# 🔎Log Analyticsデモにアクセス🛡️

以下のリンクをブラウザの別タブでアクセスしてください。

<!-- This link format lets us open in a seperate tab 😇 -->
<a href="https://aka.ms/lademo" target="_blank">https://aka.ms/lademo</a>

右上の青色バッテン ✖ を押してください。


<img src="images/KQL4.png" alt="LADemo" style="width:950px; height:500px;">


## ツールの案内と説明

使い方1️⃣：右上の機能

1. **New Diagram**: 新しい画面を作る操作。編集中のDiagramを保存しないで New Diagram押すと、途中までの図が削除される
    
1. **Clone Diagram**: 表情の図を新しいリンクで複製する
    
1. **Export**:　図を画像としてエクスポートする

1. **Settings**: プロフィールや図についてさまざまな設定。
    
1. **Save Changes**: 変更は自動保存じゃないため、閉じる前に押すこと
    
1. **プロフィール**: （任意）アカウントのログイン、プロフィール編集、パスワード変更
    

<img src="images/AZD2.png" alt="Azure Diagrams Tutorial" style="width:950px; height:500px;">


使い方2️⃣：左側の図パーツ

1. **Search**: よく利用されるサービスを検索して図に追加する。全てのリソースでもない
    
1. **Annotation**: 長文のテキストを書くためのラベル
    
1. **Label**:　短文のテキストを書くためのラベル

1. **Custom Resource**: 製品やプロセスのカスタムでできるタイル。アイコン、タイトル、サブタイトルが含まれる
    
1. **Section**: 複数のリソースをまとめて表情するためのボックス
    
1. **Shape**: 図形の作成

<img src="images/AZD3.png" alt="Azure Diagrams Tutorial" style="width:950px; height:500px;">

使い方3️⃣：カスタム リソース

1. **Custom Resource**: ドラッグアンドドロップで図に追加
    
1. **接続・データ フロー**: Custom Resourceの間に線を引くと、データの流れを表示する。リソースの種類によって、自動的線も変わる場合がある
    
1. **カスタマイズ**:　アイコンを押すと、Resource タイルの表示設定を調整

1. **アイコン**: Searchで表示されないアイコンがたくさんある。より細かいアーキテクチャ図を作るならオススメ


<img src="images/AZD4.png" alt="Azure Diagrams Tutorial" style="width:950px; height:500px;">

使い方4️⃣：カスタム シェイプ

1. **Shapes**: ドラッグアンドドロップで図に追加
    
1. **Shape**: 図形の形を設定する
    
1. **Background Color**:　透明度をマックスに上げると、枠だけの図形になる

1. **Border Color**: 図の枠の色の設定



<img src="images/AZD5.png" alt="Azure Diagrams Tutorial" style="width:950px; height:500px;">



### **任意**: アカウントの登録


今回の演習は、アカウントを登録せずに全てのタスクは完了可能です。
しかし、アカウントを持っている場合は以下のメリットあります：
- 作った Diagram を保存し、後で編集する
- Diagramを他のユーザーまたはコミュニティーに共有ができる
- 他のユーザーにプライベート（非公開）Diagram 共有とアクセス権限の設定（役割型）


<u><b>サインアップする方法</b></u>

1️⃣

右上の**Sign In**を押して、**Sign in or Create Accountを押します**

<img src="images/AZD8.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">

2️⃣

**Don't have an account? Sign up now**を押します

3️⃣

以下の画面に、メールアドレスを入力して、メールアドレス確認が終わってからパスワードと名前を設定します。

<img src="images/AZD8-5.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">



<pre><code class="language-kusto">
search "err"

search in (SecurityEvent,SecurityAlert,A*) "err"
</code></pre>



<link href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.23.0/themes/prism.min.css" rel="stylesheet" />
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.23.0/prism.min.js"></script>
<pre><code class="language-kusto">
search "err"

search in (SecurityEvent,SecurityAlert,A*) "err"
</code></pre>

<div class="code-container">
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
<pre><code class="kusto">
  search "err"

search in (SecurityEvent,SecurityAlert,A*) "err"
</code></pre>
</div>

# ✅Fabricのサンプル アーキテクチャ図を確認する✅


**1️⃣**

左下にある **Examples** を押します


<img src="images/AZD10.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">

**2️⃣**


Examplesのウィンドウが開かれます。ウィンドウの上をマウスで掴んで(1)、サイズを調整します。
Fabricのサンプル図 **Lakehouse Architecture on Fabric**を探して、クリックします。(2)


<img src="images/AZD11.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">

**3️⃣**

**Fabric Data Factory**と**Fabric Lakehouse**の間にある接続をマウスでかざして、統合の詳細が **Batch & Scheduled**となっている事を確認します。


<img src="images/AZD12.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">

**4️⃣**


コミュニティーが提供している例もあります。**Community Diagrams**を押し、ブラウザのページ上検索（Ctrl+F)に「Fabric」を入力して、好きなサンプルを選びます。


<img src="images/AZD13.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">




# 🏠Fabricのアーキテクチャ図を作成する🌊


## 演習

1. lab 01-04 で実施した内容を Azure Diatrams を使用して作図しましょう

1. （option）1. の図をクローンし、lab 05-07 の内容を反映してみましょう

1. lab 01-04 の作図をメダリオンアーキテクチャとして拡張しましょう

| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Row 1 Col 1 | Row 1 Col 2 | Row 1 Col 3 |
| Row 2 Col 1 | Row 2 Col 2 | Row 2 Col 3 |


### 回答例

1. [lab 01-04 の回答例へのリンク](./images/diagram-01-04.png)
   1. [Azure Diagrams](https://azurediagrams.com/D54ivtsh)
2. [lab 05-07 の回答例へのリンク](./images/diagram-05-07.png) 
   1. [Azure Diagrams](https://azurediagrams.com/e4F4s7l8)
3. [メダリオンアーキテクチャの回答例へのリンク](./images/diagram-medallion.png)
   1. [Azure Diagrams](https://azurediagrams.com/NhmRmML4)



# 📂図のエクスポートと共有🔗

<u><b>図の共有方法は２つあります</b></u>

方法1️⃣：画像として保存

PNGとSVGは使えます。右上の画像アイコンを押して、ファイルタイプを選択します。

SVGを選ぶと、ライブインタラクション（スクロール等）ができます

<img src="images/AZD20.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">

方法2️⃣：図へのアクセスを共有

３つの共有タイプがあります。
1. **Community**:図は検索可能で、誰でも閲覧でき、**Community Diagrams** に表示されます。
    
1. **Link**:図は検索から隠されていますが、ユニークなリンクを持っている人なら誰でもアクセスできます。

1. **Private**:図は共有した人だけがアクセスできます。

共有するために、Diagram を保存して、設定の歯車 ⚙ を押します。

設定のオプションから、Sharing 👥 を押します。

<img src="images/AZD21.png" alt="Azure Diagrams画面" style="width:950px; height:500px;">



## リソース

- [Microsoft Fabric でメダリオン Lakehouse アーキテクチャを実装](https://learn.microsoft.com/jp-ja/fabric/onelake/onelake-medallion-lakehouse-architecture)
- [Microsoft Fabric のグリーンフィールド レイクハウス](https://learn.microsoft.com/ja-jp/azure/architecture/example-scenario/data/greenfield-lakehouse-fabric)
- [Microsoft Fabric 開発ガイド](https://speakerdeck.com/ryomaru0825/microsoft-fabric-kai-fa-gaido?slide=31)
