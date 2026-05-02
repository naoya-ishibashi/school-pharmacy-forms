# まがた保育園 学校環境衛生検査 入力フォーム

iPhone から直接アクセスして使う、検査票テンプレ駆動の入力フォーム（12検査ぶん統合）。

## デプロイ済み URL（このリポジトリの GitHub Pages）

`https://naoyaishibashi.github.io/<REPO>/`  ← 公開後にここに記入

## 使い方

1. 上の URL を iPhone Safari で開く
2. 共有ボタン → **「ホーム画面に追加」** でアプリ風に常駐
3. ホーム画面のアイコンをタップ → 検査を選んで入力 → 「📥 エクセル出力」
4. ダウンロードした xlsx は共有シートから Google Drive 等に保存

## 含まれているもの

- `index.html` — 検査入力フォーム本体（12検査統合・887KB）
- `.nojekyll` — GitHub Pages の Jekyll 処理を抑止する空ファイル

## 含まれている検査

ダニ・空気(CO₂)・ホルムアルデヒド・気流粉じん・照度・NO₂CO・黒板・飲料水・プール水・環境・給食室・医薬品保管管理 の **12種**（騒音・理科室薬品は保育園対象外で除外）。

## デプロイ手順（はじめて）

### 1. GitHub にリポジトリを作成
- github.com にログイン → 右上 + → **New repository**
- リポジトリ名：例 `school-pharmacy-forms`
- **Public**（GitHub Pages の無料利用は public 必須／private は GitHub Pro 以上）
- 「Add a README」はチェックしない（このREADMEを使うため）
- **Create repository**

### 2. このフォルダのファイルをアップロード
- 作成したリポジトリのトップ画面で「**uploading an existing file**」リンクをクリック
- Mac から `gh_pages/` フォルダ内の **すべてのファイル**（index.html, .nojekyll, README.md）をドラッグ＆ドロップ
- 一番下の **Commit changes** を押す

### 3. GitHub Pages を有効化
- リポジトリの **Settings** タブ → 左メニューの **Pages**
- Source：**Deploy from a branch**
- Branch：**main / (root)** を選択 → **Save**
- 1〜2分待つと、上に `Your site is live at https://<username>.github.io/<repo>/` と表示される

### 4. iPhone で開く
- 上記URLを iPhone Safari に入力
- 共有 → 「**ホーム画面に追加**」
- 名前を「検査入力」などに編集して **追加**
- ホーム画面の青いアイコンをタップで起動

## 更新時の手順

`_definitions.py` などを編集して `python3 generate_forms.py` を再実行 →
新しい `学校薬剤師_検査入力_統合版.html` を `gh_pages/index.html` にリネームコピー →
GitHub web 画面で `index.html` を編集 → アップロードで上書き → 自動的に Pages も更新される。

## プライバシーに関する注意

このリポジトリを **Public** にする場合：
- 園名（まがた保育園）と薬剤師名がフォーム上にデフォルト値として埋め込まれている
- 入力された個人データはローカル localStorage のみ保持され、Pages 側のサーバには送信されない（クライアントのみで動作）
- 第三者がURLにアクセスすれば**フォームのテンプレ自体は閲覧できる**ので、もし懸念があれば
  - `index.html` 中の `default: "まがた保育園"` を `""` にして再生成
  - または GitHub Pro で private + Pages にする
