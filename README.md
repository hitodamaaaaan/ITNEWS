<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechFeed Complete - システム仕様書</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
</head>
<body class="bg-slate-100 text-slate-900 font-sans leading-relaxed text-base">

    <div class="max-w-5xl mx-auto px-6 py-12">
        <!-- Header -->
        <header class="border-b border-slate-300 pb-6 mb-8 flex items-center justify-between">
            <div>
                <span class="text-xs font-bold px-3 py-1 bg-indigo-100 text-indigo-700 rounded-full">System Specification v1.4</span>
                <h1 class="text-3xl md:text-4xl font-extrabold tracking-tight mt-3 text-slate-900">TechFeed Complete システム仕様書</h1>
                <p class="text-base text-slate-700 mt-2 font-medium">ITニュース収集・トレンド分析プラットフォーム 要件定義および基本設計書</p>
            </div>
            <button onclick="window.print()" class="px-5 py-2.5 bg-slate-900 text-white rounded-xl text-sm font-semibold hover:bg-slate-800 transition-colors shadow-md">
                PDF / 印刷
            </button>
        </header>

        <!-- Navigation / TOC -->
        <div class="bg-white border border-slate-300 rounded-2xl p-6 mb-8 shadow-sm">
            <h2 class="text-sm font-bold text-slate-700 uppercase tracking-wider mb-3">目次</h2>
            <ul class="grid grid-cols-1 md:grid-cols-2 gap-3 text-base font-semibold">
                <li><a href="#section-1" class="hover:underline text-indigo-700">1. システム概要 & 目的</a></li>
                <li><a href="#section-2" class="hover:underline text-indigo-700">2. 画面レイアウト・UI設計</a></li>
                <li><a href="#section-3" class="hover:underline text-indigo-700">3. 主要機能仕様</a></li>
                <li><a href="#section-4" class="hover:underline text-indigo-700">4. データ構造スキーマ</a></li>
                <li><a href="#section-5" class="hover:underline text-indigo-700">5. 技術スタック・非機能要件 & 規約遵守</a></li>
            </ul>
        </div>

        <!-- Content Sections -->
        <div class="space-y-10">
            <!-- Section 1 -->
            <section id="section-1" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">1</span>
                    システム概要 & 目的
                </h2>
                <div class="space-y-4 text-slate-800 text-base leading-loose">
                    <p><strong class="text-slate-900">目的:</strong> エンジニア向けに最適化されたITニュース・技術トレンド収集プラットフォームを提供する。多言語ソースからの情報集約、ローカル環境でのAIによる要約・翻訳、およびユーザーごとの情報管理を単一の<strong>デスクトップアプリケーション（Tauri）</strong>上で実現する。</p>
                    <p><strong class="text-slate-900">情報収集元:</strong> 外部ニュースソースとして「GNews API」を活用し、利用規約に従って許諾されたメタデータ（タイトル・概要文等）のみをクラウドのサーバー側で定期的に取得・蓄積して配信する。</p>
                    <p><strong class="text-slate-900">対象ユーザー:</strong> ITエンジニア、開発者、テックリードなど、最新技術動向を迅速にキャッチアップしたいプロフェッショナル。</p>
                </div>
            </section>

            <!-- Section 2 -->
            <section id="section-2" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">2</span>
                    画面レイアウト・UI設計
                </h2>
                <div class="space-y-4 text-slate-800 text-base leading-relaxed">
                    <p>本システムはモダンな3カラムダッシュボードUI（デスクトップ最適化）を採用しています。</p>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 mt-4">
                        <div class="p-5 bg-slate-50 rounded-xl border border-slate-200">
                            <h3 class="font-bold text-slate-900 text-lg mb-2">左サイドバー</h3>
                            <p class="text-sm text-slate-700 leading-relaxed">ロゴ、ダークモード切替、日本/グローバル切替、カテゴリ一覧、ビューフィルタ（すべて・ブックマーク・既読・トレンド）。</p>
                        </div>
                        <div class="p-5 bg-slate-50 rounded-xl border border-slate-200">
                            <h3 class="font-bold text-slate-900 text-lg mb-2">中央メインコンテンツ</h3>
                            <p class="text-sm text-slate-700 leading-relaxed">インクリメンタル検索バー、期間フィルタ、フィード更新、サムネイル付き記事一覧カード。</p>
                        </div>
                        <div class="p-5 bg-slate-50 rounded-xl border border-slate-200">
                            <h3 class="font-bold text-slate-900 text-lg mb-2">右スライドパネル</h3>
                            <p class="text-sm text-slate-700 leading-relaxed">記事詳細概要、言語切替、AIローカル要約・翻訳（推論のみ）、マイメモ入力欄（自動保存）、元記事（外部サイト）への直リンク。</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Section 3 -->
            <section id="section-3" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">3</span>
                    主要機能仕様
                </h2>
                <div class="space-y-3 text-slate-800 text-base">
                    <ul class="list-disc list-inside space-y-3 leading-relaxed">
                        <li><strong class="text-slate-900">記事収集・API管理 (GNews API):</strong> GNews APIを利用して記事メタデータ（タイトル・概要・URL等）を収集。※著作権保護およびAPI規約に基づき、**外部記事の「全文」のスクレイピングや保持は行わず、API提供範囲の概要文（Description）のみを対象**とする。API制限回避のためサーバー側で一時的にキャッシュ配信する。</li>
                        <li><strong class="text-slate-900">アカウント・ブックマーク管理 (独自認証):</strong> **専用のログインIDとパスワードによる認証機能**を実装。自動既読化、ワンクリックのブックマーク、独自の「マイメモ」をリモートのWebサーバー側（MariaDB）へ同期・永続化する。</li>
                        <li><strong class="text-slate-900">AI要約 & 多言語対応 (ローカル推論のみ・学習なし):</strong> ユーザーのPC上で動作する軽量AIモデルを利用して概要文の要約および翻訳を行う。**AIはクライアント端末上でのリアルタイム表示・推論（Inference）目的のみに使用し、取得データや推論結果のモデル追加学習（トレーニング）への流用・蓄積は一切行わない。**</li>
                        <li><strong class="text-slate-900">ITトレンド可視化 (自前集計):</strong> データベースに蓄積された記事群から、主要技術スタック（AI/LLM、React、Kube等）の出現回数をサーバー側の日次バッチで独自カウント。結果をChart.jsでトレンド推移グラフとして表示する。</li>
                    </ul>
                </div>
            </section>

            <!-- Section 4 -->
            <section id="section-4" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">4</span>
                    データ構造スキーマ
                </h2>
                
                <div class="space-y-6">
                    <div>
                        <h3 class="font-bold text-slate-800 mb-2">Article Object (記事データ - 全文は含まず概要のみ)</h3>
                        <div class="bg-slate-100 border border-slate-300 text-slate-900 p-5 rounded-xl text-sm font-mono overflow-x-auto leading-relaxed shadow-inner">
<pre>{
  "id": "string (一意の識別子)",
  "region": "string ('jp' または 'global')",
  "title": "string (タイトル)",
  "description": "string (GNews API提供の概要文のみ / 全文非所持)",
  "source": "string (情報源・メディア名)",
  "url": "string (元記事URL)",
  "date": "string (ISO8601日時)"
}</pre>
                        </div>
                    </div>

                    <div>
                        <h3 class="font-bold text-slate-800 mb-2">User Object (ユーザー・ブックマークデータ)</h3>
                        <div class="bg-slate-100 border border-slate-300 text-slate-900 p-5 rounded-xl text-sm font-mono overflow-x-auto leading-relaxed shadow-inner">
<pre>{
  "userId": "string (ログインID)",
  "passwordHash": "string (ハッシュ化パスワード)",
  "bookmarkedArticleIds": ["string"],
  "readArticleIds": ["string"],
  "memos": {
    "articleId": "string (メモ内容)"
  }
}</pre>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Section 5 -->
            <section id="section-5" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">5</span>
                    技術スタック・非機能要件 & 規約遵守
                </h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 text-base text-slate-800">
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">クライアント側 (デスクトップアプリ)</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li>UI / View: React + Tailwind CSS (v3)</li>
                            <li>ネイティブ基盤: Tauri (Rust)</li>
                            <li>チャート描画: Chart.js</li>
                            <li>AI推論処理: 初回起動時に軽量モデルをローカルDLし、表示時のみリアルタイム推論を実施。データ保持・学習は禁止。</li>
                        </ul>
                    </div>
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">サーバー側 (クラウド環境)</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li>APIサーバー: Rust (Axum または Actix-web)</li>
                            <li>データベース: MariaDB (記事概要のキャッシュ、ユーザーデータ保存)</li>
                            <li>バッチ処理: GNews APIからの記事概要取得、トレンド集計用の定期実行タスク</li>
                        </ul>
                    </div>

                    <!-- 規約遵守・コンプライアンス要件 -->
                    <div class="bg-indigo-50/60 border border-indigo-200 p-6 rounded-xl md:col-span-2">
                        <h3 class="font-bold text-indigo-950 text-lg mb-3 flex items-center">
                            <i data-lucide="shield-check" class="w-5 h-5 mr-2 text-indigo-600"></i>
                            GNews API・著作権・AI利用規約遵守（コンプライアンス設計）
                        </h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-800 text-sm leading-relaxed">
                            <li><strong class="text-slate-900">記事全文の未取得・未保持:</strong> 本システムはGNews APIより取得可能な「タイトル・概要文（Description）・元記事URL」のみを扱い、外部メディアの本文全文（Full Content）のスクレイピングおよびデータベース化は行わない。</li>
                            <li><strong class="text-slate-900">AIモデルの利用目的に関する制限（推論のみ・追加学習なし）:</strong> 取得したテキストおよび翻訳・要約データは、クライアントアプリケーション上での閲覧用UI表示（推論処理）にのみ使用する。モデルのファインチューニングやAIトレーニング用データセットとしての保存・利用は固く禁止する。</li>
                            <li><strong class="text-slate-900">データの再配布禁止:</strong> APIから取得したニュースデータおよびAIによる翻訳成果物をパブリックに再配布（APIのサードパーティ公開等）はせず、認証されたアプリ利用者のプライベートなダッシュボード表示用途に限定する。</li>
                            <li><strong class="text-slate-900">APIキーの保護:</strong> GNews APIのシークレットキーはクライアントアプリ内に保持せず、サーバー側の環境変数として安全に管理する。</li>
                        </ul>
                    </div>

                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200 md:col-span-2">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">セキュリティ・その他非機能要件</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li><strong class="text-slate-900">役割の完全分離:</strong> Tauriアプリ（クライアント）からMariaDBへの直接接続は禁止。必ずクラウド上のRust APIサーバーを介してセキュアな通信（HTTPS通信とトークン認証）を行う。</li>
                            <li><strong class="text-slate-900">認証セキュリティ:</strong> ユーザーのパスワードは平文で保存せず、サーバー側で適切にハッシュ化（Argon2等）して管理する。</li>
                        </ul>
                    </div>
                </div>
            </section>
        </div>

        <footer class="mt-12 pt-6 border-t border-slate-300 text-center text-sm font-medium text-slate-600">
            &copy; 2026 TechFeed Complete Pro Edition. All Rights Reserved.
        </footer>
    </div>

    <script>
        lucide.createIcons();
    </script>
</body>
</html>
