# 全体アーキテクチャ設計

## コア部分と UI 層の分離

コア機能は Rust ライブラリとして実装し、UI とは分離
FFmpeg などの既存ライブラリを活用して動画処理部分を効率化

## プラグインシステム

Rust の dynamic trait objects を使用したプラグインシステム
AviUtl の既存プラグインとの互換性レイヤーの検討

## パフォーマンス最適化

マルチスレッド処理の活用
GPU アクセラレーションの実装（wgpu/vulkan を使用）

## UI 設計

### モダンな GUI フレームワーク

egui, iced, druid などの Rust 製 GUI フレームワークの活用
もしくは Tauri を使って Web ベースのフロントエンドと Rust バックエンドの組み合わせ

### タイムライン編集

インタラクティブなタイムライン操作の実装
マーカー、スナップ機能などの編集支援機能

### エフェクト編集

ノードベースのエフェクト編集インターフェース
リアルタイムプレビュー機能

## コンポーネント構成

### メディアエンジン

動画・音声の読み込み/デコード (FFmpeg 連携)
フレーム処理パイプライン
エンコード/出力処理

### エフェクトシステム

基本エフェクト（フィルター、トランジションなど）
カスタムエフェクトのスクリプト実装（AviUtl の拡張編集のような機能）

### プロジェクト管理

プロジェクトファイル形式の設計（JSON ベースで検討）
アセット管理システム

### レンダリングエンジン

最終出力のレンダリングパイプライン
GPU アクセラレーション
