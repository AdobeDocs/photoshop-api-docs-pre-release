<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [プライベートベータ版](#%E3%83%97%E3%83%A9%E3%82%A4%E3%83%99%E3%83%BC%E3%83%88%E3%83%99%E3%83%BC%E3%82%BF%E7%89%88)
- [Photoshop API へようこそ！](#photoshop-api-%E3%81%B8%E3%82%88%E3%81%86%E3%81%93%E3%81%9D)
- [準備と導入](#%E6%BA%96%E5%82%99%E3%81%A8%E5%B0%8E%E5%85%A5)
  - [認証](#%E8%AA%8D%E8%A8%BC)
    - [概要](#%E6%A6%82%E8%A6%81)
    - [ワークフローとユースケース](#%E3%83%AF%E3%83%BC%E3%82%AF%E3%83%95%E3%83%AD%E3%83%BC%E3%81%A8%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9)
    - [個人ユーザー](#%E5%80%8B%E4%BA%BA%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC)
      - [OAuth 2.0 および IMS の追加情報](#oauth-20-%E3%81%8A%E3%82%88%E3%81%B3-ims-%E3%81%AE%E8%BF%BD%E5%8A%A0%E6%83%85%E5%A0%B1)
    - [サービストークンでのワークフロー（Adobe ETLAユーザー）](#%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%83%88%E3%83%BC%E3%82%AF%E3%83%B3%E3%81%A7%E3%81%AE%E3%83%AF%E3%83%BC%E3%82%AF%E3%83%95%E3%83%AD%E3%83%BCadobe-etla%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC)
      - [サービストークンとJWTの追加情報](#%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%83%88%E3%83%BC%E3%82%AF%E3%83%B3%E3%81%A8jwt%E3%81%AE%E8%BF%BD%E5%8A%A0%E6%83%85%E5%A0%B1)
  - [API キー](#api-%E3%82%AD%E3%83%BC)
  - [リトライ](#%E3%83%AA%E3%83%88%E3%83%A9%E3%82%A4)
  - [利用量の制限](#%E5%88%A9%E7%94%A8%E9%87%8F%E3%81%AE%E5%88%B6%E9%99%90)
- [Photoshop](#photoshop)
  - [一般的な利用手順](#%E4%B8%80%E8%88%AC%E7%9A%84%E3%81%AA%E5%88%A9%E7%94%A8%E6%89%8B%E9%A0%86)
    - [入力および出力ファイルの保存](#%E5%85%A5%E5%8A%9B%E3%81%8A%E3%82%88%E3%81%B3%E5%87%BA%E5%8A%9B%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E4%BF%9D%E5%AD%98)
    - [ドキュメントの更新の追跡](#%E3%83%89%E3%82%AD%E3%83%A5%E3%83%A1%E3%83%B3%E3%83%88%E3%81%AE%E6%9B%B4%E6%96%B0%E3%81%AE%E8%BF%BD%E8%B7%A1)
  - [サポートされている機能](#%E3%82%B5%E3%83%9D%E3%83%BC%E3%83%88%E3%81%95%E3%82%8C%E3%81%A6%E3%81%84%E3%82%8B%E6%A9%9F%E8%83%BD)
    - [レイヤーの編集](#%E3%83%AC%E3%82%A4%E3%83%A4%E3%83%BC%E3%81%AE%E7%B7%A8%E9%9B%86)
    - [アートボード](#%E3%82%A2%E3%83%BC%E3%83%88%E3%83%9C%E3%83%BC%E3%83%89)
    - [ドキュメントの編集](#%E3%83%89%E3%82%AD%E3%83%A5%E3%83%A1%E3%83%B3%E3%83%88%E3%81%AE%E7%B7%A8%E9%9B%86)
    - [レンダリング/変換](#%E3%83%AC%E3%83%B3%E3%83%80%E3%83%AA%E3%83%B3%E3%82%B0%E5%A4%89%E6%8F%9B)
    - [テキストレイヤー](#%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E3%83%AC%E3%82%A4%E3%83%A4%E3%83%BC)
      - [フォント](#%E3%83%95%E3%82%A9%E3%83%B3%E3%83%88)
    - [スマートオブジェクト](#%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88)
    - [Photoshopバージョンとの互換性](#photoshop%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3%E3%81%A8%E3%81%AE%E4%BA%92%E6%8F%9B%E6%80%A7)
  - [API の使用方法](#api-%E3%81%AE%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)
    - [例1： /documentManifest（PSD の構造の取得）](#%E4%BE%8B1-documentmanifestpsd-%E3%81%AE%E6%A7%8B%E9%80%A0%E3%81%AE%E5%8F%96%E5%BE%97)
      - [ステップ1：PSD の JSON 形式を取得するジョブを開始する](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%971psd-%E3%81%AE-json-%E5%BD%A2%E5%BC%8F%E3%82%92%E5%8F%96%E5%BE%97%E3%81%99%E3%82%8B%E3%82%B8%E3%83%A7%E3%83%96%E3%82%92%E9%96%8B%E5%A7%8B%E3%81%99%E3%82%8B)
      - [ステップ2：ステータスと結果をポーリングする](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%972%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9%E3%81%A8%E7%B5%90%E6%9E%9C%E3%82%92%E3%83%9D%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E3%81%99%E3%82%8B)
      - [ステップ3：返された形式](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%973%E8%BF%94%E3%81%95%E3%82%8C%E3%81%9F%E5%BD%A2%E5%BC%8F)
    - [例2： /documentOperations（PSD の編集とレンダリングをする）](#%E4%BE%8B2-documentoperationspsd-%E3%81%AE%E7%B7%A8%E9%9B%86%E3%81%A8%E3%83%AC%E3%83%B3%E3%83%80%E3%83%AA%E3%83%B3%E3%82%B0%E3%82%92%E3%81%99%E3%82%8B)
      - [オブジェクトの追加、編集、削除](#%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E8%BF%BD%E5%8A%A0%E7%B7%A8%E9%9B%86%E5%89%8A%E9%99%A4)
      - [ステップ1：かんたんな編集（テキストレイヤーに対して）](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%971%E3%81%8B%E3%82%93%E3%81%9F%E3%82%93%E3%81%AA%E7%B7%A8%E9%9B%86%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E3%83%AC%E3%82%A4%E3%83%A4%E3%83%BC%E3%81%AB%E5%AF%BE%E3%81%97%E3%81%A6)
      - [ステップ2：ステータスと結果をポーリングする](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%972%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9%E3%81%A8%E7%B5%90%E6%9E%9C%E3%82%92%E3%83%9D%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E3%81%99%E3%82%8B-1)
      - [ステップ3：新しい調整レイヤーを追加する](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%973%E6%96%B0%E3%81%97%E3%81%84%E8%AA%BF%E6%95%B4%E3%83%AC%E3%82%A4%E3%83%A4%E3%83%BC%E3%82%92%E8%BF%BD%E5%8A%A0%E3%81%99%E3%82%8B)
      - [ステップ4：ピクセルレイヤーの画像を編集する](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%974%E3%83%94%E3%82%AF%E3%82%BB%E3%83%AB%E3%83%AC%E3%82%A4%E3%83%A4%E3%83%BC%E3%81%AE%E7%94%BB%E5%83%8F%E3%82%92%E7%B7%A8%E9%9B%86%E3%81%99%E3%82%8B)
      - [ステップ5：新しい画像を作成する](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%975%E6%96%B0%E3%81%97%E3%81%84%E7%94%BB%E5%83%8F%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B)
      - [手順6：スマートオブジェクトレイヤーの画像を置き換える](#%E6%89%8B%E9%A0%866%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%83%AC%E3%82%A4%E3%83%A4%E3%83%BC%E3%81%AE%E7%94%BB%E5%83%8F%E3%82%92%E7%BD%AE%E3%81%8D%E6%8F%9B%E3%81%88%E3%82%8B)
    - [例3： /renditionCreate（新しい画像の生成）](#%E4%BE%8B3-renditioncreate%E6%96%B0%E3%81%97%E3%81%84%E7%94%BB%E5%83%8F%E3%81%AE%E7%94%9F%E6%88%90)
        - [ステップ1：ファイルがひとつのとき](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%971%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%8C%E3%81%B2%E3%81%A8%E3%81%A4%E3%81%AE%E3%81%A8%E3%81%8D)
      - [ステップ2：ステータスと結果をポーリングする](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%972%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9%E3%81%A8%E7%B5%90%E6%9E%9C%E3%82%92%E3%83%9D%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E3%81%99%E3%82%8B-2)
      - [ステップ3：フォルダごとのとき（複数のファイル）](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%973%E3%83%95%E3%82%A9%E3%83%AB%E3%83%80%E3%81%94%E3%81%A8%E3%81%AE%E3%81%A8%E3%81%8D%E8%A4%87%E6%95%B0%E3%81%AE%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB)
    - [例4： /smartObject （スマートオブジェクトの置き換え）](#%E4%BE%8B4-smartobject-%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E7%BD%AE%E3%81%8D%E6%8F%9B%E3%81%88)
        - [ステップ1：スマートオブジェクトの置き換え](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%971%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E7%BD%AE%E3%81%8D%E6%8F%9B%E3%81%88)
        - [ステップ2：スマートオブジェクトを作成する](#%E3%82%B9%E3%83%86%E3%83%83%E3%83%972%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B)
  - [サンプルコード](#%E3%82%B5%E3%83%B3%E3%83%97%E3%83%AB%E3%82%B3%E3%83%BC%E3%83%89)
  - [現在の制限](#%E7%8F%BE%E5%9C%A8%E3%81%AE%E5%88%B6%E9%99%90)
- [Image Cutout（画像の切り抜き）](#image-cutout%E7%94%BB%E5%83%8F%E3%81%AE%E5%88%87%E3%82%8A%E6%8A%9C%E3%81%8D)
  - [バージョン2](#%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B32)
    - [一般的な利用手順](#%E4%B8%80%E8%88%AC%E7%9A%84%E3%81%AA%E5%88%A9%E7%94%A8%E6%89%8B%E9%A0%86-1)
    - [APIの使用方法](#api%E3%81%AE%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)
      - [例1：画像の切り抜きを作成する](#%E4%BE%8B1%E7%94%BB%E5%83%8F%E3%81%AE%E5%88%87%E3%82%8A%E6%8A%9C%E3%81%8D%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B)
      - [例2：画像マスクを作成するジョブを開始する](#%E4%BE%8B2%E7%94%BB%E5%83%8F%E3%83%9E%E3%82%B9%E3%82%AF%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B%E3%82%B8%E3%83%A7%E3%83%96%E3%82%92%E9%96%8B%E5%A7%8B%E3%81%99%E3%82%8B)
  - [バージョン1 （非推奨）](#%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B31-%E9%9D%9E%E6%8E%A8%E5%A5%A8)
    - [一般的な利用手順](#%E4%B8%80%E8%88%AC%E7%9A%84%E3%81%AA%E5%88%A9%E7%94%A8%E6%89%8B%E9%A0%86-2)
    - [API の使用方法](#api-%E3%81%AE%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95-1)
- [Lightroom API](#lightroom-api)
  - [一般的な利用手順](#%E4%B8%80%E8%88%AC%E7%9A%84%E3%81%AA%E5%88%A9%E7%94%A8%E6%89%8B%E9%A0%86-3)
  - [APIの使用方法](#api%E3%81%AE%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95-1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


[README(English)](https://github.com/AdobeDocs/photoshop-api-docs-pre-release)

[README(Japanese)](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/README.ja.md)


<!--
# Private Beta

The Photoshop APIs are made available through an invitation only Private Beta. In order to be considered for the Private Beta please apply here https://photoshop.adobelanding.com/api-signup/

Make sure to take a look at the Pre-release agreement before applying and ensure you understand the aspects of the program.
-->

# プライベートベータ版

Photoshop API は、プライベートベータ版に招待された人のみ利用できます。プライベートベータ版の対象となるには、こちら https://photoshop.adobelanding.com/api-signup/ からお申し込みください。

申請する前にプレリリース規約に同意し、プログラムの状態をしっかりと確実に理解してください。

<!--
# Welcome to Photoshop APIs!

The Adobe Photoshop API gives you access to a subset of Photoshop, Lightroom, and Sensei  services. The API will allow you to make both layer and document level edits to Photoshop PSD files as well as perform a number of image edits and improvements.

The Photoshop API is designed with REST like principles and uses standard HTTP response codes, verbs and authentication and returns JSON-encoded responses.

The links below provide more detailed information about the API services including code samples and reference guides.  Once you are done setting up your Authentication you can dive into these links.

The API documentation is published at

[Photoshop API Reference](https://adobedocs.github.io/photoshop-api-docs-pre-release/)

[Lightroom Getting Started](https://github.com/AdobeDocs/lightroom-api-docs)

[Lightroom API Reference](https://adobedocs.github.io/lightroom-api-docs/)

[Image Cutout Getting Started](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout)

[Image Cutout API Reference](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei-ImageCutout)
-->

# Photoshop API へようこそ！

Adobe Photoshop API を使用すると、Photoshop、Lightroom、および Sensei にアクセスできます。API を使用すると、Photoshop PSD ファイルのレイヤーとドキュメント自体の両方の編集ができるだけでなく、大量の画像の編集や合成をすることができます。

Photoshop API は一般的な REST になっており、標準の HTTP レスポンスコード、メソッド、認証を使います。JSON 形式の応答を返します。

以下のリンクは、コードサンプルやリファレンスガイドなど、API サービスについての詳しい情報です。認証の設定ができたら、これらのリンクをたどってみてください。

APIのドキュメントは以下で公開しています:

[Photoshop API リファレンス](https://adobedocs.github.io/photoshop-api-docs-pre-release/)

[Lightroom をはじめよう](https://github.com/AdobeDocs/lightroom-api-docs)

[Lightroom API リファレンス](https://adobedocs.github.io/lightroom-api-docs/)

[Image Cutout をはじめよう](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout)

[Image Cutout API リファレンス](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei-ImageCutout)

<!--
# General Setup and Onboarding

## Authentication
### Overview

The Photoshop API uses client id’s (also know as api keys) and authentication tokens to authenticate requests. There are two different kinds of authorization tokens available: 

1. Individual user access (OAuth 2.0 access token)
2. Adobe Enterprise ETLA (Service token using JSON Web Token/JWT)

If this is your first time using Adobe API’s we suggest trying out the OAuth workflow.

In order to use the Photoshop API's you’ll need to get a Client ID (also known as an API key) and a Client Secret. Once you have those you can use them to programmatically get an access token to authenticate your requests.  We’ll walk you through the steps below.
-->

# 準備と導入

## 認証

### 概要

Photoshop API は、クライアントID（APIキー）と認証トークンを用いてリクエストを認証します。認証トークンには、次の2種類があります。

1. 個人ユーザーアクセス（OAuth 2.0 アクセストークン）
2. Adobe Enterprise ETLA（エンタープライズタームライセンス契約）（JSON Web Token（JWT）を用いたサービストークン）

Adobe API を初めて使用する場合は、OAuth を使う方法から試すことをお勧めします。

Photoshop API を使用するには、クライアントID（APIキー）とクライアントシークレットを入手しておく必要があります。
それらを入手したら、それらを使用してプログラムでアクセストークンを取得し、リクエストを認証できます。以下に手順を示します。

<!--
### Workflow and Use Cases

Here are the workflows we currently support.  You are…

- An individual user logged in who has an Adobe Creative Cloud Account
- An organization with an Adobe ETLA (an enterprise account)
- Running a job on a server
- Running in a browser

If your workflow falls outside of these please contact us at psdservices@adobe.com so we can help meet your needs.
-->

### ワークフローとユースケース

現在サポートしているワークフローは次のとおりです。あなたは、以下の条件に当てはまっている必要があります。

- Adobe Creative Cloud アカウントでログインしている個人ユーザー
- Adobe ETLA（エンタープライズアカウント）を契約している組織
- サーバーでジョブを実行する
- ブラウザでジョブを実行する

あなたのワークフローが、これらの条件に当てはまらない場合は、 psdservices@adobe.com （英語）までご連絡ください。あなたのニーズにお応えします。

<!--
### Individual users
1. Get your client id and client secret.
After you've been accepted to the PreRelease program you will be emailed your credentials (your client ID and client Secret) required for API authentication.
-->

### 個人ユーザー

1. クライアントIDとクライアントシークレットを入手する。
プレリリースプログラムに承認されると、API 認証に必要な資格情報（クライアント ID とクライアントシークレット）がメールで送信されてきます。

<!--
2. Test out your credentials.
This will allow you to verify that your credentials work and show you want an OAuth token looks like for when you eventually do this programmatically.
  - Browse to https://ps-prerelease-us-east-1.cloud.adobe.io
  - Enter the client id and secret
  - Follow through the login process
  - If your credentials work you should see an authorization token appear on your screen
This is the OAuth token that’s required to make calls to the Photoshop API’s and if you’d like you can jump ahead and immediately try them out now.  Eventually you will make this process programmatic (instructions below) but in the meantime the token expires in 24 hours and you can use this workflow during development for as long as you’d like.
-->

2.　資格情報をテストする。
資格情報が正しいことを確認し、プログラムから OAuth トークンがどのように見えるかを、確認しておくことができます。
   - https://ps-prerelease-us-east-1.cloud.adobe.io にアクセスします。
   - クライアント ID とクライアントシークレットを入力します。
   - ログインする
   - 認証情報が正しければ、画面に認証トークンが表示されます。
これは、Photoshop API を呼び出すために必要な OAuth トークンです。必要に応じて、今すぐアクセスして、すぐに試すことができます。最終的には、このプロセスをプログラムにします（以下の手順を参照）が、それまでのあいだ、トークンは 24時間で期限が切れます。開発中は、このワークフローを好きなときに使用できます。

<!--
3. Make an authenticated call to ensure you can round trip successfully with the API’s
```shell
curl --request GET \
  --url https://image.adobe.io/pie/psdService/hello  \
  --header 'Authorization: Bearer <YOUR_OAUTH_TOKEN>' \
  --header 'x-api-key: <YOUR_CLIENT_ID>' \
```
  Congrats! You just made your first request to the Photoshop API.
-->

3. 認証された呼び出しをして、API を用いて正常に通信のやりとりができることを確認する。
```shell
curl --request GET \
  --url https://image.adobe.io/pie/psdService/hello  \
  --header 'Authorization: Bearer <YOUR_OAUTH_TOKEN>' \
  --header 'x-api-key: <YOUR_CLIENT_ID>' \
```
おめでとうございます！ Photoshop API に最初のリクエストを送信できました。

<!--
4.  Make a Photoshop API call with real assets

  Now that you can successfully authenticate and talk to the API’s it’s time to make “real” calls…

  ```shell
  curl -X POST \
    https://image.adobe.io/pie/psdService/documentManifest \
    -H 'Authorization: Bearer <auth_token>' \
    -H 'Content-Type: application/json' \
    -H 'x-api-key: <YOUR_API_KEY>' \
    -d '{
    "inputs": [
      {
        "href":"files/Example.psd",
        "storage":"adobe"
      }
    ]
  }'
  ```
-->

4. 実際のアセットで Photoshop API を呼び出す。

   APIを正しく認証して通信できるようになったので、次は「本当の」呼び出しをします。

  ```shell
  curl -X POST \
    https://image.adobe.io/pie/psdService/documentManifest \
    -H 'Authorization: Bearer <auth_token>' \
    -H 'Content-Type: application/json' \
    -H 'x-api-key: <YOUR_API_KEY>' \
    -d '{
    "inputs": [
      {
        "href":"files/Example.psd",
        "storage":"adobe"
      }
    ]
  }'
  ```

<!--
5. Notes on token retrieval

  The access token must never be transmitted as a URI parameter. Doing so would expose it to being captured in-the-clear by intermediaries such as proxy server logs. The API does not allow you to send an access token anywhere except the Authorization header field.

  Your access token will expire typically in 24 hours.  You will receive a ‘refresh_token’ when you initially obtain the access token that you can use to get a new access token.  Be aware that refreshing your token might require a new login event.  Please reference the [OAuth documentation](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/OAuth/OAuth.md) for additional instructions.
-->

5. トークンの取得における注意

   アクセストークンは、URIパラメーターとして送信しないでください。これをすると、プロキシサーバーのログなどの仲介者により、暗号化されていないテキストとしてキャプチャされる可能性があります。API では、Authorization ヘッダーフィールド以外の場所にアクセストークンを送信することはできません。

   アクセストークンは通常24時間で期限切れになります。新しいアクセストークンを得るためのアクセストークンを最初に取得したとき、「refresh_token」を受け取るはずです。トークンを更新すると、もう一度ログインが必要になる場合があることに注意してください。詳しくは、 [OAuthのドキュメント](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/OAuth/OAuth.md) を参照してください。

<!--
6. Automate token retrieval

  Please contact psdservices@adobe.com for more information on how you can automate token generation for your workflow.
-->

6. トークンの取得を自動化する

   あなたのワークフローにおけるトークン生成を自動化する方法の詳細は、 psdservices@adobe.com （英語）にお問い合わせください。

<!--
#### Additional OAuth 2.0 and IMS Information

You can find details on interacting with Adobe IMS API’s and authentication in general
1. [General Authentication Information](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)
2. [OAuth Authentication](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/OAuth/OAuth.md)
3. [IMS API’s](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/Resources/IMS.md)
4. [OAuth Sample Code](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/tree/sudipta/archydoc/sample_code/oauth-sample-app)
-->

#### OAuth 2.0 および IMS の追加情報

Adobe IMS API との相互関係および認証全般についての詳細は以下にあります。

1. [一般的な認証情報](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)
2. [OAuth 認証](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/OAuth/OAuth.md)
3. [IMS API について](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/Resources/IMS.md)
4. [OAuth サンプルコード](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/tree/sudipta/archydoc/sample_code/oauth-sample-app)


<!--
### Service Token Workflow (Adobe ETLA users)
In order to be an enterprise user you must already have an ETLA.  To find out if you have an ETLA reach out to your system administrator or your Adobe Account Executive. 

Enterprise users will not have access to assets stored in the Creative Cloud so you must use an external storage source when making calls to the API.
-->

### サービストークンでのワークフロー（Adobe ETLAユーザー）
エンタープライズユーザーになるには、ETLAをすでに契約している必要があります。ETLA があるかどうかを確認するには、貴社のシステム管理者またはアドビアカウントエグゼクティブに連絡してください。

エンタープライズユーザーは Creative Cloud に保存されているアセットにアクセスできないため、API を呼び出すときに外部ストレージ元を使用する必要があります。

<!--
1. Get a developer role in the Adobe Admin Console
You system admin will need to give you developer access in the [Adobe Admin Console](https://adminconsole.adobe.com/overview)
-->

1. Adobe Admin Console で開発者権限を取得する。
貴社のシステム管理者が、 [Adobe Admin Console](https://adminconsole.adobe.com/overview)で、あなたに開発者のアクセス権限を付与する必要があります。

<!--
2. Go to https://console.adobe.io and create a service integration and follow the instructions at [Service Token Instructions](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md)

  On Step 1 of the Service Integration docs, ‘Subscribe to an Adobe Service’ you will select the following
    1. Photoshop
    2. Lightroom / Camera Raw API
    3. Image Cutout
-->

2. https://console.adobe.io にアクセスしてサービスインテグレーションを作成し、 [サービストークンの手順](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) の指示に従います。

   サービスインテグレーションのドキュメントのステップ1にある「アドビのサービスに登録」では、以下を選択します。
     1. Photoshop
     2. Lightroom / Camera Raw API
     3. Image Cutout

<!--
3. Create a JSON Web Token (JWT) and exchange it for an access token
Take the information from your integration, plus your private key that you created when you created your integration and follow the instructions at [JWT Instructions:](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md)

  You can refer to [JWT sample code](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/tree/sudipta/archydoc/sample_code/jwt-sample-app) for additional help
-->

3. JSON Web Token（JWT）を作成し、アクセストークンと交換する。
インテグレーションから情報と、インテグレーションを作成したとき生成した秘密鍵を取得して、 [JWTの手順](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md) の指示に従います。

   追加のヘルプは、 [JWT サンプルコード](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/tree/sudipta/archydoc/sample_code/jwt-sample-app) を参照してください。

<!--
4. Make your first Photoshop API call
Make an authenticated call to ensure you can round trip successfully with the API’s

``` shell

curl --request GET \
  --url https://image.adobe.io/pie/psdService/hello \
  --header 'Authorization: Bearer <YOUR_SERVICE_TOKEN>' \
  --header 'x-api-key: <YOUR_CLIENT_ID>'
  ```
  Congrats! You just made your first request to the Photoshop API.
-->

4. 初めての Photoshop API の呼び出しをする。
認証された呼び出しをして、API を用いて正常に通信のやりとりができることを確認します。

``` shell

curl --request GET \
  --url https://image.adobe.io/pie/psdService/hello \
  --header 'Authorization: Bearer <YOUR_SERVICE_TOKEN>' \
  --header 'x-api-key: <YOUR_CLIENT_ID>'
  ```
  おめでとうございます！ Photoshop API に最初のリクエストを送信できました。

<!--
5. Automate your access token retrieval
Go back to step 3 to obtain a fresh service token
-->

5. トークンの取得を自動化する
ステップ3に戻り、新しいサービストークンを取得します。

<!--
#### Additional Service Token and JWT Information

You can find details on interacting with Adobe IMS API’s and authentication in general
  1. [General Authentication Information](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)
  2. [JWT/Service Token Authentication](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md)
  3. [IMS API’s](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/Resources/IMS.md)
  4. [JWT Sample Code](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/tree/sudipta/archydoc/sample_code/jwt-sample-app) 
-->

#### サービストークンとJWTの追加情報

Adobe IMS API との相互関係および認証全般についての詳細は以下にあります。
  1. [一般的な認証情報](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)
  2. [JWT/サービストークン認証](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md)
  3. [IMS APIについて](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/Resources/IMS.md)
  4. [JWT サンプルコード](https://github.com/AdobeDocs/photoshop-api-docs-pre-release/tree/sudipta/archydoc/sample_code/jwt-sample-app) 

<!--
## API Keys

Also known as the `client_id`. You must additionally pass in your Adobe API key in the `x-api-key` header field. You’ll automatically get a developer API key when you create your Adobe I/O Console Integration.  After you've created your integration you can find your API key in the `Overview` tab of your Integration
-->

## API キー

これは `client_id` とも呼ばれます。`x-api-key` ヘッダーフィールドで Adobe API キーを渡す必要があります。Adobe I/O コンソールインテグレーションを作成すると、開発者 API キーが自動的に取得されます。インテグレーションを作成したら、インテグレーションの `Overview` タブで API キーを確認できます。

<!--
## Retries

- The service will retry status codes of 429, 502, 503, 504 three times.
- You should only retry requests that have a 5xx response code. A 5xx error response indicates there was a problem processing the request on the server.
- You should implement an exponential back-off retry strategy with 3 retry attempts.
- You should not retry requests for any other response code.
-->

## リトライ

- サービスは 429、502、503、504 のステータスコードを3回リトライします。
- 5xx のレスポンスコードを持つリクエストのみ、リトライする必要があります。 5xx のエラーレスポンスは、サーバーにおけるリクエストの処理に問題があったことを示します。
- 3回のリトライをするエクスポネンシャルバックオフの仕組みを実装する必要があります。
- 他のレスポンスコードの要求をリトライしないでください。

<!--
## Rate Limiting

We have not put a throttle limit on requests to the API at this time.
-->

## 利用量の制限

現時点では、API へのリクエストに上限は設けていません。


<!--
# Photoshop
-->

# Photoshop

<!--
## General Workflow

The typical workflow involves retrieving a PSD document manifest file via `/documentManifest` (a JSON representation of the documents layer tree), followed by one or more calls to `/documentOperations` to optionally edit the PSD and/or create new image renditions. Both endpoints are asynchronous so the response will contain the `/status` endpoint to poll for job status and results
-->

## 一般的な利用手順

典型的な利用手順は、 `/documentManifest` （ドキュメントのレイヤーツリーを JSON に表したもの）を呼び出して PSD ドキュメントの構造ファイルを取得し、続けて `/documentOperations` に1回か複数回かの呼び出しをして、PSD を編集したり、新しい画像を作成したりします。両方のエンドポイントは非同期であるため、レスポンスは、ジョブのステータスと結果をポーリングするための `/status` エンドポイントを含んでいます。

<!--
### Input and Output file storage

Clients can use assets stored on one of the following storage types:
1. Adobe: by referencing the path to the files on Creative Cloud
2. External: (like AWS S3) by using a presigned GET/PUT URL
3. Azure: By generating a SAS (Shared Access Signature) for upload/download
4. Dropbox: Generate temporary upload/download links using https://dropbox.github.io/dropbox-api-v2-explorer/
-->

### 入力および出力ファイルの保存

クライアントは、次のストレージタイプのいずれかに保存されているアセットを使うことができます。

1. Adobe： Creative Cloud 上のファイルへのパスを参照する。
2. 外部：（AWS S3のような）署名済みの GET/PUT URL を使う。
3. Azure： アップロード/ダウンロード用の SAS（Shared Access Signature）を生成する。
4. Dropbox： https://dropbox.github.io/dropbox-api-v2-explorer/ を用いて一時的なアップロード/ダウンロードリンクを生成する。

<!--
### Tracking document changes

If you are making multiple edits to a PSD during the course of a user session it is your decision on how you want to track and store changes from one version of a PSD to another. Some clients will choose to refresh the document's JSON manifest by calling `/documentManifest` again after each call to `/documentOperations`. Other clients may choose to cache the changes locally and then make one final call to `/documentOperations` with the original PSD and the accumulated changes requested by the user.
-->

### ドキュメントの更新の追跡

ユーザーセッション中に、PSD に複数の編集をするときは、PSDの元バージョンから別のバージョンへの更新を追跡および保存する方法を決めます。クライアントによっては、 `/documentOperations` を呼び出すたびに `/documentManifest` を再度呼び出して、ドキュメントの JSON 形式を更新するようにします。他のクライアントでは、更新をローカルにキャッシュしてから、元の PSD とユーザーがした更新の累積をもとにして `/documentOperations` を最後に1回呼び出します。

<!--
## Supported Features

This is a partial list of currently supported features.  Please also see the [Release Notes](https://forums.adobeprerelease.com/photoshopapiservice/categories/releasenotes) for a list of added features
-->

## サポートされている機能

これは現在、対応している機能のリストです。新たに追加された機能のリストについては、 [リリースノート](https://forums.adobeprerelease.com/photoshopapiservice/categories/releasenotes) もご覧ください。

<!--
### Layer level edits

- General layer edits
  - Edit the layer name
  - Toggle the layer locked state
  - Toggle layer visibility
  - Move or resize the layer via it's bounds
  - Delete layers
- Adjustment layers
  - Add or edit an adjustment layer. The following types of adjustment layers are currently supported:
  - Brightness and Contrast
  - Exposure
  - Hue and Saturation
  - Color Balance
- Image/Pixel layers
  - Add a new pixel layer, with optional image
  - Swap the image in an existing pixel layer
- Shape layers
  - Resize a shape layer via it's bounds
- Text layers
  - Edit the text
  - Change the font (See the `Fonts` section for more info)
  - Edit the font size
  - Edit the text decoration (bold, italic, etc)
  - Edit the text orientation (horizontal/vertical)
  - Edit the paragraph alignment (centered, justified, etc)
  - Edit the font weight
-->

### レイヤーの編集

- レイヤーの一般的な編集
   - レイヤー名の編集
   - レイヤーのロックの切り替え
   - レイヤーの表示／非表示の切り替え
   - 座標によるレイヤーの移動とサイズ変更
   - レイヤーの削除
- 調整レイヤー
   - 調整レイヤーの追加または編集。現在、次の種類の調整レイヤーがサポートされています：
   - 明るさ・コントラスト
   - 露光量
   - 色相・彩度
   - カラーバランス
- 画像/ピクセルレイヤー
   - 選択した画像で新しいピクセルレイヤーを追加
   - 既存のピクセルレイヤーの画像の入れ替え
- シェイプレイヤー
   - 座標によるシェイプレイヤーのサイズ変更
- テキストレイヤー
   - テキストの編集
   - フォントの変更（詳細は「フォント」の項を参照してください）
   - フォントサイズの編集
   - テキストの装飾の編集（太字、斜体など）
   - テキストの向きの編集（横書き/縦書き）
   - 段落の配置の編集（中央揃え、両端揃えなど）
   - フォントの太さの編集

<!--
### Artboards

- Show artboard information in the JSON Manifest
- Create a new artboard from multiple input psd's
-->

### アートボード

- アートボードの情報をJSON形式で出力する
- 複数の PSD から新しいアートボードを作成する

<!--
### Document level edits

- Crop a PSD
- Resize a PSD
-->

### ドキュメントの編集

- PSD のトリミング
- PSD のサイズ変更

<!--
### Rendering / Conversions

- Create a new PSD document
- Create a JPEG, TIFF or PNG rendition of various sizes
- Request thumbnail previews of all renderable layers
- Convert between any of the supported filetypes (PSD, JPEG, TIFF, PNG)
-->

### レンダリング/変換

- 新しい PSD ドキュメントを作成する
- さまざまなサイズの JPEG、TIFF、または PNG 画像を出力する
- レンダリングできるすべてのレイヤーのサムネイルプレビューを出力する
- サポートされているファイル形式（PSD、JPEG、TIFF、PNG）の間で変換する

<!--
### Text layers

The Photoshop APIs currently support creating and editing of Text Layer with different fonts, character styles and paragraph styles.

The API's are documented [here](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-document_operations)

We also have an example of making a simple text layer edit.

[Text layer Example Code](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#example-1-making-a-simple-edit-to-a-text-layer)
-->

### テキストレイヤー

Photoshop API は現在、さまざまなフォント、文字のスタイル、段落のスタイルの、テキストレイヤーの作成と編集ができます。

API のドキュメントは [こちら](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-document_operations)

シンプルなテキストレイヤーの編集のサンプルもあります。

[テキストレイヤーのサンプルコード](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#example-1-making-a-simple-edit-to-a-text-layer)

<!--
#### Fonts

The APIs all use Postscript names.

The Photoshop APIs supports using fonts from two locations:
- [Currently Installed Fonts](SupportedFonts.md)
- Fonts the user is authorized to access via [Typekit](https://fonts.adobe.com/fonts). (Currently only available for OAuth tokens, service token support is forthcoming...)

If your font is not included in either of these locations you must include an href to the font in your request. See the api docs for more information.

Font support is a work in progress.
-->

#### フォント

API はすべて Postscript の名称を使用します。

Photoshop API は、次の2箇所からフォントを使うことができます。

- [現在インストールされているフォント](SupportedFonts.md)
- [Typekit](https://fonts.adobe.com/fonts) でユーザーがアクセスを許可されているフォント。（現在、OAuth トークンでのみ利用ができます。サービストークンは近日提供予定です...）

あなたが使いたいフォントが、これらのいずれにも含まれていない場合は、リクエストにフォントへの href を含める必要があります。詳細は API ドキュメントを参照してください。

フォントの対応は開発中の機能です。

<!--
### SmartObject

The Photoshop APIs currently support creating and editing of Embedded Smart Objects. Support for Linked Smart Objects is forthcoming.

- If the replacement image is of same size as of the original, the replaced smart object is placed in the bounding box of the original.
If the replacement image is bigger or smaller than the original image, it fits into the original bounding box maintaining the aspect ratio.
You can change the bounds of the replacement image by passing bounds parameters in the API call.

- In order to replace an embedded smart object that is referenced by multiple layers you need to update all of those layers with the replacement image. Currently only same size image replacement is supported for this scenario.

- Smart Object replacement is supported for file types, `psd`, `tif`, `jpeg` and `png`. We don't support `pdf` and `ai` files yet.

The API's are documented [here](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-document_operations)

We also have an example of replacing a Smart Object within a layer.

[Smart Object Example Code](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#example-6-swapping-the-image-in-a-smart-object-layer)

Smart Object support is a work in progress.
-->

### スマートオブジェクト

Photoshop API は現在、埋め込みスマートオブジェクトの作成と編集ができます。リンクされたスマートオブジェクトは近日提供予定です。

- 置換した画像が元の画像と同じサイズの場合、置換したスマートオブジェクトは元のバウンティングボックスに配置されます。置換した画像が元の画像よりも大きいか、または小さい場合は、アスペクト比を維持しながら元のバウンティングボックスに収まります。API 呼び出しのときに座標パラメータを渡すことで、置換する画像の座標を変更できます。

- 複数のレイヤーから参照されている埋め込みスマートオブジェクトを置き換えるには、それらのレイヤーすべてを置換する画像で更新する必要があります。 現在、この利用方法は、同じサイズの画像での置換のみが対応しています。

- スマートオブジェクトの置換は、ファイルの種類で `psd`、 `tif`、 `jpeg`、 `png` が対応しています。 `pdf` および `ai` ファイルはまだ対応していません。

API のドキュメントは [こちら](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-document_operations)

レイヤー内のスマートオブジェクトを置き換えるサンプルもあります。

[スマートオブジェクトのサンプルコード](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#example-6-swapping-the-image-in-a-smart-object-layer)

スマートオブジェクトの対応は開発中の機能です。

<!--
### Compatibility with Photoshop versions

1. The API’s will open any PSD created with Photoshop 1.0 through the current release and this will always be true.
2.  When saving as PSD, the API’s will create PSD’s compatible with the current shipping Photoshop.
3.  In regards to “maximize compatibility” referenced in [https://helpx.adobe.com/photoshop/using/file-formats.html#maximize_compatibility_for_psd_and_psb_files](https://helpx.adobe.com/photoshop/using/file-formats.html#maximize_compatibility_for_psd_and_psb_files)  the API's default to “yes”
-->

### Photoshopバージョンとの互換性

1. API は、Photoshop 1.0 から最新のバージョンまでに作成された PSD を開くことができます。これはつねに当てはまります。
2. PSD として保存する場合、API は現在出荷されている Photoshop に互換性のある PSD を作成します。
3. [https://helpx.adobe.com/photoshop/using/file-formats.html#maximize_compatibility_for_psd_and_psb_files](https://helpx.adobe.com/photoshop/using/file-formats.html#maximize_compatibility_for_psd_and_psb_files) にある「ファイルの互換性」は、APIのデフォルトは「常にオン」になります。

<!--
## How to use the APIs

The API's are documented at https://adobedocs.github.io/photoshop-api-docs-pre-release/
-->

## API の使用方法

API のドキュメントは https://adobedocs.github.io/photoshop-api-docs-pre-release/ にあります。

<!--
### Example 1: /documentManifest (Retrieving a PSD manifest)

#### Step 1: Initiate a job to retrieve a PSD's JSON manifest

The `/documentManifest` api can take one or more input PSD's to generate JSON manifest files from. The JSON manifest is the tree representation of all of the layer objects contained in the PSD document. Using Example.psd, with the use case of a document stored in Adobe's Creative Cloud, a typical curl call might look like this:
-->

### 例1： /documentManifest（PSD の構造の取得）

#### ステップ1：PSD の JSON 形式を取得するジョブを開始する

`/documentManifest` の API は、1つ以上の PSD から、JSON形式のファイルを生成できます。JSON 形式は、PSD ドキュメントにあるすべてのレイヤーオブジェクトをツリーとして表現したものです。Example.psd というファイルが Adobe Creative Cloud に保存されているとしたとき、典型的な curl の呼び出しは次のようになります。


```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentManifest \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs": [
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ]
}'
```

<!--
This initiates an asynchronous job and returns a response containing the href to poll for job status and the JSON manifest.
-->

これにより、非同期ジョブが開始され、ジョブのステータスとJSON形式をポーリングするための href を含むレスポンスが返されます。

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/pie/psdService/status/63c6e812-6cb8-43de-8a60-3681a9ec6feb"
        }
    }
}
```

<!--
#### Step 2: Poll for status and results

Using the job id returned from the previous call you can poll on the returned `/status` href to get the job status and, upon success, the JSON Manifest
-->

#### ステップ2：ステータスと結果をポーリングする

前回の呼び出しで返されたジョブ ID を使って、 `/status` href をポーリングして、ジョブのステータスを取得し、成功していれば JSON 形式を取得できます。

```shell
curl -X GET \
  https://image.adobe.io/pie/psdService/status/63c6e812-6cb8-43de-8a60-3681a9ec6feb \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```
<!--
#### Step 3: The returned manifest

Once your job completes (and does not report any errors) the status response will contain your document's JSON manifest along with other metadata about the input document. The JSON Manifest is further described in the [api docs](https://git.corp.adobe.com/pages/dice/pie-in-the-sky/#api-Documents-document_manifest_status)
-->

#### ステップ3：返された形式

ジョブが完了すると（そしてエラーが何もなければ）、ステータスのレスポンスには、ドキュメントの JSON 形式とその他のメタデータが含まれます。JSON 形式については、 [API ドキュメント](https://git.corp.adobe.com/pages/dice/pie-in-the-sky/#api-Documents-document_manifest_status) で詳しく説明しています。

```json
{
  "jobId":"63c6e812-6cb8-43de-8a60-3681a9ec6feb",
  "outputs":[
    {
      "input":"files/Example.psd",
      "status":"succeeded",
      "created":"2018-08-24T23:07:36.8Z",
      "modified":"2018-08-24T23:07:37.688Z",
      "layers":[
        {
          "bounds":{
            "height":64,
            "left":12,
            "top":1,
            "width":39
          },
          "id":549,
          "index":8,
          "locked":false,
          "name":"CompanyLogo",
          "type":"smartObject",
          "visible":true
        },
        {
          "bounds":{
            "height":153,
            "left":31,
            "top":334,
            "width":197
          },
          "children":[
            {
              "bounds":{
                "height":136,
                "left":29,
                "top":326,
                "width":252
              },
              "text": {
                "content":"Reset your customers’ expectations.",
                "paragraphStyles":[
                  {   
                    "alignment":"left"
                  }
                ],
                "characterStyles":[{
                  "fontAvailable":true,
                  "fontName":"AdobeClean-Bold",
                  "fontSize":36,
                  "orientation":"horizontal",
                }]               
              },
              "id":412,
              "index":6,
              "locked":false,
              "name":"Reset your customers’ expectations.",
              "type":"textLayer",
              "visible":true
            },
            {
              "bounds":{
                "height":67,
                "left":30,
                "top":452,
                "width":230
              },
              "text":{
                "content":"Get our retail experience article and infographic.",
                "paragraphStyles":[{
                  "alignment":"left"
                }],
                "characterStyles":[{
                  "fontAvailable":true,
                  "fontName":"AdobeClean-Regular",
                  "fontSize":15,
                  "orientation":"horizontal",
                }]
              },
              "id":676,
              "index":5,
              "locked":false,
              "name":"Get our retail experience article and infographic.",
              "type":"textLayer",
              "visible":true
            }
          ],
          "id":453,
          "index":7,
          "locked":false,
          "name":"Headline",
          "type":"layerSection",
          "visible":true
        },
        {
          "bounds":{
            "height":34,
            "left":31,
            "top":508,
            "width":99
          },
          "id":762,
          "index":3,
          "locked":false,
          "name":"CallToAction",
          "type":"smartObject",
          "visible":true
        },
        {
          "bounds":{
            "height":405,
            "left":0,
            "top":237,
            "width":300
          },
          "id":751,
          "index":2,
          "locked":false,
          "name":"BackgroundGradient",
          "type":"layer",
          "visible":true
        },
        {
          "bounds":{
            "height":515,
            "left":-385,
            "top":-21,
            "width":929
          },
          "id":750,
          "index":1,
          "locked":false,
          "name":"HeroImage",
          "type":"smartObject",
          "visible":true
        },
        {
          "bounds":{
            "height":600,
            "left":0,
            "top":0,
            "width":300
          },
          "id":557,
          "index":0,
          "locked":false,
          "name":"Background",
          "type":"layer",
          "visible":true
        }
      ],
      "document":{
        "height":600,
        "name":"Example.psd",
        "width":300
      }
    }
  ],
  "_links":{
    "self":{
      "href":"https://image.adobe.io/pie/psdService/status/8ec6e4f5-b580-41ac-b693-a72f150fec59"
    }
  }
}
```

<!--
### Example 2: /documentOperations (Making PSD edits and renders)

Once you have your PSD file's JSON manifest you can use it to make layer and/or document level edits to your PSD and then generate new renditions with the changes. You can pass in either all or a subset of the JSON manifest to `/documentOperations` as represented in the request body's `options.layers` argument. In other words you can choose to pass `options.layers` as a flat array of only the layers that you wish to act upon and can, if desired, leave out the rest.

The layer id or layer name are used by the service to identify the correct layer to operation upon in your PSD; Note that adding a new layer does not require the ID to be included, the service will generate a new layer id for you.
-->

### 例2： /documentOperations（PSD の編集とレンダリングをする）

PSD ファイルの JSON 形式を取得したら、それを使って、PSD のレイヤーやドキュメントの編集をし、更新した新しい画像を生成することができます。リクエストボディの `options.layers` 引数として、JSON 形式のすべてまたは一部を `/documentOperations` に渡すことができます。言い換えると、 `options.layers` を、編集したいレイヤーのみのフラットな配列として渡すことができ、必要に応じて残りを除外することができます。

レイヤー ID またはレイヤー名は、PSD のなかで編集するレイヤーを正しく識別するために、サービスが使用します。なお、新しいレイヤーを追加するときに、ID を含める必要はありません。サービスによって新しいレイヤー ID が生成されます。

<!--
#### The add, edit and delete objects

The `add`, `edit`, `move` and `delete` blocks are how you communicate that you'd like action taken on that particular layer object. Any layer block passed into the API that is missing the one of these attributes will be ignored.
-->

#### オブジェクトの追加、編集、削除

`add`、 `edit`、 `move`、および `delete` のブロックは、そのレイヤーオブジェクトにするアクションを渡します。これらいずれかの属性のないレイヤーブロックがAPIに渡されても、無視されます。

<!--
#### Step 1: Making a simple edit (to a text layer)

In this example we will be editing a single text layer from Example.psd. We are only including a single layer object in the `options.layers` array. We will be editing layer id 412 from the `/documentManfest` examples above and making the following requests:

- NEW KEYWORD TO INDICATE AN EDIT: The `edit` key is included in layer id 412
- CHANGE LAYER POSITION: The layer's top and left will be set to 0,0
- CHANGE FONT SIZE: The font size will be reduced from 36 to 24 pixels
- CHANGE TEXT CONTENT: The text string will be changed to "Inspire your customers’ creativity."
- CHANGE LAYER NAME: The layer name will be changed to "Inspire your customers’ creativity."
- LOCK THE LAYER: The layer will be locked
- GENERATE RENDITION: We are requesting one new fullsize jpeg rendition
-->

#### ステップ1：かんたんな編集（テキストレイヤーに対して）

以下の例では、Example.psd のひとつのテキストレイヤーを編集します。配列 `options.layers` にはひとつのレイヤーオブジェクトのみを含めています。上記の `/documentManfest` の例をもとに、レイヤー ID 412 を編集する次のリクエストを作成します。

- 「編集」を示すための新しいキーワード： `edit` キーがレイヤー ID 412 に含まれています。
- レイヤーの位置の変更：レイヤーの top と left を 0, 0 にします。
- フォントサイズの変更：フォントサイズを 36 ピクセルから 24 ピクセルへ縮小します。
- テキストコンテンツの変更：テキストの文字列を「Inspire your customers’ creativity.」へ変更します。
- レイヤー名の変更：レイヤー名を「Inspire your customers’ creativity.」へ変更します。
- レイヤーのロック：レイヤーをロックします。
- 画像の生成：新しく、フルサイズの jpeg 画像を1つ生成します。

<!--
```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},                                    // <--- NEW KEYWORD TO INDICATE AN EDIT
        "bounds":{
          "height":136,
          "left":0,                                       // <--- CHANGE LAYER POSITION
          "top":0, 
          "width":252
        },
        "text":{
          "content":"Inspire your customers’ creativity.",    // <--- CHANGE TEXT CONTENT
          "paragraphStyles":[{
            "alignment":"left"
          }],
          "characterStyles":[{
            "fontAvailable":true,
            "fontName":"AdobeClean-Bold",
            "fontSize":24,                                  // <--- CHANGE FONT SIZE
            "orientation":"horizontal",
          }]
        },
        "id":412,
        "index":6,
        "locked":true,                                      // <--- LOCK THE LAYER
        "name":"Inspire your customers’ creativity.",       // <--- CHANGE LAYER NAME
        "type":"textLayer",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example.jpeg",                           // <--- GENERATE RENDITION
      "storage":"adobe", 
      "width":0,
      "type":"image/jpeg"
    }
  ]
}'
```
-->

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},                                    // <--- 「編集」を示すための新しいキーワード
        "bounds":{
          "height":136,
          "left":0,                                       // <--- レイヤーの位置を変更
          "top":0, 
          "width":252
        },
        "text":{
          "content":"Inspire your customers’ creativity.",    // <--- テキストコンテンツを変更
          "paragraphStyles":[{
            "alignment":"left"
          }],
          "characterStyles":[{
            "fontAvailable":true,
            "fontName":"AdobeClean-Bold",
            "fontSize":24,                                  // <--- 文字サイズを変更
            "orientation":"horizontal",
          }]
        },
        "id":412,
        "index":6,
        "locked":true,                                      // <--- レイヤーをロック
        "name":"Inspire your customers’ creativity.",       // <--- レイヤー名を変更
        "type":"textLayer",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example.jpeg",                           // <--- ファイルを生成
      "storage":"adobe", 
      "width":0,
      "type":"image/jpeg"
    }
  ]
}'
```

<!--
This initiates an asynchronous job and returns a request body containing the href to poll for job status and requested rendition information.
-->

これにより、非同期ジョブが開始され、ジョブのステータスと生成される画像の情報をポーリングするための href を含むレスポンスボディが返されます。

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/pie/psdService/status/8ad955af-e511-4c6f-845b-193c7bbba9b9"
        }
    }
}
```
<!--
#### Step 2: Poll for status and results

Using the job id returned from the previous call you can poll on the returned `/status` href to get the status for the edit job and each requested output
-->

#### ステップ2：ステータスと結果をポーリングする

前回の呼び出しで返されたジョブ ID を使って、 `/status` href をポーリングして、編集のジョブとそれぞれのリクエストの出力のステータスを取得します。

```shell
curl -X GET \
  https://image.adobe.io/pie/psdService/status/8ad955af-e511-4c6f-845b-193c7bbba9b9 \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

<!--
And this will return a request body containing the job status for each requested output and eventually either errors or the hrefs to the requested outputs
-->

そしてこれは、リクエストそれぞれのジョブのステータスを含むリクエストボディを返し、最終的には、エラーまたはリクエストされた出力への href のいずれかを返します。

```json
{
  "jobId":"8ad955af-e511-4c6f-845b-193c7bbba9b9",
  "outputs":[
    {
      "input":"/files/Example.psd",
      "status":"succeeded",
      "created":"2018-01-04T12:57:15.12345:Z",
      "modified":"2018-01-04T12:58:36.12345:Z",
      "_links":{
        "renditions":[
          {
            "href":"/files/Example.jpeg",
            "storage":"adobe",
            "type":"vnd.adobe.photoshop"
          }
        ]
      }
    }
  ],
  "_links":{
    "self":{
      "href":"https://image.adobe.io/pie/psdService/status/8ad955af-e511-4c6f-845b-193c7bbba9b9"
    }
  }
}
```

<!--
#### Step 3: Adding a new adjustment layer

This example shows how you can add a new brightnessContrast adjustment layer to the top of your PSD.  Things to note:

- NEW KEYWORD TO INDICATE AN ADDITION: The `add` key is included, along with `insertAbove` in the new layer object to indicate exactly where you want the new layer placed in the overall Manifest tree. 
- LAYER TYPE IS REQUIRED: The type indicates you want a new layer of type adjustment layer.
- LAYER ID AND INDEX ARE NOT PRESENT: The layer index and id are not supported for add operations. The index is implied by the objects position in the manifest tree and the ID will be generated by the service and returned to you in subsequent calls to `/documentManifest`
-->

#### ステップ3：新しい調整レイヤーを追加する

以下の例は、PSD の上に、新しい「明るさ・コントラスト」の調整レイヤーを追加します。注意事項：

- 「追加」を示すための新しいキーワード：ツリー全体のどこに新しいレイヤーを追加するのかを正確に示すために、新しいレイヤーオブジェクトに `insertAbove` をもつ `add` キーが含まれています。
- レイヤーの種類は必須：種類は、どの調整レイヤーを新しく追加したいのかを示します。
- レイヤー ID とインデックスは存在しない：レイヤーのインデックスと ID は、「追加」の操作には対応していません。インデックスはツリー内のオブジェクトの位置によって暗に示され、ID はサービスによって生成され、以降の `/documentManifest` の呼び出しで返されます。

<!--
```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {                                       
        "add":{                                     // <--- NEW KEYWORD TO INDICATE AN ADDITION
          "insertAbove": {
            "id": 549
          }                         // <--- INDICATES THE LAYER SHOULD BE CREATED ABOVE ID 549
        },
        "adjustments":{
          "brightnessContrast":{
            "brightness":25,
            "contrast":-40
          }
        },
        "name":"NewBrightnessContrast",
        "type":"adjustmentLayer"              // <--- LAYER TYPE IS REQUIRED
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.jpeg",
      "storage":"adobe",
      "type":"image/jpeg"
    }
  ]
}'
```
-->

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {                                       
        "add":{                               // <--- 「追加」を示すための新しいキーワード
          "insertAbove": {
            "id": 549
          }                     // <--- レイヤーが ID:549 の上に生成されることを示す
        },
        "adjustments":{
          "brightnessContrast":{
            "brightness":25,
            "contrast":-40
          }
        },
        "name":"NewBrightnessContrast",
        "type":"adjustmentLayer"              // <--- レイヤーの種類は必須
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.jpeg",
      "storage":"adobe",
      "type":"image/jpeg"
    }
  ]
}'
```

<!--
#### Step 4: Editing the image in a pixel layer

In this example we want to replace the image in an existing pixel layer, the Hero Image layer in Example.psd. We are requesting the following:

- NEW KEYWORD TO INDICATE AN EDIT: The `edit` key is included to indicate we want to edit this layer
- NEW KEYWORD TO INDICATE IMAGE REPLACEMENT INFO: The `layers.input` object is included to indicate where the replacement image can be found
-->

#### ステップ4：ピクセルレイヤーの画像を編集する

以下の例は、既存のピクセルレイヤー（Example.psd の「HeroImage」レイヤー）の画像を置き換えます。 以下をリクエストします。

- 「編集」を示すための新しいキーワード：このレイヤーを編集することを示すために、 `edit` キーが含まれます。
- 置換する画像の情報を示すための新しいキーワード：置換する画像がある場所を示すために、 `layers.input` オブジェクトが含まれます。

<!--
```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},                                                                              // <--- NEW KEYWORD TO INDICATE AN ADDITION
        "input":{                                       // <--- NEW KEYWORD TO INDICATE IMAGE REPLACEMENT INFO
          "href":"/files/newBackgroundImage.jpeg",
          "storage":"adobe"
        },
        "bounds":{
          "height":405,
          "left":0,
          "top":237,
          "width":300
        },
        "id":751,
        "index":2,
        "locked":false,
        "name":"BackgroundGradient",
        "type":"layer",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}
'
```
-->

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},                    // <--- 「編集」を示すための新しいキーワード
        "input":{                                       // <--- 置換する画像の情報を示すための新しいキーワード
          "href":"/files/newBackgroundImage.jpeg",
          "storage":"adobe"
        },
        "bounds":{
          "height":405,
          "left":0,
          "top":237,
          "width":300
        },
        "id":751,
        "index":2,
        "locked":false,
        "name":"BackgroundGradient",
        "type":"layer",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}
'
```

<!--
#### Step 5: Creating new Renditions

See the `/renditionCreate` examples below as the format for the `outputs` object in the request body is identical
-->

#### ステップ5：新しい画像を作成する

リクエストボディの `outputs` オブジェクトの形式は、以下の `/renditionCreate` の例を参照してください。

<!--
#### Step 6: Swapping the image in a smart object layer

In this example we want to swap the smart object in an existing embedded smart object layer, the Hero Image layer in Example.psd. We are requesting the following:

- The `edit` key is included to indicate we want to edit this layer
- The `layers.input` object is included to indicate where the replacement image can be found
- The `layers.smartObject` object is included to indicate specific information related to this image as SO

All the files used in the example are available in [sample_files](https://github.com/AdobeDocs/photoshop-api-docs/tree/master/sample_files). You can download the files and put it in your CC account or any storage(AWS, Azure or Dropbox).
-->

#### 手順6：スマートオブジェクトレイヤーの画像を置き換える

以下の例は、既存の埋め込みスマートオブジェクトレイヤー（Example.psd の「HeroImage」レイヤー）のスマートオブジェクトを置き換えます。以下をリクエストします。

- このレイヤーを「編集」することを示すために、 `edit` キーが含まれます。
- 置換する画像がある場所を示すために、 `layers.input` オブジェクトが含まれます。
- スマートオブジェクトとしてのこの画像に関連する情報を示すために、 `layers.smartObject` オブジェクトが含まれています。

例で使われているすべてのファイルは、 [sample_files](https://github.com/AdobeDocs/photoshop-api-docs/tree/master/sample_files) にあります。ファイルをダウンロードして、Creative Cloud アカウントまたは任意のストレージ（AWS、Azure、Dropbox）に置いてください。

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},     
        "input":{                                       
          "href":"files/heroImage.png", 
          "storage":"adobe"
        },
        "smartObject" : {               
                "type" : "image/png",
                "linked" : false
        },
        "attributes":{
          "bounds":{
            "height":515,
            "left":-385,
            "top":-21,
            "width":929
          }
        },
        "id":750,
        "index":1,
        "locked":false,
        "name":"HeroImage",
        "type":"smartObject",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}
'
```

<!--
### Example 3: /renditionCreate (Generating New Renditions)

The `/renditionsCreate` endpoint can take a number of input PSD files and generate new image renditions or a new PSD
-->

### 例3： /renditionCreate（新しい画像の生成）

`/renditionsCreate` エンドポイントは、多数の PSD ファイルを受け取り、新しい画像または新しい PSD を生成できます。

<!--
##### Step 1: A single file input

In this example we are requesting two different outputs from our Example.psd input:

- Example.jpeg is a new JPEG rendition that has a width of 512 pixels
- Example.png is a new fullsize PNG rendition
-->

##### ステップ1：ファイルがひとつのとき

以下の例では、ひとつの Example.psd から2つの異なる出力をリクエストしています。

- Example.jpeg は、幅が 512 ピクセルの新しい JPEG 画像です。
- Example.png はフルサイズの新しい PNG 画像です。

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/renditionCreate \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "outputs":[
    {
      "href":"files/Example.jpeg",         
      "width": 512,
      "storage":"adobe",
      "type":"image/jpeg"     
    },
    {
      "href":"files/Example.png",
      "storage":"adobe",
      "type":"image/png"
    }
  ]
}
'
```

<!--
This initiates an asynchronous job and returns a request body containing the href to poll for job status and requested rendition information.
-->

これにより、非同期ジョブが開始され、ジョブのステータスと生成される画像の情報をポーリングするための href を含むレスポンスボディが返されます。

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/pie/psdService/status/de2415fb-82c6-47fc-b102-04ad651c5ed4"
        }
    }
}
```

<!--
#### Step 2: Poll for status and results

Using the job id returned from the previous call you can poll on the returned `/status` href to get the status for each requested output
-->

#### ステップ2：ステータスと結果をポーリングする

前回の呼び出しで返されたジョブ ID を使って、 `/status` href をポーリングして、それぞれのリクエストの出力のステータスを取得します。

```shell
curl -X GET \
  https://image.adobe.io/pie/psdService/status/de2415fb-82c6-47fc-b102-04ad651c5ed4 \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

<!--
This will return a request body containing the job status for each requested output
-->

これは、リクエストそれぞれの出力のジョブのステータスを含むリクエストボディを返します。

```json
{
  "jobId":"de2415fb-82c6-47fc-b102-04ad651c5ed4",
  "outputs":[
    {
      "input":"/files/Example.psd",
      "status":"succeeded",
      "created":"2018-01-04T12:57:15.12345:Z",
      "modified":"2018-01-04T12:58:36.12345:Z",
      "_links":{
        "renditions":[
          {
            "href":"files/Example.jpeg",         
            "width": 512,
            "storage":"adobe",
            "type":"image/jpeg"   
          },
          {
            "href":"files/Example.png",
            "storage":"adobe",
            "type":"image/png"
          }
        ]
      }
    }
  ],
  "_links":{
    "self":{
      "href":"https://image.adobe.io/pie/psdService/status/de2415fb-82c6-47fc-b102-04ad651c5ed4"
    }
  }
}
```

<!--
#### Step 3: A folder input (multiple files)

In this example we are requesting new full size jpeg renditions from an input folder containing multiple PSD documents.

Note that the `outputs` object is using file tokens, $FileName, to create new files with the same names as the input files found
-->

#### ステップ3：フォルダごとのとき（複数のファイル）

以下の例では、複数の PSD ドキュメントを含んでいるフォルダから、フルサイズの新しい jpeg 画像をリクエストしています。

注意： `outputs` オブジェクトは、ファイルトークン $FileName を使って、入力したファイルと同じ名前で新しいファイルを生成します。

<!--
```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/renditionCreate \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/my_input_folder",
      "storage":"adobe"
    }
  ],
  "outputs":[
    {
      "href":"files/$FileName.jpeg",           // <--- THE $FileName TOKEN
      "storage":"adobe",
      "type":"image/jpeg",
    }
  ]
}
'
```
-->

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/renditionCreate \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/my_input_folder",
      "storage":"adobe"
    }
  ],
  "outputs":[
    {
      "href":"files/$FileName.jpeg",           // <--- $FileName トークン
      "storage":"adobe",
      "type":"image/jpeg",
    }
  ]
}
'
```

<!--
### Example 4: /smartObject (Replacing smartobject)

The `/smartObject` endpoint can take an input PSD file with an embedded smartobject and can replace with another smartobject.
This API is a simple API developed to ease the smartObject replacement workflow for an user.
-->

### 例4： /smartObject （スマートオブジェクトの置き換え）

`/smartObject` エンドポイントは、埋め込みスマートオブジェクトを含む PSD ファイルを受け取り、別のスマートオブジェクトで置き換えます。
この API は、ユーザーのスマートオブジェクト置換作業を手軽にするために開発されたシンプルな API です。

<!--
##### Step 1: Replacing a SmartObject
This example shows how you can replace an embedded smart object
-->

##### ステップ1：スマートオブジェクトの置き換え
以下の例は、埋め込みスマートオブジェクトを置き換えます。

``` shell
curl -H "Authorization: Bearer $token" \
-H "x-api-key: $api_key" \
-X POST \
https://image.adobe.io/pie/psdService/smartObject \
-d '{
  "inputs": [
  {
    "href": "files/SOCreate.psd",
    "storage": "adobe"
  }],
  "options": {
    "layers": [{
      "name": "New",
      "input": {
        "href": "files/jt-guitar.jpeg",
        "storage": "adobe"
      }
     }
    ]
  },
  "outputs": [
  {
    "storage": "adobe",
    "href": "files/SOedit.psd",
    "type": "vnd.adobe.photoshop"
  }
  ]}'

```

<!--
##### Step 2: Creating a SmartObject
This example shows how you can create an embedded smart object
-->

##### ステップ2：スマートオブジェクトを作成する
以下の例は、埋め込みスマートオブジェクトを作成します。

``` shell
curl -H "Authorization: Bearer $token" \
-H "x-api-key: $api_key" \
-X POST \
https://image.adobe.io/pie/psdService/smartObject
-d '{
  "inputs": [
  {
    "href": "files/SO.psd",
    "storage": "adobe"
  }],
  "options": {
    "layers": [{
      "name": "New",
      "add": {
        "insertTop": true
      },
      "input": {
        "href": "files/jt-drums.jpeg",
        "storage": "adobe"
       }
      }
    ]
  },
  "outputs": [
  {
    "storage": "adobe",
    "href": "files/SOCreate.psd",
    "type": "vnd.adobe.photoshop"
  }
]}'

```

<!--
## Sample Code

The [sample_code](sample_code) folder in this repo contains sample code for calling the Photoshop APIs.

Note that the sample code is covered by the MIT license.
-->

## サンプルコード

このリポジトリの [sample_code](sample_code) フォルダには、Photoshop API を呼び出すサンプルコードがあります。

注意：サンプルコードは MIT ライセンスの対象です。

<!--
## Current Limitations
There are a few limitations to the APIs you should be aware of ahead of time. 
- Multi-part uploads and downloads are not yet supported
- The `/documentOperations` , `/documentManifest`, `/renditionCreate` and `/smartObject` endpoints only support a single PSD input
- Error handling is a work in progress. Sometimes you may not see the most helpful of messages

The file Example.psd is included in this repository if you'd like to experiment with these example calls on your own.
-->

## 現在の制限
API には、事前に知っておくべき制限がいくつかあります。
- マルチパートのアップロードとダウンロードはまだ対応していません。
- `/documentOperations` 、 `/documentManifest` 、  `/renditionCreate` 、および `/smartObject` エンドポイントは、ひとつの PSD ファイルのみに対応しています。
- エラー処理は開発中です。適切なメッセージが表示されない場合があります。

上記のサンプルの呼び出しを試したい場合は、Example.psd がこのリポジトリにあります。

<!--
# ImageCutout

**IMPORTANT: V1 of the Image Cutout service is being deprecated in favor of a new, more performant V2.**

The Image Cutout API is powered by Sensei, Adobe’s Artificial Intelligence Technology, and Photoshop. The API's can identify the main subject of an image and produce two types of outputs. You can create a greyscale [mask](https://helpx.adobe.com/photoshop/using/masking-layers.html) png file that you can composite onto the original image (or any other).  You can also create a cutout where the mask has already composited onto your original image so that everything except the main subject has been removed.
-->

# Image Cutout（画像の切り抜き）

**重要：Image Cutout サービスの V1 は非推奨となり、よりパフォーマンスの高い新しい V2 を採用してください。**

Image Cutout API は Sensei、すなわち Adobe の人工知能技術と、Photoshop から成ります。 API は画像に主に何が写っているかを識別し、2種類の出力をできます。グレースケール [マスク](https://helpx.adobe.com/photoshop/using/masking-layers.html) png ファイルを生成して、元の画像（や、その他の画像）に合成できます。また、マスクがすでに用意されている切り抜きを生成して、元の画像に合成し、主要な被写体以外のすべてを削除することもできます。

<!--
| Original        | Mask           | Cutout  |
| :-------------: |:-------------:| :-----:|
| ![Alt text](assets/sensei_orig.jpg?raw=true "Original Image") | ![Alt text](assets/sensei_mask.png?raw=true "Mask") | ![Alt text](assets/sensei_cutout.png?raw=true "Original Image") |
-->

| 元の画像        | マスク           | 切り抜き  |
| :-------------: |:-------------:| :-----:|
| ![Alt text](assets/sensei_orig.jpg?raw=true "元の画像") | ![Alt text](assets/sensei_mask.png?raw=true "マスク") | ![Alt text](assets/sensei_cutout.png?raw=true "切り抜き") |

<!--
## Version 2

### General Workflow

The typical workflow involves making an API POST call to the endpoint https://image.adobe.io/sensei for which the response will contain a link to check the status of the asynchronous job. Making a GET call to this link will return the status of the job and, eventually, the links to your generated output.
-->

## バージョン2

### 一般的な利用手順

典型的な利用手順は、エンドポイント https://image.adobe.io/sensei に対して API POST での呼び出しをし、そのレスポンスには非同期のジョブのステータスを確認するためのリンクが含まれます。このリンクに GET で呼び出しをすると、ジョブのステータスが返され、最終的には生成された画像へのリンクが返されます。

<!--
### How to use the API's

The API's are documented at [https://adobedocs.github.io/photoshop-api-docs/#api-Sensei](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei)

First be sure to follow the instructions in the [Authentication](#authentication) section to get your token.
-->

### APIの使用方法

API のドキュメントは [https://adobedocs.github.io/photoshop-api-docs/#api-Sensei](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei) にあります。

まず、 [認証](#authentication) の項の指示に従って、トークンを取得してください。

<!--
#### Example 1: Initiate a job to create an image cutout

The `/cutout` api takes a single input image to generate your mask or cutout from. Using Example.jpg, with the use case of a document stored in Adobe's Creative Cloud, a typical curl call might look like this:
-->

#### 例1：画像の切り抜きを作成する

`/cutout` APIは、ひとつの画像を受け取って、マスクまたは切り抜きを生成します。Adobe Creative Cloud に保存されているドキュメントの例として Example.jpg があるとしたとき、一般的な curl 呼び出しは次のようになります。

```shell
curl -X POST \
  https://image.adobe.io/sensei/cutout \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
   "input":{
      "storage":"adobe",
      "href":"/files/images/Example.jpg"
   },
   "output":{
      "storage":"adobe",
      "href":"/files/output/cutout.png",
      "mask":{
         "format":"binary"
      }
   }
}'
```

<!--
This initiates an asynchronous job and returns a response containing the href to poll for job status and the JSON manifest.
-->

これにより、非同期ジョブが開始され、ジョブのステータスと JSON 形式をポーリングするための href を含むレスポンスが返されます。

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/sensei/status/e3a13d81-a462-4b71-9964-28b2ef34aca7"
        }
    }
}
```

<!--
Using the job id returned from the previous call you can poll on the returned `/status` href to get the job status
-->

前回の呼び出しで返されたジョブ ID を使って、 `/status` href をポーリングして、ジョブのステータスを取得します。

```shell
curl -X GET \
  https://image.adobe.io/sensei/status/e3a13d81-a462-4b71-9964-28b2ef34aca7 \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

<!--
Once the job is complete your successful `/status` response will look similar to the response below; The output will have been placed in your requested location. In the event of failure the errors will be shown instead
-->

ジョブが成功すると `/status` レスポンスは以下のようになります。出力された画像は、リクエストした場所に置かれます。失敗した場合は、代わりにエラーが表示されます。

```json
{
    "jobID": "e3a13d81-a462-4b71-9964-28b2ef34aca7",
    "status": "succeeded",
    "created": "2020-02-11T21:08:43.789Z",
    "modified": "2020-02-11T21:08:48.492Z",
    "input": "/files/images/Example.jpg",
    "_links": {
        "self": {
            "href": "https://image-stage.adobe.io/sensei/status/e3a13d81-a462-4b71-9964-28b2ef34aca7"
        }
    },
    "output": {
        "storage": "adobe",
        "href": "/files/output/cutout.png",
        "mask": {
            "format": "binary"
        }
    }
}
```

<!--
#### Example 2: Initiate a job to create an image mask

The workflow is exactly the same as [creating an image cutout](#example-1-initiate-a-job-to-create-an-image-cutout) except you use the `/mask` endpoint instead of `/cutout`. 
-->

#### 例2：画像マスクを作成するジョブを開始する

利用手順は、 `/cutout` ではなく `/mask`  エンドポイントを使用する以外は、 [画像の切り抜き](#example-1-initiate-a-job-to-create-an-image-cutout) とまったく同じです。

<!--
## Version 1 [DEPRECATED]

### General Workflow

The typical workflow involves making a synchronous API call to the POST endpoint https://sensei.adobe.io/services/v1/predict for which the response will contain a link to the created mask file.
-->

## バージョン1 （非推奨）

### 一般的な利用手順

典型的な利用手順は、POST エンドポイント https://sensei.adobe.io/services/v1/predict へ同期 API 呼び出しをし、レスポンスには生成されたマスクファイルへのリンクが含まれます。

<!--
### How to use the API's

The API's are documented at [https://adobedocs.github.io/photoshop-api-docs/#api-Sensei-ImageCutout_V1](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei-ImageCutout_V1)
-->

### API の使用方法

API ドキュメントは [https://adobedocs.github.io/photoshop-api-docs/#api-Sensei-ImageCutout_V1](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei-ImageCutout_V1) にあります。

<!--
# Lightroom APIs

The Adobe Lightroom APIs allow you to make Lightroom-like automated edits to image files.

## General Workflow

The typical workflow involves making an API POST call to the endpoint https://image.adobe.io/lrService/ for which the response will contain a link to check the status of the asynchronous job. Making a GET call to this link will return the status of the job and, eventually, the links to your generated output.

## How to use the API's

The API's are documented at [https://github.com/AdobeDocs/lightroom-api-docs](https://github.com/AdobeDocs/lightroom-api-docs/)
-->

# Lightroom API

Adobe Lightroom API を使うと、Lightroom のような自動編集を、画像ファイルにすることができます。

## 一般的な利用手順

典型的な利用手順は、エンドポイント https://image.adobe.io/lrService/ に API POST 呼び出しをし、その応答には、非同期ジョブのステータスを確認するためのリンクが含まれます。 このリンクに GET で呼び出しをすると、ジョブのステータスが返され、最終的には生成された画像へのリンクが返されます。

## APIの使用方法

API ドキュメントは [https://github.com/AdobeDocs/lightroom-api-docs](https://github.com/AdobeDocs/lightroom-api-docs/) にあります。