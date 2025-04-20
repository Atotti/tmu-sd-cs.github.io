# 東京都立大学 情報科学科 ウェブサイト管理者向けREADME

このREADMEは東京都立大学情報科学科ウェブサイトの管理者向けのドキュメントです。サイトの構造、開発環境のセットアップ方法、コンテンツの追加・編集方法、多言語対応の管理方法、およびデプロイ手順について説明します。

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
├── ja/                   # 日本語コンテンツ
│   ├── about.md          # 情報科学科とは
│   ├── staff.md          # 教員紹介
│   ├── news/             # 日本語ニュース
│   │   ├── 2020-06-05-covid-info.md
│   │   └── ...
│   └── staff/            # 日本語教員詳細ページ
│       ├── aida.md       # 會田教授のページ
│       └── ...
├── en/                   # 英語コンテンツ
│   ├── about.md          # About
│   ├── staff.md          # Faculty
│   ├── news/             # 英語ニュース
│   │   ├── 2020-06-05-covid-info.md
│   │   └── ...
│   └── staff/            # 英語教員詳細ページ
│       ├── aida.md       # Professor Aida's page
│       └── ...
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

1. `_pages/`（日本語）または`en/`（英語）ディレクトリ内の対応するMarkdownファイルを開きます
2. フロントマター（YAMLヘッダー）と本文を編集します
3. 変更を保存し、ローカルサーバーで確認します

#### 新しいページの追加

1. `_pages/`（日本語）または`en/`（英語）ディレクトリに新しいMarkdownファイルを作成します
2. 以下のようなフロントマターを追加します：

   ```yaml
   # 日本語ページの場合
   ---
   layout: default
   title: "ページタイトル"
   copyright_year: 2025
   lang: "ja"
   ref: "unique-reference-id"  # 日英ページを関連付けるための一意のID
   ---

   # 英語ページの場合
   ---
   layout: default
   title: "Page Title"
   copyright_year: 2025
   lang: "en"
   ref: "unique-reference-id"  # 日英ページを関連付けるための一意のID
   permalink: /en/page-name.html  # 英語ページには必ずpermalinkを設定
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
   staff_image: "lastname_prof.webp"
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

2. **ディレクトリ構造**：
   - 日本語ページ：`_pages/`ディレクトリ（または直接ルートディレクトリ）
   - 英語ページ：`en/`ディレクトリ

3. **パーマリンク**：
   - 日本語ページ：デフォルトで`/:name.html`
   - 英語ページ：必ず`permalink: /en/:name.html`を設定

4. **言語切り替え**：ヘッダーの言語切り替えボタンは、同じ`ref`値を持つ異なる言語のページを検索し、リンクを生成します。

5. **翻訳データ**：共通の翻訳テキスト（ナビゲーションメニュー、フッターなど）は`_data/i18n/`ディレクトリ内のYAMLファイルで管理されています：
   - `_data/i18n/ja.yml`：日本語翻訳
   - `_data/i18n/en.yml`：英語翻訳

6. **新しい翻訳の追加**：新しい共通テキストを追加する場合は、両方の言語ファイルに同じキーで追加します。例えば：

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

7. **テンプレート内での使用**：翻訳テキストはテンプレート内で以下のように使用します：

   ```liquid
   {{ site.data.i18n[page.lang].new_section.title }}
   ```

### 言語切り替えロジック

言語切り替えボタンは、`_includes/header.html`で実装されています。このロジックは以下のように動作します：

1. 現在のページの`ref`属性を使用して、同じ`ref`を持つ異なる言語のページを検索します。
2. 対応するページが見つかった場合、そのページへのリンクを生成します。
3. 対応するページが見つからない場合、ページの`ref`属性を使用して適切なURLを構築します：
   - 英語ページから日本語ページへ：`/[ref].html`
   - 日本語ページから英語ページへ：`/en/[ref].html`

```liquid
{% if page.ref %}
  {% assign pages=site.pages | where:"ref", page.ref | where_exp:"p", "p.lang != page.lang" %}
  {% if pages.size > 0 %}
    {% for p in pages %}
      <a href="{{ p.url | relative_url }}"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
    {% endfor %}
  {% else %}
    {% if page.lang == 'en' %}
      {% if page.ref == 'index' %}
        <a href="{{ site.baseurl }}/index.html"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
      {% else %}
        <a href="{{ site.baseurl }}/{{ page.ref }}.html"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
      {% endif %}
    {% else %}
      {% if page.ref == 'index' %}
        <a href="{{ site.baseurl }}/en/index.html"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
      {% else %}
        <a href="{{ site.baseurl }}/en/{{ page.ref }}.html"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
      {% endif %}
    {% endif %}
  {% endif %}
{% else %}
  {% if page.lang == 'en' %}
    <a href="{{ site.baseurl }}/index.html"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
  {% else %}
    <a href="{{ site.baseurl }}/en/index.html"><img src="{{ site.baseurl }}/image/lang.webp" alt="JP/EN"></a>
  {% endif %}
{% endif %}
```

## CI/CD (継続的インテグレーション/継続的デリバリー)

このサイトはGitHub Actionsを使用した継続的インテグレーション/継続的デリバリー（CI/CD）パイプラインを実装しています。mainブランチへのプッシュまたはプルリクエストが作成されると、以下の自動チェックが実行されます：

1. **ビルド**: Jekyllを使用してサイトをビルドします。`--strict_front_matter`オプションを使用して、フロントマターの構文エラーを厳格にチェックします。

2. **HTML検証**:
   - **html-proofer**: リンク切れ、画像の存在確認、HTML構文などをチェックします。
   - **htmlhint**: HTML構文とベストプラクティスをチェックします。`.htmlhintrc`ファイルで定義されたルールに基づいて検証します。
     - 画像には`alt`属性が必要
     - 安全でない文字を含む属性をチェック
     - 画像には`src`属性が必要

3. **デプロイ**: 上記のすべてのチェックが成功し、変更がmainブランチにマージされると、サイトは自動的にGitHub Pagesにデプロイされます。

これらのチェックにより、サイトの品質と整合性が保たれ、問題のある変更がデプロイされることを防ぎます。

## デプロイ手順

このサイトはGitHub Pagesを使用してデプロイされています。
mainブランチにマージされた内容は上記のCI/CDパイプラインを通じて自動でデプロイされます。
