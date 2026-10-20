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
                <span class="text-xs font-bold px-3 py-1 bg-indigo-100 text-indigo-700 rounded-full">System Specification v1.3</span>
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
                <li><a href="#section-5" class="hover:underline text-indigo-700">5. 技術スタック・非機能要件</a></li>
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
                    <p><strong class="text-slate-900">目的:</strong> エンジニア向けに最適化されたITニュース・技術トレンド収集プラットフォームを提供する。多言語ソースからの情報集約、ローカル環境でのAIによる要約、およびユーザーごとの情報管理を単一の<strong>デスクトップアプリケーション（Tauri）</strong>上で実現する。</p>
                    <p><strong class="text-slate-900">情報収集元:</strong> 外部ニュースソースとして「GNews API」を活用し、クラウドのサーバー側で定期的に記事データを取得・蓄積してクライアントへ配信する。</p>
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
                            <p class="text-sm text-slate-700 leading-relaxed">記事詳細、言語切替、AIローカル要約、マイメモ入力欄（自動保存）、関連記事リンク。</p>
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
                        <li><strong class="text-slate-900">記事収集・API管理 (GNews API):</strong> GNews APIを利用して記事情報を収集。API制限を回避するため、クラウドのサーバー側で定期バッチ処理としてデータを取得し、MariaDBにキャッシュしてクライアントへ配信する。</li>
                        <li><strong class="text-slate-900">アカウント・ブックマーク管理 (独自認証):</strong> <strong>専用のログインIDとパスワードによる認証機能</strong>を実装。自動既読化、ワンクリックのブックマーク、独自の「マイメモ」をリモートのWebサーバー側（MariaDB）へ同期・永続化する。</li>
                        <li><strong class="text-slate-900">AI要約 & 多言語対応 (ローカル実行):</strong> ユーザーのPC上で動作する軽量なAIモデルを利用して長文記事を要約する。<strong>アプリの初回起動時にAIモデル本体をダウンロード・インストールする設計</strong>とし、以後はサーバーへのデータ送信なしで安全かつ高速なローカル推論を実現する。</li>
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
                        <h3 class="font-bold text-slate-800 mb-2">Article Object (記事データ)</h3>
                        <div class="bg-slate-100 border border-slate-300 text-slate-900 p-5 rounded-xl text-sm font-mono overflow-x-auto leading-relaxed shadow-inner">
<pre>{
  "id": "string (一意の識別子)",
  "region": "string ('jp' または 'global')",
  "title": "string (タイトル)",
  "description": "string (GNews API概要文)",
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
                    技術スタック & アーキテクチャ
                </h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 text-base text-slate-800">
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">クライアント側 (デスクトップアプリ)</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li>UI / View: React + Tailwind CSS (v3)</li>
                            <li>ネイティブ基盤: Tauri (Rust)</li>
                            <li>チャート描画: Chart.js</li>
                            <li>AI推論処理: アプリ初回起動時にモデルをローカルストレージへDLし、TauriのRust側またはWebGPU経由で実行。</li>
                        </ul>
                    </div>
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">サーバー側 (クラウド環境)</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li>APIサーバー: Rust (Axum または Actix-web)</li>
                            <li>データベース: MariaDB (記事キャッシュ、ユーザーデータ保存)</li>
                            <li>バッチ処理: GNews APIからの記事取得、トレンド集計用の定期実行タスク</li>
                        </ul>
                    </div>
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200 md:col-span-2">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">セキュリティ・非機能要件</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li><strong class="text-slate-900">役割の完全分離:</strong> Tauriアプリ（クライアント）からMariaDBへの直接接続は禁止。必ずクラウド上のRust APIサーバーを介してセキュアな通信（HTTPS通信とトークン認証）を行う。</li>
                            <li><strong class="text-slate-900">認証セキュリティ:</strong> ユーザーのパスワードは平文で保存せず、サーバー側で適切にハッシュ化（Argon2等）して管理する。</li>
                            <li><strong class="text-slate-900">APIキー保護:</strong> GNews APIのシークレットキーはクライアントアプリ内に含めず、サーバー側の環境変数で安全に管理する。</li>
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
