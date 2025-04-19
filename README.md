# 東京都立大学 情報科学科 ウェブサイト管理者向けREADME

このREADMEは東京都立大学情報科学科ウェブサイトの管理者向けのドキュメントです。サイトの構造、開発環境のセットアップ方法、コンテンツの追加・編集方法、多言語対応の管理方法、およびデプロイ手順について説明します。

## 目次

- [東京都立大学 情報科学科 ウェブサイト管理者向けREADME](#東京都立大学-情報科学科-ウェブサイト管理者向けreadme)
  - [目次](#目次)
  - [サイト概要](#サイト概要)
  - [サイト構造](#サイト構造)
  - [開発環境のセットアップ](#開発環境のセットアップ)
    - [必要条件](#必要条件)
    - [インストール手順](#インストール手順)
  - [コンテンツ管理](#コンテンツ管理)
    - [ページの追加・編集](#ページの追加編集)
      - [既存ページの編集](#既存ページの編集)
      - [新しいページの追加](#新しいページの追加)
    - [News \& Topicsの管理](#news--topicsの管理)
      - [ニュースアイテムの追加](#ニュースアイテムの追加)
      - [ニュースアイテムの編集・削除](#ニュースアイテムの編集削除)
    - [教員プロフィールの追加・編集](#教員プロフィールの追加編集)
      - [既存の教員プロフィールの編集](#既存の教員プロフィールの編集)
      - [新しい教員プロフィールの追加](#新しい教員プロフィールの追加)
    - [多言語コンテンツの管理](#多言語コンテンツの管理)
  - [デプロイ手順](#デプロイ手順)

## サイト概要

このウェブサイトは[Jekyll](https://jekyllrb.com/)を使用して構築されています。Jekyllは静的サイトジェネレーターであり、Markdownファイルからウェブサイトを生成します。このサイトは日本語と英語の両方のコンテンツを提供しており、多言語対応（i18n）が実装されています。

## サイト構造

サイトは以下のディレクトリ構造で構成されています：

```
/
├── _config.yml           # Jekyllの設定ファイル
├── Gemfile               # Rubyの依存関係
├── index.md              # トップページ（日本語）
├── _data/                # サイトデータ
│   ├── staff/            # 教員情報
│   │   ├── ja.yml        # 日本語版教員情報
│   │   └── en.yml        # 英語版教員情報
│   └── i18n/             # 多言語翻訳データ
│       ├── ja.yml        # 日本語翻訳
│       └── en.yml        # 英語翻訳
├── _docs/                # ドキュメント
│   ├── news-management.md       # News & Topics管理ガイド（日本語）
│   └── news-management-en.md    # News & Topics管理ガイド（英語）
├── _includes/            # 再利用可能なコンポーネント
│   ├── header.html       # ヘッダー
│   ├── footer.html       # フッター
│   ├── navigation.html   # ナビゲーション
│   └── ...
├── _layouts/             # レイアウトテンプレート
│   ├── default.html      # デフォルトレイアウト
│   └── staff_member.html # 教員ページレイアウト
├── _news/                # 日本語ニュースアイテム
│   ├── 2025-04-20-new-sample.md # サンプルニュース
│   └── ...
├── _en_news/             # 英語ニュースアイテム
│   ├── 2025-04-20-new-sample.md # サンプルニュース（英語）
│   └── ...
├── _pages/               # 日本語ページ
│   ├── about.md          # 情報科学科とは
│   ├── staff.md          # 教員紹介
│   └── ...
├── _en_pages/            # 英語ページ
│   ├── about.md          # About
│   ├── staff.md          # Faculty
│   └── ...
├── _staff/               # 日本語教員ページ
│   ├── ono.md            # 小野教授のページ
│   └── ...
├── _en_staff/            # 英語教員ページ
│   ├── ono.md            # Professor Ono's page
│   └── ...
├── assets/               # アセット（CSS、JS、画像など）
│   └── css/
├── _sass/                # Sassスタイルシート
└── image/                # 画像ファイル
```

## 開発環境のセットアップ

### 必要条件

- Ruby 2.5.0以上
- RubyGems

### インストール手順

1. Rubyをインストールします（まだインストールされていない場合）
   ```bash
   # macOSの場合（Homebrewを使用）
   brew install ruby

   # Ubuntuの場合
   sudo apt-get install ruby-full build-essential
   ```

2. Bundlerをインストールします
   ```bash
   gem install bundler
   ```

3. プロジェクトディレクトリに移動し、依存関係をインストールします
   ```bash
   cd /path/to/tmu-sd-cs.github.io
   bundle install
   ```

4. ローカルサーバーを起動します
   ```bash
   bundle exec jekyll serve
   ```

5. ブラウザで `http://localhost:4000` にアクセスして、サイトを確認します

## コンテンツ管理

### ページの追加・編集

#### 既存ページの編集

1. `_pages/`（日本語）または`_en_pages/`（英語）ディレクトリ内の対応するMarkdownファイルを開きます
2. フロントマター（YAMLヘッダー）と本文を編集します
3. 変更を保存し、ローカルサーバーで確認します

#### 新しいページの追加

1. `_pages/`（日本語）または`_en_pages/`（英語）ディレクトリに新しいMarkdownファイルを作成します
2. 以下のようなフロントマターを追加します：

   ```yaml
   ---
   layout: default
   title: "ページタイトル"
   copyright_year: 2025
   lang: "ja"  # または "en"（英語の場合）
   ref: "unique-reference-id"  # 日英ページを関連付けるための一意のID
   ---
   ```

3. ページコンテンツを追加します
4. 変更を保存し、ローカルサーバーで確認します

### News & Topicsの管理

News & Topicsセクションは、個別のマークダウンファイルとして管理されています。これにより、各ニュースアイテムを簡単に追加、編集、削除することができます。

詳細なガイドは以下のドキュメントを参照してください：
- 日本語: [News & Topics 管理ガイド](_docs/news-management.md)
- 英語: [News & Topics Management Guide](_docs/news-management-en.md)

#### ニュースアイテムの追加

1. `_news/`（日本語）または`_en_news/`（英語）ディレクトリに新しいMarkdownファイルを作成します
   - ファイル名は `YYYY-MM-DD-title-slug.md` の形式にします
   - 例: `2025-04-20-open-campus.md`

2. 以下のようなフロントマターを追加します：

   ```yaml
   ---
   title: "ニュースのタイトル"
   date: YYYY-MM-DD
   ---
   ```

3. ニュースの内容を本文に追加します
4. 重要なニュースの場合は、日本語版と英語版の両方を作成します

#### ニュースアイテムの編集・削除

- **編集**: 該当するマークダウンファイルを開いて内容を変更します
- **削除**: 該当するマークダウンファイルを削除します

### 教員プロフィールの追加・編集

#### 既存の教員プロフィールの編集

1. `_staff/`（日本語）または`_en_staff/`（英語）ディレクトリ内の対応するMarkdownファイルを開きます
2. フロントマターと本文を編集します
3. 変更を保存し、ローカルサーバーで確認します

#### 新しい教員プロフィールの追加

1. `_staff/`（日本語）ディレクトリに新しいMarkdownファイルを作成します（例：`lastname.md`）
2. 以下のようなフロントマターを追加します：

   ```yaml
   ---
   layout: staff_member
   title: "氏名 研究室"
   copyright_year: 2025
   staff_id: lastname
   staff_name: "氏名"
   staff_title: "役職"
   staff_image: "lastname_prof.jpg"
   lang: "ja"
   ref: "staff-lastname"  # 日英ページを関連付けるための一意のID
   specialties:
   - "専門分野1"
   - "専門分野2"
   description: "研究室の説明文"
   links:
   - title: "研究室website"
     url: "http://example.com"
   ---
   ```

3. 研究内容などの本文を追加します
4. 同様に、`_en_staff/`ディレクトリに英語版のファイルを作成します
5. 教員情報を言語ごとのファイルに追加します：

   ```yaml
   # _data/staff/ja.yml に日本語情報を追加
   - id: lastname
     name: 氏名
     title: 役職
     image: lastname_prof.jpg
     en_page: staff_lastname.html
     specialties:
       - 専門分野1
       - 専門分野2
     description: ""
     links: []

   # _data/staff/en.yml に英語情報を追加
   - id: lastname
     name: Name in English
     title: Position in English
     image: lastname_prof.jpg
     en_page: staff_lastname.html
     specialties:
       - Specialty 1 in English
       - Specialty 2 in English
     description: ""
     links: []
   ```

6. 変更を保存し、ローカルサーバーで確認します

### 多言語コンテンツの管理

このサイトは日本語と英語の両方のコンテンツを提供しています。多言語コンテンツは以下のように管理されています：

1. **ページの関連付け**：日本語と英語のページは`ref`属性で関連付けられています。同じ`ref`値を持つページは同じコンテンツの異なる言語バージョンとして扱われます。

2. **翻訳データ**：共通の翻訳テキスト（ナビゲーションメニュー、フッターなど）は`_data/i18n/`ディレクトリ内のYAMLファイルで管理されています：
   - `_data/i18n/ja.yml`：日本語翻訳
   - `_data/i18n/en.yml`：英語翻訳

3. **新しい翻訳の追加**：新しい共通テキストを追加する場合は、両方の言語ファイルに同じキーで追加します。例えば：

   ```yaml
   # _data/i18n/ja.yml
   new_section:
     title: "新しいセクション"
     description: "説明文"
   ```

   ```yaml
   # _data/i18n/en.yml
   new_section:
     title: "New Section"
     description: "Description"
   ```

4. **テンプレート内での使用**：翻訳テキストはテンプレート内で以下のように使用します：

   ```liquid
   {{ site.data.i18n[page.lang].new_section.title }}
   ```

## デプロイ手順

このサイトはGitHub Pagesを使用してデプロイされています。
mainブランチにマージされた内容は自動でデプロイされます。

