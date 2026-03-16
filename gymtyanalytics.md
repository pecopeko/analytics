# Analytics 仕様メモ

このアプリでは **Firebase Analytics (GA4)** へイベント送信しています。  
現在の実装は `AppAnalytics.initialize()` の条件により **iOSのみ送信** です（Web/Androidは未送信）。

## 1. 収集しているイベント

| 区分 | イベント名 | 主な送信タイミング | 主なパラメータ |
|---|---|---|---|
| 共通ボタン | `button_tap` | `logButtonTap()` 呼び出し時 | `button_id`, `screen` |
| ファネル | `funnel_home_viewed` | ホーム表示 | なし |
| ファネル | `funnel_search_opened` | 検索条件画面を開いた時 | なし |
| ファネル | `funnel_search_validation_error` | 検索条件の入力不足 | `reason` (`prefecture_missing`/`city_missing`) |
| ファネル | `funnel_search_submitted` | 「この条件で検索」実行時 | `region`, `prefecture`, `city_count`, `sports_count` |
| ファネル | `funnel_search_results_viewed` | 検索結果表示時（重複抑止あり） | `result_count`, `prefecture`, `city_count`, `sports_count`, `has_result` |
| ファネル | `funnel_reserve_tapped` | 施設の予約リンクをタップ | `facility_name` |
| ファネル | `funnel_inquiry_opened` | お問い合わせ画面を開く | なし |
| ファネル | `funnel_inquiry_viewed` | お問い合わせ画面表示 | なし |
| ファネル | `funnel_inquiry_submitted` | お問い合わせ送信成功 | なし |
| 要望導線 | `funnel_request_submitted` | 「この市区町村で要望する」成功 | `prefecture`, `city`, `supporters` |
| 要望導線 | `supporters_refreshed` | 「人数を更新」押下後の再取得成功 | `prefecture`, `city`, `supporters` |
| バナー広告 | `ad_banner_loaded` | バナー読み込み成功 | `ad_unit_id` |
| バナー広告 | `ad_banner_failed` | バナー読み込み失敗 | `ad_unit_id`, `error_code` |
| バナー広告 | `ad_banner_impression` | バナーインプレッション発生 | `ad_unit_id` |
| バナー広告 | `ad_banner_clicked` | バナークリック | `ad_unit_id` |
| 全画面広告 | `ad_interstitial_loaded` | 全画面広告読み込み成功 | なし |
| 全画面広告 | `ad_interstitial_failed` | 全画面広告読み込み失敗 | `error_code` |
| 全画面広告 | `ad_interstitial_open_attempt` | 「広告を見る」押下時 | `area_key` |
| 全画面広告 | `ad_interstitial_shown` | 全画面広告表示開始 | `area_key` |
| 全画面広告 | `ad_interstitial_impression` | 全画面広告インプレッション | `area_key` |
| 全画面広告 | `ad_interstitial_clicked` | 全画面広告クリック | `area_key` |
| 全画面広告 | `ad_interstitial_completed` | 広告閉じた後（視聴完了扱い） | `area_key`, `watched_ads` |
| 全画面広告 | `ad_interstitial_show_failed` | 全画面広告表示失敗 | `area_key`, `error_code` |

## 2. `button_tap` の `button_id` 一覧

- `open_search_conditions`
- `open_inquiry`
- `search_submit`
- `open_location_onboarding`
- `open_reserve_link`
- `submit_gym_request`
- `watch_interstitial_ad`
- `share_invite`
- `refresh_supporters`
- `submit_inquiry`
- `open_sns_link`

## 3. 何が分析できるか

- 途中離脱率（検索導線）
  - 例: `funnel_home_viewed` → `funnel_search_opened` → `funnel_search_submitted` → `funnel_search_results_viewed` → `funnel_reserve_tapped`
  - GA4 Funnel Exploration で各ステップの離脱率を確認可能
- 広告の見られ方
  - バナー: `ad_banner_impression`, `ad_banner_clicked`
  - 全画面: `ad_interstitial_shown`, `ad_interstitial_impression`, `ad_interstitial_completed`, `ad_interstitial_clicked`
- どのボタンが押されているか
  - `button_tap` を `button_id` / `screen` で集計

## 4. 補足

- `funnel_search_results_viewed` は同一条件での過剰送信を避けるため、内部でキー管理して重複送信を抑止しています。
- Firebase/GA4の管理画面で集計しやすくするため、必要に応じて `button_id`, `screen` などをカスタム定義として登録してください。
