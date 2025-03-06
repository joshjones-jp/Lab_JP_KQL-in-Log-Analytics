# ✅演習：クエリ作成チャレンジ回答例✅


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
SecurityEvent
| where EventID == 4625
| project TimeGenerated, Account, TargetAccount
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
| summarize count() by Source
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
SecurityEvent
| where TimeGenerated > ago(7d)
| where format_datetime(TimeGenerated, "HH:mm:ss") between (time(08:00:00) and time(18:00:00))
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
| where EventID == 4625
| summarize FailedAttempts = count() by bin(TimeGenerated, 1h), Account
| where FailedAttempts > 5
| project TimeGenerated, Account, FailedAttempts
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
| where LogonType == 3
| summarize NetworkLogons = count() by IPAddress
| join kind=inner (SecurityEvent | where EventID == 4625 | summarize FailedLogons = count() by IPAddress) on IPAddress
| where NetworkLogons > 10
| project TimeGenerated, IPAddress, NetworkLogons, FailedLogons
</code></pre>
</div>
