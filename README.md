# ai-doctrine

AI アシスタント向けの共通ルール集（doctrine）。すべてのプロジェクトに共通する判断の軸・思考プロセス・ツール操作の安全則を定義する。

プロジェクトごとにコピーすると改善が原本に戻らず、版も追えない。そのため、このリポジトリを原本とし、タグで版を管理する。各プロジェクトは `git subtree` で特定の版を `.ai/doctrine/` に取り込む。

## ファイル構成

| ファイル | 役割 |
| --- | --- |
| `PRINCIPLES.md` | 判断の軸。品質判断の優先順位と、設計・実装の判断基準 |
| `WORKFLOW.md` | 思考プロセス。タスクの入口ごとの進め方、検証、報告 |
| `TOOLING.md` | ツール操作の安全則。確認が必須な操作、秘匿情報・個人情報の扱い |

## 取り込み方

取り込み先のプロジェクトのルートで、タグを指定して実行する。

```sh
git subtree add --prefix=.ai/doctrine https://github.com/mackie376/ai-doctrine.git v1.0.0 --squash
```

このリポジトリの中身がそのまま `.ai/doctrine/` に入る。

## 更新の仕方

取り込むタグを変えて `pull` する。`--prefix` と `--squash` は取り込み時と同じにする。

```sh
git subtree pull --prefix=.ai/doctrine https://github.com/mackie376/ai-doctrine.git v1.1.0 --squash
```

各版の変更内容は [GitHub Releases](https://github.com/mackie376/ai-doctrine/releases) のリリースノートを参照する。

## 取り込み先でのルール

- `.ai/doctrine/` は編集しない。改善したい点はこのリポジトリに反映し、新しい版として取り込み直す
- プロジェクト固有のルールは、各プロジェクトの `.ai/project/` に書く

## 版の上げ方

タグは `vMAJOR.MINOR.PATCH` 形式とする。

- **MAJOR**：既存ルールの削除、または意味の変更
- **MINOR**：ルールの追加
- **PATCH**：意味が変わらない表現の修正

変更履歴はファイルにせず、GitHub Releases のリリースノートに書く。

## このリポジトリに置くもの

subtree はリポジトリの中身をまるごと取り込み先に入れる。そのため、CI 設定・スクリプトなど、取り込み先で不要なファイルは置かない。

また、このリポジトリは public である。**プロジェクト固有の情報（顧客・案件・社内事情）は書かない。**

## ライセンス

© 2026 Takashi Makimoto

このリポジトリの内容は [CC BY 4.0](LICENSE) で提供する。
