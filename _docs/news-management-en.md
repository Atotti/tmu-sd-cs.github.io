# News & Topics Management Guide

This document explains how to manage the News & Topics section of the website.

## Overview

News & Topics are managed as individual markdown files. This makes it easy to add, edit, and delete news items.

## Directory Structure

- `_news/` - Directory for Japanese news items
- `_en_news/` - Directory for English news items

## How to Add a New News Item

### 1. File Name Format

Create files with the following format:

```
YYYY-MM-DD-title-slug.md
```

Examples:
- `2025-04-20-new-system-announcement.md`
- `2025-05-01-open-campus-info.md`

### 2. File Content

Create each news file with the following format:

```markdown
---
title: "News Title"
date: YYYY-MM-DD
---
Write the news content here. HTML tags can be used.
```

Example:

```markdown
---
title: "Open Campus Announcement"
date: 2025-05-01
---
We will hold an Open Campus at Hino Campus on Sunday, June 15, 2025.
For details, please see <a href="https://example.com">here</a>.
```

### 3. Create Both Japanese and English Versions

For important news, please create both Japanese and English versions:

- Japanese version: `_news/YYYY-MM-DD-title-slug.md`
- English version: `_en_news/YYYY-MM-DD-title-slug.md`

Use the same file name but adapt the content for each language.

## Display Order

News items are displayed in order of newest date first. They are sorted by the value of the `date` field.

## Editing Existing News Items

To edit an existing news item, open the corresponding markdown file and modify the content.

## Deleting News Items

To delete a news item, delete the corresponding markdown file.
