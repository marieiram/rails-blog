# rails-blog（Rails MVC 版）

Ruby on Rails を使って、投稿＋コメント機能を持つ基本的なWebアプリケーション 
Rails の MVC・認証・権限制御の理解を目的とした学習用プロジェクト

---

## 機能概要

### 投稿（Post）
- 投稿の作成 / 一覧表示 / 詳細表示 / 編集 / 削除
- タイトル・本文を持つ
- 一覧画面では本文を100文字までに省略表示
- 投稿は **ユーザーに紐づく**

### コメント（Comment）
- 投稿に対するコメントの作成 / 削除
- コメントは **投稿・ユーザーに紐づく**
- コメント作成時のバリデーションあり
- 失敗時は投稿詳細画面を re-render してエラー表示

### ユーザー（User）
- Devise によるユーザー認証
- サインアップ / ログイン / ログアウト
- ログイン中のユーザーを `current_user` で取得

---

## 権限制御

- **自分の投稿のみ** 編集・削除可能
- **自分のコメントのみ** 削除可能
- URL直打ちによる不正操作を防ぐため、Controller 側で制御
- 権限制御ロジックは `before_action :authorize_owner!` に共通化

---

## 技術スタック

- Ruby on Rails 8.x
- Ruby 3.x
- SQLite3
- Devise（ユーザー認証）
- Turbo / Hotwire
- ERB
- Git / GitHub

---

## 実装ポイント・学習内容

- Rails MVC の基本構造
- `form_with` と `persisted?` による new / edit の自動切り替え
- Strong Parameters (`params.require(...).permit(...)`)
- バリデーションと re-render の挙動
- partial（`_post.html.erb`, `_comment.html.erb`）によるView分割
- `has_many / belongs_to` の関連付け
- `current_user` を使ったデータ紐付け
- HTTPメソッド（GET / POST / PATCH / DELETE）
- Turbo を使ったフォーム送信・リンク操作

---

## 今後の予定

- このリポジトリをベースとして **Rails API + React** 版を別リポジトリで作成予定
- 見た目（UI/UX）の改善
- API設計・フロントエンド分離の学習

---

## 補足

本リポジトリは **Rails単体（MVC）での基礎理解を目的**として作成しています。  
API化・フロント分離は別リポジトリで行います。
