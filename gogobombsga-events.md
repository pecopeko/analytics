# GA Events (Current Implementation)

## 概要
- 計測は以下の実装で有効。
  - **iOSのみ**: `GoogleService-Info.plist` を使った Firebase Analytics
  - iOS以外は no-op（送信なし）
- 共通ファネルイベントとして `funnel_step` を送信。
- `funnel_step` は `flow / step / status` を必須軸として扱う。

## 送信イベント一覧

| event_name | 主な用途 | 主な params |
|---|---|---|
| `app_open` | アプリ起動計測 | なし |
| `select_mode` | タイトル画面でモード選択 | `mode` |
| `screen_view` | 画面表示（現状 online 画面） | `screen_name` |
| `feedback_open` | フィードバック画面遷移 | なし |
| `online_screen_exit` | オンライン画面離脱 | `stage` |
| `online_lifecycle` | ライフサイクル変化 | `state`, `stage`, `connected` |
| `online_rematch_request` | リマッチ要求 | なし |
| `online_auto_disconnect` | 自動切断発生 | なし |
| `online_surrender` | 降参実行 | なし |
| `online_quit_to_title` | タイトルへ戻る操作 | なし |
| `online_leaderboard_open` | リーダーボード表示 | なし |
| `ad_interstitial_prompt_open` | 全画面広告同意ダイアログ表示 | なし |
| `ad_interstitial_prompt_accept_tap` | ダイアログでOKタップ | なし |
| `ad_interstitial_prompt_skip_tap` | ダイアログでスキップタップ | なし |
| `ad_interstitial_prompt_result` | 同意結果 | `accepted` |
| `ad_interstitial_skipped` | 全画面広告が出なかった理由 | `reason`, `counter`, `show_every` |
| `ad_interstitial_loaded` | 全画面広告ロード成功 | なし |
| `ad_interstitial_load_failed` | 全画面広告ロード失敗 | `code`, `message` |
| `ad_interstitial_shown` | 全画面広告表示開始 | なし |
| `ad_interstitial_impression` | 全画面広告インプレッション | なし |
| `ad_interstitial_clicked` | 全画面広告クリック | なし |
| `ad_interstitial_dismissed` | 全画面広告閉じる | なし |
| `ad_interstitial_show_failed` | 全画面広告表示失敗 | `code`, `message` |
| `ad_interstitial_timeout` | 全画面広告待機タイムアウト | なし |
| `ad_interstitial_error` | 全画面広告処理例外 | なし |
| `funnel_step` | 離脱分析用の共通ファネル | `flow`, `step`, `status`, その他補助params |

## `funnel_step` 詳細

### 共通 params
- `flow`: ファネル名（例: `mode_select`, `online_onboarding`）
- `step`: ステップ名（例: `mode_dialog_open`, `match_connected`）
- `status`: 状態（既定値 `view`）
  - 利用中の値: `view`, `attempt`, `success`, `invalid`, `error`, `timeout`, `abandon`

### flow: `mode_select`

| step | status | 追加 params | 意味 |
|---|---|---|---|
| `start_button_tap` | `view` | なし | Startボタン押下 |
| `mode_dialog_open` | `view` | なし | モード選択ダイアログ表示 |
| `mode_dialog_cancel` | `view` | なし | ダイアログをキャンセル |
| `mode_chosen` | `success` | `mode` | モード選択確定 |
| `navigate_from_title` | `success` | `mode` | タイトルから次画面へ遷移 |

### flow: `online_onboarding`

| step | status | 追加 params | 意味 |
|---|---|---|---|
| `screen_open` | `view` | なし | オンライン画面オープン |
| `stage_loading` | `view` | なし | ステージ遷移: loading |
| `stage_identity` | `view` | なし | ステージ遷移: identity |
| `stage_lobby` | `view` | なし | ステージ遷移: lobby |
| `stage_playing` | `view` | なし | ステージ遷移: playing |
| `identity_restored` | `success` | なし | 既存プロフィール復元成功 |
| `identity_required` | `view` | なし | プロフィール登録が必要 |
| `identity_bootstrap` | `timeout` / `error` | なし | 初期プロフィール読込失敗 |
| `identity_submit` | `attempt` | なし | ユーザー名登録送信 |
| `identity_submit` | `invalid` | `reason=empty/too_long` | 入力バリデーション失敗 |
| `identity_submit` | `success` | なし | ユーザー名登録成功 |
| `identity_submit` | `error` | `reason=username_taken/exception` | ユーザー名登録失敗 |
| `match_start_tap` | `attempt` | `entry=host/join/random` | 開始ボタン押下 |
| `match_start_tap` | `invalid` | `entry`, `reason=empty_code` | Join時コード未入力 |
| `match_start` | `invalid` | `reason=missing_profile` | プロフィール不足で開始不可 |
| `match_search_started` | `attempt` | `is_host`, `is_random` | マッチ探索/接続開始 |
| `match_connected` | `success` | `wait_ms`, `is_host`, `is_random` | マッチ接続成功 |
| `match_connected` | `timeout` / `error` | なし | マッチ接続失敗 |
| `match_search_cancel` | `abandon` | なし | 探索中キャンセル |

## 離脱分析の見方（GA4探索）

1. イベント名 `funnel_step` で絞る
2. ディメンション `flow=online_onboarding` を適用
3. ステップを `step` で順序化し、`status` で内訳を見る
4. `match_search_started` -> `match_connected(success)` の落差と、`match_search_cancel(abandon)` を確認

## 実装参照
- `lib/app/analytics/analytics_service.dart`
- `lib/main.dart`
- `lib/ui/screens/title_screen.dart`
- `lib/ui/screens/online_match_screen.dart`
- `lib/ui/screens/online_match_screen_actions.dart`
