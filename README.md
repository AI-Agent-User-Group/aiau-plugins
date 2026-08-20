# aiau-plugins

AIAU（[AIエージェントユーザー会](https://aiau.group/)）向けの [Agent Plugin](https://agent-plugins.org/)。コミュニティ運営で使う Agent Skills を、クライアント横断で読み込めるポータブル形式でまとめています。

仕様:

- [Agent Plugins 1.0.0](https://agent-plugins.org/specification)
- [Agent Skills](https://agentskills.io/specification)

## 構成

```text
aiau-plugins/
├── plugin.json
└── skills/
    └── aiau-event-post/
        ├── SKILL.md
        └── references/
            └── templates.md
```

- ルートの `plugin.json` がプラグイン識別子です
- Skills は `skills/` 直下の各ディレクトリ（`SKILL.md` 必須）
- MCP は含みません（`mcp.json` なし）

## インストール

このリポジトリを clone し、対応クライアントのプラグインルートとしてディレクトリ全体を指定してください。

```bash
git clone https://github.com/AI-Agent-User-Group/aiau-plugins.git
```

クライアントが Agent Plugins の `plugin.json` と `skills/` を読む場合、追加の変換は不要です。

## 収録スキル

### aiau-event-post

AIAU 公式 X（[@ai_agent_ug](https://x.com/ai_agent_ug)）向けのイベント告知投稿を生成します。

- 初回告知・追加告知・リマインダー・前日案内・当日告知・開催後御礼・中止/延期・アーカイブ公開
- 140文字制限の検証
- ハッシュタグはユーザー指定（自動生成しない）

使い方の例: 「AIAU のイベント告知ポストを書いて」と URL や日時を渡す。

詳細テンプレートは [skills/aiau-event-post/references/templates.md](skills/aiau-event-post/references/templates.md) にあります。

## スキルの追加

1. `skills/<skill-name>/SKILL.md` を追加する（`name` はディレクトリ名と一致、小文字・ハイフンのみ）
2. 詳細資料は `references/`、スクリプトは `scripts/`、静的ファイルは `assets/` に置く
3. `plugin.json` の `version` と `CHANGELOG.md` を更新する

`plugin.json` にスキルパスを列挙する必要はありません。クライアントは `skills/` 直下を発見します。

## ライセンス

[MIT](LICENSE)
