* * *

license: Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements. See the NOTICE file distributed with this work for additional information regarding copyright ownership. The ASF licenses this file to you under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

           http://www.apache.org/licenses/LICENSE-2.0
    
         Unless required by applicable law or agreed to in writing,
         software distributed under the License is distributed on an
         "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
         KIND, either express or implied.  See the License for the
         specific language governing permissions and limitations
         under the License.
    

* * *

# 概要

Apache は、オープン ソース モバイル開発フレームワークです。 HTML5、CSS3、JavaScript などの標準的な web 技術開発を使用するクロス プラットフォーム、各モバイル プラットフォームのネイティブ開発言語を回避することができます。 アプリケーション各プラットフォームを対象としたラッパー内で実行される各デバイスのセンサー、データ、およびネットワークの状態をアクセスするための標準に準拠した API バインドに依存しています。

Apache コルドバ、Apache ソフトウェア財団 （ASF） 内のトップ レベルのプロジェクトとして 2012 年 10 月に卒業しました。 ASF を使用して将来のコルドバの開発プロジェクトのオープン管理が保証されます。 フリーでオープン ソースのバージョン 2.0 Apache ライセンスの下で常にままになります。詳細については[cordova.apache.org][1]を参照してください。

 [1]: http://cordova.apache.org

場合は、Apache コルドバを使用します。

*   モバイル開発者と各プラットフォームの言語とツールを再実装しなくても 1 つ以上のプラットフォーム上でアプリケーションを拡張する設定します。

*   web 開発者と様々 なアプリケーションの配布用にパッケージ化されている web アプリケーションを配置するポータルを格納します。

*   モバイル開発者、 *WebView* (特別なブラウザー ウィンドウ) デバイス レベルの Api にアクセスできるとネイティブ アプリケーションのコンポーネントを混在することに興味があるまたはネイティブと WebView コンポーネント間のプラグイン インターフェイスを開発する場合。

## 基本的なコンポーネント

Apache コルドバ アプリケーション共通に依存して `config.xml` ファイルをアプリケーションに関する情報を提供し、シフト方向に応答かどうかなど、そのしくみに影響を与えるパラメーターを指定します。 このファイルは W3C の[Web アプリのパッケージ化][2]、または*ウィジェット*は、仕様に準拠しています。

 [2]: http://www.w3.org/TR/widgets/

アプリケーション自体は web ページとして*index.html*、任意の CSS、JavaScript、画像、メディア ファイル、またはその他のリソースを参照するという名前のローカル ファイルを実行するために必要な既定で実装されます。 アプリは、アプリ ストアに配布するネイティブ アプリケーションのラッパー内の*WebView*として実行します。

コルドバ有効 WebView その全体のユーザー インターフェイスを持つアプリケーションがあります。 いくつかのプラットフォームでネイティブのアプリケーション コンポーネントと一緒に、WebView をミックス、大きな、ハイブリッド アプリケーション内のコンポーネントもできます。 （詳細は埋め込み web 表示を参照してください)。

*プラグイン*のインターフェイスはコルドバとネイティブ コンポーネントが互いに通信するために使用できます。 Java スクリプトの設定からのネイティブ コードを呼び出すことができます。 理想的には、そのネイティブ コードに JavaScript Api が複数のデバイス プラットフォームで一貫しました。 バージョン 3.0 は、現在プラグインは標準デバイス Api へのバインディングを提供します。 サード パーティのプラグインはすべてのプラットフォームで必ずしも利用できない機能への追加のバインディングを提供します。 [プラグイン レジストリ][3]にこれらのサード パーティのプラグインを見つけるし、アプリケーションで使用することができます。 プラグイン開発ガイド 』 で説明されているように、独自のプラグインを開発することもできます。 プラグインは、コルドバとカスタム ネイティブ コンポーネント間で通信するなど、必要なことがあります。

 [3]: http://plugins.cordova.io

**注**: バージョン 3.0、それはすべての現在のプラグインを持っていないコルドバ プロジェクトを作成するとき。 これは、新しい既定の動作です。 任意のプラグインは、あなたが望むもコアプラグインは明示的に追加する必要があります。

コルドバは、任意の UI ウィジェットや MV のフレームワークを提供しません。 コルドバのみ実行することができますこれらのランタイムを提供します。 UI ウィジェットや MV * フレームワークを使用したい場合は、それらを選択し、それらをアプリケーションに含める自分でサードパーティ製の材料としてする必要があります。

## 開発パス

バージョン 3.0 は、現在モバイル アプリを作成するのに 2 つの基本的なワークフローを使用できます。多くの場合同じタスクを実行するいずれかのワークフローを使用できますが、彼らはそれぞれ利点があります：

*   **クロスプラット フォーム (CLI) ワークフロー**: このワークフロー、可能な限り多くのモバイル オペレーティング システム上で実行するアプリの場合と少し開発に必要なプラットフォーム固有の使用。 このワークフローを中心に、 `cordova` ユーティリティ、コルドバ*CLI*、コルドバ 3.0 で導入されたとも呼ばれます。CLI は低レベルのシェル スクリプトの機能の大部分を抽象化すること一度に、多くのプラットフォームのためのプロジェクトをビルドすることができます高度なツールです。 CLI はモバイル プラットフォームごとのサブディレクトリを web 資産の共通セットをコピーごとに、必要な構成の変更になります、アプリケーション バイナリを生成するビルド スクリプトを実行します。 CLI はまた、アプリにプラグインを適用する共通インターフェイスを提供します。CLI の詳細は、コマンド ライン インターフェイスを参照してください。 プラットフォームを中心としたワークフローの必要がある場合を除き、プラットフォーム間のワークフローの使用をお勧めします。

*   **プラットフォームを中心としたワークフロー**: このワークフローを使用する単一のプラットフォーム用のアプリの構築に焦点を当てるし、下位レベルで変更することができる必要がある場合。 埋め込み web 表示で説明したようにカスタム ネイティブ コンポーネント コンポーネント web ベース コルドバ、ミックスにアプリをしたい場合はこの方法を使用する必要があります。 親指のルールとして、SDK 内のプロジェクトを変更する必要がある場合、このワークフローを使用します。 このワークフローはサポートされる各プラットフォームとプラグインを適用することができます別の Plugman ユーティリティに適した低レベルのシェル スクリプトのセットに依存します。 クロス プラットフォーム アプリケーションを構築するこのワークフローを使用できますが、一般的により大変だ上位レベル ツールの欠如は別個のビルド サイクルと各プラットフォーム用のプラグインの変更を意味します。 それでも、このワークフロー各 SDK によって提供される開発オプションへのアクセスを許可し、複雑なハイブリッド アプリのために不可欠です。 プラットフォームごとの使用可能なシェル ユーティリティの詳細については様々 なプラットフォームのガイドを参照してください。

最初に始まるとき、は、前述のコマンド ライン インターフェイスでプラットフォーム間のワークフローを使用してアプリを作成する最も簡単な場合があります。 その後、SDK より詳細に制御が必要な場合、プラットフォーム中心のワークフローに切り替えるオプションがあります。 低レベルのシェル ユーティリティは CLI より別のディストリビューションで[cordova.apache.org][1]でご利用いただけます。 CLI で生成される最初プロジェクト、これらのシェルのツールも利用できますで、プロジェクトのさまざまな `platforms/*/cordova` ディレクトリ。

**注**: 1 つのプラットフォーム固有の Sdk およびシェル ・ ツールを中心に、CLI ベースのワークフローから切り替えると、一度戻ることはできません。 CLI は各プラットフォーム固有のソース コードを記述する使用を構築するクロスプラット フォームのソース コードの一般的なセットを保持します。 プラットフォーム固有の資産への変更を維持するためにクロスプラット フォームのソース コードを無視する、プラットフォーム中心のシェルのツールに切り替える必要あるし、代わりにプラットフォーム固有のソース コードに依存します。

## コルドバのインストール

コルドバのインストールは、上記のワークフローを選択するによって異なります。

*   クロス プラットフォームのワークフロー:、コマンド ライン インターフェイスを参照してください。

*   プラットフォームを中心としたワークフロー: プラットフォームのガイドを参照してください。

コルドバをインストールした後の開発をして、モバイル プラットフォームのためのプラットフォームのガイドを確認することをお勧めします。 またプライバシー ガイド、セキュリティ ガイド、次の手順を確認することをお勧めします。 コルドバの構成、config.xml ファイルを参照してください。 Java スクリプトの設定からデバイスのネイティブ機能にアクセスする、プラグイン Api を参照してください。 必要に応じて、他の含まれているガイドを参照してください。