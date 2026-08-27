# SMV 2026 — Unconventional Image Sensors Meet Computer Vision

ACCV 2026 Workshop **W09**, in conjunction with **IWISS 2026**
14 December 2026 (full day) · Room 1007 · Grand Cube Osaka, Japan

Website source. Plain HTML + CSS, no build step, no dependencies.

```
index.html          # the whole site (single page with anchor navigation)
assets/style.css    # all styling
.nojekyll           # tells GitHub Pages to serve files as-is
```

---

## ローカルでの確認

`index.html` をブラウザで開くだけ。ビルドもサーバも不要。

## 公開先（リポジトリは2つ）

| リポジトリ | URL | 役割 | ローカルのフォルダ |
|---|---|---|---|
| `smv2026` | <https://sensorsmeetvision.github.io/smv2026/> | **2026年版の本体。永久に残すアーカイブ** | `website/` ← このフォルダ |
| `SensorsMeetVision.github.io` | <https://sensorsmeetvision.github.io/> | 最新開催回へ自動転送する入口 | `website-root/` |

```
  対外的に案内する URL
  https://sensorsmeetvision.github.io/
                │
                └─ 自動転送 ─→  https://sensorsmeetvision.github.io/smv2026/
                                 （このリポジトリ）
```

**案内・CFP・メールに載せるのはルート URL** の
`https://sensorsmeetvision.github.io/` の方。次回開催時は入口の転送先を
差し替えるだけで、`/smv2026/` は 2026 年版としてそのまま生き続けます。

先に **こちら（`smv2026`）を公開してから**、`website-root/` を公開してください
（転送先が存在しない状態を作らないため）。

## 公開手順（GitHub Pages）

1. <https://github.com/organizations/SensorsMeetVision/repositories/new> で
   リポジトリを作成
   - Repository name: `smv2026`
   - **Public**
   - **README / .gitignore / license は追加しない**（空のまま作る。
     追加すると初回 push が競合する）

2. ローカルから push

   ```bash
   cd "C:\Users\tsuyo\Documents\Claude\Projects\ACCV WS\website"
   git init
   git add .
   git commit -m "Initial site for SMV 2026 (ACCV 2026 Workshop W09)"
   git branch -M main
   git remote add origin https://github.com/SensorsMeetVision/smv2026.git
   git push -u origin main
   ```

3. リポジトリの **Settings → Pages** で
   Source = `Deploy from a branch`、Branch = `main` / `/ (root)` に設定

4. 1〜2 分で <https://sensorsmeetvision.github.io/smv2026/> が公開される

5. 続けて `website-root/` を公開する（手順は `../website-root/README.md`）

6. **ACCV 運営へ URL を連絡**し、公式 Workshops 一覧の W09 にリンクを張ってもらう。
   知らせるのは **ルート URL `https://sensorsmeetvision.github.io/`** の方。
   （現在 W09 だけリンクが未設定。宛先：`accv26-workshops@googlegroups.com` /
   `contact@accv2026.org`）

### 以降の更新

```bash
cd "C:\Users\tsuyo\Documents\Claude\Projects\ACCV WS\website"
git add .
git commit -m "Update speakers"
git push
```

push から反映まで 1〜2 分。反映されない時はブラウザのキャッシュを疑う
（`Ctrl` + `F5`）。

## 更新のしかた

| やりたいこと | 編集箇所 |
|---|---|
| 講演者を追加・変更 | `index.html` の `<article class="speaker">` ブロックをコピーして編集。`speaker__avatar` はイニシャル2文字 |
| 講演タイトル・アブストを追加 | 各 speaker ブロックの `speaker__topic` の下に `<p>` を追加 |
| 顔写真を入れる | `assets/img/` に画像を置き、`<div class="speaker__avatar">` を `<img class="speaker__avatar" src="assets/img/xxx.jpg" alt="">` に置換 |
| プログラム確定 | `#program` の `<table>` の行を編集。「Tentative program」の見出しと注記文も忘れず変更 |
| CFP の投稿方法を公開 | `#cfp` 内の `note--todo` ブロックを実際の投稿手順に差し替え（下記 TODO 参照） |
| 色を変える | `assets/style.css` 冒頭の `:root` 変数のみ |

---

## 公開前の TODO

- [ ] **ポスター投稿の受付方法を決定**し、`#cfp` の `note--todo` ブロックを差し替える
      （メール受付 / Google フォーム / CMT のいずれか）。オレンジ色の注記が出ている間は未完成の目印
- [ ] **IWISS 2026 併催のダブルネーミングについて ACCV Workshop Chairs へ一報**
      （`chair_query_IWISS_conjunction.md` が未送付。現在サイトはヒーロー・フッタで併催を前面に出している）
- [ ] **講演者リストの更新を Chairs へ一報**（Seung-Hwan Baek → Seung Ah Lee の差し替え、CV 側 1 名の追加）
- [ ] Min-Woong Seo 氏（Samsung / Pixel-parallel ADC）の回答 → センサ側の「To be announced」を確定 or 削除
- [ ] CV 側追加 1 名（分光・偏光）の招待 → CV 側の「To be announced」を確定 or 削除
- [ ] 講演者の顔写真・所属ページ URL を収集（10 月予定）
- [ ] `og:image` 用のバナー画像を作るか判断（SNS 告知時の見栄えに影響）

## 出典

サイト掲載内容の根拠は `../011_website_content_source.md` に集約。
提案書本文は `../application/main.tex`。
