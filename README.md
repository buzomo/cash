# 財布の現金

シンプルな現金管理ウェブアプリケーションです。収入と支出を簡単に記録し、残高や使用状況を視覚的に確認できます。

## 特徴

- 収入と支出の簡単な記録
- 日付、金額、名目ごとの取引記録
- 残高のリアルタイム表示
- 日次、週次、月次の支出概要
- 週ごとの支出グラフ表示
- 取引の検索機能
- GitHub連携によるデータのバックアップと同期

## セットアップ手順

### 1. データ保存用のリポジトリを準備する

1. GitHubで新しいリポジトリを作成します（例：`your-username/cash-data`）
2. リポジトリに初期の空のJSONファイルを作成します:
   - ファイル名: `transactions.json`
   - 内容: `[]`

### 2. GitHub個人アクセストークンの取得

1. GitHubにログインし、「Settings」→「Developer settings」→「Personal access tokens」→「Tokens (classic)」に移動
2. 「Generate new token」をクリックし、適切な権限（少なくとも`repo`スコープ）を付与
3. 生成されたトークンをコピーして安全な場所に保管

### 3. アプリケーションの設定

1. このリポジトリをクローンまたはダウンロード
2. `index.html`ファイルを編集し、以下の部分を変更:

```javascript
// 以下の行を見つけて、あなたのリポジトリ情報に変更
fetch('https://raw.githubusercontent.com/buzomo/cash-data/refs/heads/main/transactions.json')
// ↓ 以下のように変更
fetch('https://raw.githubusercontent.com/your-username/cash-data/refs/heads/main/transactions.json')

// 同様に、以下の行も変更
'https://api.github.com/repos/buzomo/cash-data/contents/transactions.json'
// ↓ 以下のように変更
'https://api.github.com/repos/your-username/cash-data/contents/transactions.json'
```

### 4. GitHubトークンの設定

アプリケーションを使用する前に、ブラウザのコンソールで以下のコマンドを実行してGitHubトークンを設定:

```javascript
localStorage.setItem('gh_token', 'あなたのGitHubトークン');
```

## 使用方法

1. アプリケーションをWebサーバーでホスティングするか、ローカルで`index.html`ファイルを開きます
2. 「+」ボタンをクリックして、新しい取引を追加
3. 日付、金額、説明を入力し、取引タイプ（収入/支出）を選択
4. 追加された取引はリアルタイムでGitHubリポジトリに保存されます
5. 過去の取引を編集するには、取引リストの項目をクリック

## 注意事項

- このアプリはブラウザのローカルストレージに保存されたGitHubトークンを使用します
- セキュリティのため、公共のコンピュータでの使用は避けてください
- トークンは定期的に更新することをお勧めします

## カスタマイズ

スタイルやレイアウトをカスタマイズするには、`<style>`セクションを編集してください。

## 貢献

問題の報告や機能リクエストは、Issueを通じてお願いします。
