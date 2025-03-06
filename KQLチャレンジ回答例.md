# 🧩演習：クエリ作成チャレンジ🧩


以下のクエリは、チャレンジの回答案です。
KQLはクエリ言語として柔軟ですので、以下は唯一の正解という意味ではない。


## **1️⃣**


<div class="code-container">
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
<pre><code class="kusto">
// SecurityEvent テーブルでのログイン失敗を見つける
SecurityEvent
| where _______________ == "Account logon failure"
| project TimeGenerated, Account, _______________
</code></pre>
</div>


## **2️⃣**


<div class="code-container">
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
<pre><code class="kusto">
// SecurityEvent テーブルでのソース別のイベント数をカウントする
SecurityEvent
| summarize _______________ by _______________
</code></pre>
</div>


## **3️⃣**


<div class="code-container">
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
<pre><code class="kusto">
// SecurityEvent テーブルで過去1週間以内の特定の時間範囲で発生したイベントをフィルタリングする
SecurityEvent
| where TimeGenerated > ago(7d)
| where _______________ between (time(08:00:00) and time(18:00:00))
</code></pre>
</div>


## **4️⃣**


<div class="code-container">
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
<pre><code class="kusto">
// SecurityEvent テーブルで特定のユーザーが短期間に複数回の失敗したログイン試行を行った場合の不正アクセス試行を特定する
SecurityEvent
| where EventID == _______________
| summarize _______________ by bin(TimeGenerated, 1h), _______________
| where _______________ > 5
| project _______________, _______________, _______________
</code></pre>
</div>


## **5️⃣**


<div class="code-container">
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
<pre><code class="kusto">
// SecurityEvent テーブルで異常なネットワークアクティビティを検出し、特定のIPアドレスからの異常なイベントを見つける
SecurityEvent
| where _______________ == 3
| summarize _______________ by _______________
| join kind=inner (SecurityEvent | where _______________ | summarize count() by IPAddress) on _______________
| where _______________ > 10
| project _______________, _______________, _______________
</code></pre>
</div>
