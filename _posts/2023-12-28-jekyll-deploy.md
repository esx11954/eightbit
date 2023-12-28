---
layout: post
title:  "Jekyll Deploy"
date:   2023-12-19 11:01:11 +0900
categories: jekyll
---

## 事前準備
---

- githubアカウント
- 新規リモートリポジトリ
- git環境
- ruby環境

<br>

現状上記の環境がなければ以下から作成  
- [github](https://github.com/)  
- [git](https://gitforwindows.org/)  
- [ruby](https://rubyinstaller.org/downloads/)  

<br>

## 環境構築
---

任意のパスに作業用フォルダを作成し、該当パスでCLI (cmd or powershell) を起動  
以下のコマンドを実行  

```gem install jekyll bundler```  ...必要ライブラリインストール (**※初回のみ**)

```jekyll new --skip-bundle .```  ...Jekyllプロジェクト雛形作成

<br>

#### **Gemfile**
---

    gem "jekyll", "~> 4.3.2"  

上記を以下のように変更  

    gem "jekyll", "~> 3.9.3"  

<br>


    # gem "github-pages", group: :jekyll_plugins

上記を以下のように変更  

    gem 'github-pages', '~> 228', group: :jekyll_plugins

<br>    

ファイル最下部に以下を追記

    gem "webrick", "~> 1.8"

<br>

上記が完了したら以下コマンドを実行  

```bundle install```  ...Gemfileを参照して依存関係を解決  

<br>

#### **_config.yml**
---

以下抜粋部分を任意の値に変更  
**※[★context path]部分は作成したリモートリポジトリ名と一致させる**

```yml
title: [★サイトタイトル]
email: [★sample@sample.co.jp]
description: >- # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "/[★context path]/" # the subpath of your site, e.g. /blog
url: "https://[★githubアカウント名].github.io" # the base hostname & protocol for your site, e.g. http://example.com
# twitter_username: jekyllrb
github_username:  [★githubアカウント名]
```

<br>

#### **プロジェクトビルド**
---
Jekyllプロジェクトの動作をローカルで確認したい場合は以下のコマンドを実行する

```bundle exec jekyll build```  ... Jekyllプロジェクトのビルド

```bundle exec jekyll serve --trace```  ... ローカルで実行 (動作確認)

ローカル実行時は以下URLで確認可能　　

*http://127.0.0.1:4000/[baseUrl]*

<br>

<br>

#### **git**
---

ビルド後、*_site* というフォルダが生成されるので、  
CLIでそこに移動し、以下コマンドを実行  

    git init
    git add .
    git commit -m "Initial GitHub pages site with Jekyll"
    git branch -M main  
    git remote add origin [リモートリポジトリURL]
    git push -u origin main

<br>

#### **github (リモートリポジトリ設定)**
---

該当リポジトリの **Settings** > **Code and automation** > **Pages**を開く  
**Select branch** → **main**に設定  
**Select folder** → **root**に設定  
→ **Save**をクリック


<br>

設定後は以下のURLパターンで該当プロジェクトのサイトにアクセスできる  

```https://[githuアカウント名].github.io/[リポジトリ名]/```


<br>
<br>
<br>











