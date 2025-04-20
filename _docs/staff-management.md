# 教員プロフィール管理ガイド

このドキュメントでは、ウェブサイトの教員プロフィールセクションを管理する方法について説明します。

## 概要

教員プロフィールは、個別のマークダウンファイルとYAMLデータファイルを組み合わせて管理されています。教員の基本情報（名前、役職、専門分野など）はYAMLファイルに保存され、詳細な研究内容などはマークダウンファイルに記述されます。

## ディレクトリ構造

### データファイル
- `_data/staff/ja.yml` - 日本語の教員基本情報を格納するYAMLファイル
- `_data/staff/en.yml` - 英語の教員基本情報を格納するYAMLファイル

### プロフィールページ
- `ja/staff/` - 日本語の教員詳細ページを格納するディレクトリ
- `en/staff/` - 英語の教員詳細ページを格納するディレクトリ

## 新しい教員プロフィールの追加方法

### 1. データファイルへの追加

まず、教員の基本情報を言語ごとのYAMLファイルに追加します。

#### 日本語版 (`_data/staff/ja.yml`)

```yaml
- id: lastname
  name: 氏名
  title: 役職
  image: lastname_prof.jpg
  en_page: staff_lastname.html
  specialties:
    - 専門分野1
    - 専門分野2
  description: "簡単な説明文（省略可）"
  links:
    - title: "研究室website"
      url: "http://example.com"
```

#### 英語版 (`_data/staff/en.yml`)

```yaml
- id: lastname
  name: Name in English
  title: Position in English
  image: lastname_prof.jpg
  en_page: staff_lastname.html
  specialties:
    - Specialty 1 in English
    - Specialty 2 in English
  description: "Brief description in English (optional)"
  links:
    - title: "Laboratory Website"
      url: "http://example.com"
```

### 2. プロフィールページの作成

次に、教員の詳細ページを言語ごとに作成します。

#### 日本語版 (`ja/staff/lastname.md`)

```markdown
---
layout: staff_member
title: "氏名 研究室"
copyright_year: 2025
staff_id: lastname
staff_name: "氏名"
staff_title: "役職"
staff_image: "lastname_prof.webp"
lang: "ja"
ref: "staff-lastname"
specialties:
- "専門分野1"
- "専門分野2"
description: "研究室の説明文"
links:
- title: "研究室website"
  url: "http://example.com"
---
研究内容や業績などの詳細情報をここに記述します。
HTMLとMarkdownの書式を使用できます。

### 研究テーマ

- テーマ1の説明
- テーマ2の説明

### 主な業績

1. 業績1
2. 業績2
```

#### 英語版 (`en/staff/lastname.md`)

```markdown
---
layout: staff_member
title: "Name Laboratory"
copyright_year: 2025
staff_id: lastname
staff_name: "Name in English"
staff_title: "Position in English"
staff_image: "lastname_prof.webp"
lang: "en"
ref: "staff-lastname"
specialties:
- "Specialty 1 in English"
- "Specialty 2 in English"
description: "Laboratory description in English"
links:
- title: "Laboratory Website"
  url: "http://example.com"
---
Detailed information about research and achievements can be described here.
You can use Markdown formatting.

### Research Themes

- Description of theme 1
- Description of theme 2

### Major Achievements

1. Achievement 1
2. Achievement 2
```

### 3. 画像の追加

教員のプロフィール画像を `image/` ディレクトリに追加します。
ファイル名は `lastname_prof.jpg` のような形式にすることをお勧めします。

## 表示順序

教員プロフィールは `_data/staff/ja.yml` および `_data/staff/en.yml` ファイル内の順序で表示されます。表示順序を変更したい場合は、これらのファイル内でエントリの順序を変更してください。

## 既存の教員プロフィールの編集

### データの編集

既存の教員情報を編集するには、`_data/staff/ja.yml` または `_data/staff/en.yml` ファイル内の該当するエントリを変更します。

### プロフィールページの編集

詳細ページを編集するには、`ja/staff/` または `en/staff/` ディレクトリ内の該当するマークダウンファイルを開いて内容を変更します。

## 教員プロフィールの削除

教員プロフィールを削除するには、以下の手順を実行します：

1. `_data/staff/ja.yml` および `_data/staff/en.yml` ファイルから該当するエントリを削除します。
2. `ja/staff/` ディレクトリから該当するマークダウンファイルを削除します。
3. `en/staff/` ディレクトリから該当するマークダウンファイルを削除します。
4. 必要に応じて、`image/` ディレクトリから該当する画像ファイルを削除します。

## 多言語対応のヒント

- `ref` 属性は日本語版と英語版のページを関連付けるために使用されます。同じ教員の日本語ページと英語ページには同じ `ref` 値を設定してください。
