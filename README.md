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
                <span class="text-xs font-bold px-3 py-1 bg-indigo-100 text-indigo-700 rounded-full">System Specification v1.0</span>
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
                    <p><strong class="text-slate-900">目的:</strong> エンジニア向けに最適化されたITニュース・技術トレンド収集プラットフォームを提供する。多言語ソース（日本・グローバル）からの情報集約、AIによる要約、およびユーザーごとの効率的な情報管理（ブックマーク・既読管理・個人メモ）を単一のWebインターフェース上で実現する[cite: 1]。</p>
                    <p><strong class="text-slate-900">対象ユーザー:</strong> ITエンジニア、開発者、テックリード、インフラエンジニアなど、最新技術動向を迅速にキャッチアップしたい個人プロフェッショナル[cite: 1]。</p>
                </div>
            </section>

            <!-- Section 2 -->
            <section id="section-2" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">2</span>
                    画面レイアウト・UI設計
                </h2>
                <div class="space-y-4 text-slate-800 text-base leading-relaxed">
                    <p>本システムはモダンな3カラムダッシュボードUI（デスクトップ最適化 / レスポンシブ対応）を採用しています[cite: 1]。</p>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 mt-4">
                        <div class="p-5 bg-slate-50 rounded-xl border border-slate-200">
                            <h3 class="font-bold text-slate-900 text-lg mb-2">左サイドバー</h3>
                            <p class="text-sm text-slate-700 leading-relaxed">ロゴ、ダークモード、日本/グローバル切替タブ、カテゴリ一覧、ビューフィルタ（すべて・ブックマーク・既読・トレンド）[cite: 1]。</p>
                        </div>
                        <div class="p-5 bg-slate-50 rounded-xl border border-slate-200">
                            <h3 class="font-bold text-slate-900 text-lg mb-2">中央メインコンテンツ</h3>
                            <p class="text-sm text-slate-700 leading-relaxed">インクリメンタル検索バー、期間フィルタ、フィード更新、サムネイル付き記事一覧カード[cite: 1]。</p>
                        </div>
                        <div class="p-5 bg-slate-50 rounded-xl border border-slate-200">
                            <h3 class="font-bold text-slate-900 text-lg mb-2">右スライドパネル</h3>
                            <p class="text-sm text-slate-700 leading-relaxed">記事詳細、言語切替（日本語/原文）、AIローカル要約、マイメモ入力欄（自動保存）、関連記事リンク[cite: 1]。</p>
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
                        <li><strong class="text-slate-900">リージョン管理:</strong> 国内テックブログとグローバルメディア（Hacker News等）のスコープ切り替え[cite: 1]。</li>
                        <li><strong class="text-slate-900">検索・フィルタリング:</strong> キーワード（タイトル・ソース・タグ）および期間（24時間以内/7日以内/全期間）による絞り込み[cite: 1]。</li>
                        <li><strong class="text-slate-900">パーソナライズ管理:</strong> 詳細パネル表示に伴う自動既読化、ワンクリックのブックマーク登録、ユーザー独自の「マイメモ」自動保存機能[cite: 1]。</li>
                        <li><strong class="text-slate-900">AI要約 & 多言語対応:</strong> 長文記事の重要ポイント箇条書き要約、および日本語翻訳と原文の切り替え表示[cite: 1]。</li>
                        <li><strong class="text-slate-900">ITトレンド可視化:</strong> Chart.jsを用いた主要技術スタック（AI/LLM、React、Kube等）のトレンド指数推移グラフ（モーダル表示）[cite: 1]。</li>
                    </ul>
                </div>
            </section>

            <!-- Section 4 -->
            <section id="section-4" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">4</span>
                    データ構造スキーマ (Article Object)
                </h2>
                <!-- 背景を明るいグレー(bg-slate-100)にし、文字を濃い色(text-slate-900)にしてコントラストを改善 -->
                <div class="bg-slate-100 border border-slate-300 text-slate-900 p-5 rounded-xl text-sm font-mono overflow-x-auto leading-relaxed shadow-inner">
<pre>{
  "id": "string (一意の識別子)",
  "region": "string ('jp' または 'global')",
  "category": "string (カテゴリID)",
  "title": "string (日本語タイトル)",
  "titleOrig": "string (原文タイトル)",
  "source": "string (情報源・メディア名)",
  "date": "string (ISO8601日時)",
  "image": "string (サムネイル画像URL)",
  "bookmarked": "boolean (ブックマーク状態)",
  "read": "boolean (既読状態)",
  "summaryJa": ["string"],
  "summaryOrig": ["string"],
  "contentJa": "string",
  "contentOrig": "string",
  "tags": ["string"],
  "memo": "string",
  "relatedIds": ["string"]
}</pre>
                </div>
            </section>

            <!-- Section 5 -->
            <section id="section-5" class="bg-white border border-slate-300 rounded-2xl p-8 shadow-sm">
                <h2 class="text-2xl font-bold mb-4 flex items-center text-slate-900 border-b border-slate-100 pb-3">
                    <span class="w-9 h-9 rounded-lg bg-indigo-100 text-indigo-700 flex items-center justify-center text-base font-bold mr-3">5</span>
                    技術スタック & 非機能要件
                </h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 text-base text-slate-800">
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">技術スタック</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li>Markup: HTML5 / Tailwind CSS (v3)[cite: 1]</li>
                            <li>Icons: Lucide Icons[cite: 1]</li>
                            <li>Chart: Chart.js[cite: 1]</li>
                            <li>Script: Vanilla JavaScript (SPA設計)[cite: 1]</li>
                        </ul>
                    </div>
                    <div class="bg-slate-50 p-5 rounded-xl border border-slate-200">
                        <h3 class="font-bold text-slate-900 text-lg mb-3">非機能要件</h3>
                        <ul class="list-disc list-inside space-y-2 text-slate-700">
                            <li>ダークモード対応（Class toggle）[cite: 1]</li>
                            <li>スムーズなスライドパネルアニメーション[cite: 1]</li>
                            <li>ローカルステートによる高速な応答性[cite: 1]</li>
                        </ul>
                    </div>
                </div>
            </section>
        </div>

        <footer class="mt-12 pt-6 border-t border-slate-300 text-center text-sm font-medium text-slate-600">
            &copy; 2026 TechFeed Complete Pro Edition. All Rights Reserved.[cite: 1]
        </footer>
    </div>
</body>
</html>
