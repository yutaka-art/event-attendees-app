# Event Attendees App

イベント参加者を管理するためのWebアプリケーションです。

## 概要

このアプリケーションは、イベントの参加者登録、管理、出席確認などを効率的に行うためのASP.NET Core Razor Pagesベースのシステムです。

## 主な機能

- 参加者登録
- 参加者一覧表示
- 出席状況管理
- イベント情報管理
- 参加者検索・フィルタリング

## 技術スタック

- **フロントエンド**: ASP.NET Core Razor Pages, Bootstrap
- **バックエンド**: ASP.NET Core 8.0
- **データベース**: SQL Server (Entity Framework Core 8.0.10)
- **認証**: Azure Key Vault (本番環境)
- **コンテナ**: Docker (Linux)

## セットアップ

### 前提条件

- .NET 8.0 SDK
- SQL Server (LocalDB または SQL Server Express)
- Visual Studio 2022 または Visual Studio Code
- Docker Desktop (コンテナ実行時)

### インストール手順

1. リポジトリをクローン
   ```bash
   git clone https://gitlab.com/union.dml-group/event-attendees-app.git
   cd event-attendees-app/src/EventAttendeesApp
   ```

2. 依存関係を復元
   ```bash
   dotnet restore
   ```

3. データベース接続文字列を設定
   ```bash
   # appsettings.json または User Secrets で設定
   dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=(localdb)\\mssqllocaldb;Database=EventAttendeesDB;Trusted_Connection=true;MultipleActiveResultSets=true"
   ```

4. データベースマイグレーション実行
   ```bash
   dotnet ef database update
   ```

5. アプリケーションを起動
   ```bash
   dotnet run
   ```

## 使用方法

1. ブラウザで `https://localhost:5001` または `http://localhost:5000` にアクセス
2. ホームページから各機能にアクセス
3. イベント参加者一覧は `/EventAttendees` で確認可能

## 開発

### 開発環境での起動

```bash
dotnet watch run
```

### テスト実行

```bash
dotnet test
```

### ビルド

```bash
dotnet build
```

### Dockerでの実行

```bash
docker build -t event-attendees-app .
docker run -p 8080:8080 event-attendees-app
```

## ディレクトリ構成

```
event-attendees-app/
├── src/
│   └── EventAttendeesApp/
│       ├── Pages/              # Razor Pages
│       │   ├── EventAttendees/ # 参加者管理ページ
│       │   └── Shared/         # 共有レイアウト
│       ├── Models/             # データモデル
│       ├── Data/               # Entity Framework コンテキスト
│       ├── wwwroot/            # 静的ファイル
│       └── appsettings.json    # 設定ファイル
└── docs/                       # ドキュメント
```

## データベースモデル

### EventAttendee エンティティ
- EventName: イベント名
- AttendeeName: 参加者名
- Email: メールアドレス
- RegistrationDate: 登録日

## デプロイメント

### Azure App Service
1. Azure CLI でログイン
2. リソースグループとApp Serviceを作成
3. デプロイ実行

### Docker コンテナ
```bash
docker build -t event-attendees-app .
docker push [your-registry]/event-attendees-app
```

## 環境変数

- `ConnectionStrings:DefaultConnection`: データベース接続文字列
- Azure Key Vault設定 (本番環境)

## 貢献

プルリクエストやイシューの報告を歓迎します。

1. フォークする
2. フィーチャーブランチを作成 (`git checkout -b feature/AmazingFeature`)
3. 変更をコミット (`git commit -m 'Add some AmazingFeature'`)
4. ブランチにプッシュ (`git push origin feature/AmazingFeature`)
5. プルリクエストを作成

## ライセンス

このプロジェクトは MIT ライセンスの下で公開されています。

## 連絡先

質問や問題がある場合は、GitLabのイシューを作成してください。

## 開発者向け情報

- Entity Framework Core を使用したデータアクセス
- Azure Key Vault による設定管理
- Bootstrap を使用したレスポンシブデザイン
- Docker対応でクロスプラットフォーム実行可能
