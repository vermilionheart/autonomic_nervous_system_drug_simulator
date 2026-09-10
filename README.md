# 自律神経系薬物シミュレーター

ブラウザで動作する教育用シミュレーターです。自律神経系作用薬の投与に対する平均血圧(MAP)、心拍数(HR)、呼吸数(RR)の時間変化を可視化します。

## 同梱内容
- `index.html` : シミュレーター本体（GitHub Pages の公開入口）
- `.nojekyll` : GitHub Pages で `_` 始まりの資産が除外されるのを防止
- `.github/workflows/static.yml` : GitHub Actions で Pages 配備する場合の設定
- `verification_render.pdf` : PDF出力の確認用レンダリング（存在する場合）

## 主な修正反映
- 初期値の統一: SBP 120 / DBP 80 / HR 70 / RR 16
- 状態表示の修正: 正常 / 薬物作用中 / 回復中
- アトロピン + アセチルコリン時の節N成分調整
- PDF出力時のグラフ見切れ修正
- 投与リストの作用中/終了判定の整合化

## GitHub Pages 公開手順（標準）
> 画面に **`Upgrade or make this repository public to enable Pages`** と出る場合、原因は **このリポジトリが private のまま** で、現在のプランでは Pages を有効化できないことです。先に **public に変更** するか、**Upgrade** が必要です。
>
> GitHub UI: **Settings → General → Danger Zone → Change repository visibility → Make public**

1. GitHub で空のリポジトリ `autonomic_nervous_system_drug_simulator` を作成する
2. 必要なら先にそのリポジトリを **public** に変更する
3. この ZIP を展開する
4. 展開したフォルダで以下を実行する

```bash
git remote set-url origin https://github.com/vermilionheart/autonomic_nervous_system_drug_simulator.git
git push -u origin main
```

5. GitHub の **Settings → Pages** を開く
6. **Build and deployment** の **Source** で **Deploy from a branch** を選ぶ
7. **Branch** を **main**、フォルダを **/(root)** にして **Save**
8. 数十秒〜数分待つ
9. 公開URL: `https://vermilionheart.github.io/autonomic_nervous_system_drug_simulator/`

## GitHub Pages 公開手順（Actions を使う場合）
このリポジトリには `.github/workflows/static.yml` を同梱しています。

1. 先にリポジトリを **public** にする（または **Upgrade** する）
2. `main` に push する
3. GitHub の **Settings → Pages** を開く
4. **Build and deployment** の **Source** で **GitHub Actions** を選ぶ
5. Actions 実行完了後、同じURLで公開される

公開URL:
- `https://vermilionheart.github.io/autonomic_nervous_system_drug_simulator/`

## GitHub Pages 互換性メモ
- エントリーファイルは **リポジトリ直下の `index.html`** です
- `<base>` タグは使っていません
- 絶対パス (`/assets/...`) は使っていません
- CDN 依存の `src` / `href` も使っていません
- そのまま `https://user.github.io/repo/` 配下で配信できます

## ローカル動作
1. `index.html` をブラウザで開く
2. 薬物を選択してシミュレーションを実行
3. Excel / PDF / PNG を必要に応じて出力
