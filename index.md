---
marp: true
theme: academic
footer: @2022 [Katsuyuki-Karasawa](https://github.com/Katsuyuki-Karasawa)
paginate: true
style:
    
---
<!-- _class: lead -->

# 学内チャットツール
## NT25-A 6班

1. K021C1258/阿部 拓海  
2. K021C1260/唐澤 克幸  
3. K021C1252/松本 智紀  
4. K021C1259/大槻 諒
5. K021C1248/加藤 好太  
6. K021C1286/小出 佑希  

![bg contain opacity:20%](https://github.com/marp-team/marp/raw/main/marp.png)

---

<!-- _header: 先行開発 -->

<div style="text-align:center;"> 
    <a href="https://github.com/vector-im/element-web">
        <img src="https://github-link-card.s3.ap-northeast-1.amazonaws.com/vector-im/element-web.png" width="460px">
    </a>
    <a href="https://github.com/mattermost/mattermost-server">
        <img src="https://github-link-card.s3.ap-northeast-1.amazonaws.com/mattermost/mattermost-server.png" width="460px">
    </a>
    <a href="https://github.com/traPtitech/traQ">
        <img src="https://github-link-card.s3.ap-northeast-1.amazonaws.com/traPtitech/traQ.png" width="460px">
    </a>
    <a href="https://github.com/zulip/zulip">
        <img src="https://github-link-card.s3.ap-northeast-1.amazonaws.com/zulip/zulip.png" width="460px">
    </a>
    <a href="https://github.com/RocketChat/Rocket.Chat">
        <img src="https://github-link-card.s3.ap-northeast-1.amazonaws.com/RocketChat/Rocket.Chat.png" width="460px">
    </a>
    <a href="https://github.com/fosscord/fosscord">
        <img src="https://github-link-card.s3.ap-northeast-1.amazonaws.com/fosscord/fosscord.png" width="460px">
    </a>
</div> 

---


<!-- header: Why -->

# なぜ作ろうとしたか

1. 学内のチャットツール(教師用/生徒用)がバラバラすぎる
2. 既存のシステムだと外部に依存しすぎている
3. Chatworkが改悪
4. 学内で保守できるような環境がある(AWS)
5. プライベート端末に学内のツールをインストールすることに疑問:thinking:
6. ファイル周りの管理
7. 料金体系などの問題

---

# 学内のチャットツールがバラバラ
* 管理がしづらい
* 教員ごとにツールが違うせいで連絡が取りづらい
* classroomでしか反応してくれない教員がいるため非常に連絡がしづらい

---

# 既存システムでは外部依存が激しい
* なぜかGoogle Workspaceが活用できていない
* もし、外部のツールの場合なにか問題が発生した際のバックアップがない
* 追跡や情報収集を嫌う人は一定数いるという部分の解消(degoogle)

---

# Chatworkが改悪
## (そもそも商用利用で無償利用はどうなのか)
* オンプレミス or クラウドで自分での保守
(インシデントが発生しない可能性がないわけではない)
* 一定期間経過するとログが残らなくなる(40日)
* 広告やメールへの通知、そもそもの機能面の問題
---

# 学内で保守できる環境がある
* ゆくゆくはtraSのような同好会の環境を作成することを可能
* AWSが比較的自由に使える環境がある

---

# プライベート端末へ学内ツールのインストール
* プライベートを干渉されたくない
* 教員によっていれるソフトウェアがバラバラのため複数必要
* UIや操作性の一貫性が取れない
---

# ファイル周りの管理
* GDriveをベースにしているが、ChatworkやSlackなどで扱いが違う
* ブラウザ内でプレビュー対応など

---

# 料金体系
* 無料で使おうとする教員がほとんどのため、ツールが分散しすぎている
* 海外のツールが多いため、日本円での内課金にはそれなりの追加コストがある
* 誰が負担するのかという問題点がある
　
---
<!-- header: What -->
# これはなに
1. チャンネルの管理
2. 拡張性(API周りやカスタムテーマを扱えるようにする)
3. 軽量・シンプルかつ誰でも扱えるようなUIとサーバー(React.JS Socket.IO)
4. Google OAuth
6. AWS EC2を採用

**かつOSSなチャットツール**

---

# チャンネルの管理
* チャンネルの追加
* チャンネルの削除
* チャンネルの権限設定
etc...

各種ツールにも実装されてる機能を実装する

---

# 拡張性
* 軽量な動作を目指してTailwindを採用
* Socket.IOでリアルタイム双方向通信が可能
* Node.jsによる実装のため拡張性が高い
* OSSのため実装されている機能の透明性が高い

---

# Google OAuth
* Passportを使用した実装
* Google Workspaceアカウントの活用
* 実装が複雑ではない

---

# AWS EC2を採用
* デプロイ専用
* オンプレミスでの保守は人件費が大きい
* EC2以外にも採用しやすい

