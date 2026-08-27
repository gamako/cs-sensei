# cs-sensei

自分の技能の「一歩外側」を見つけて、手を動かして学ぶための作業リポジトリのテンプレート。

学ぶのはコンピュータサイエンスの原理です。命令とメモリ階層、GC、トランザクション、
並行性、分散、圧縮、評価設計。ただし教科書の目次からは選びません。
**自分の実務や関心のある題材を入口にして、そこから題材が変わっても通じる原理を一つ**選び、
小さく作って測ります。フレームワークの使い方や運用の作法は扱いません。

コーディングエージェントが、実装を代行する役ではなく**本人に手を動かさせる役**として振る舞います。
課題の出し方と伴走の仕方、そして「やらないこと」をまとめてあるので、
エージェントを起動して「学習を始めたい」と言うだけで始まります。

方法そのものは [template/AGENTS.md](template/AGENTS.md) に書いてあります。
中身を確かめてから使うかどうか決めてください。

## コピーして使い始める

このリポジトリの [`template/`](template) の中身が、そのまま自分の作業リポジトリになります。
リポジトリ全体ではなく `template/` だけをコピーしてください。

名前は `my-sensei` を例にします。このテンプレートと区別が付けば何でもかまいません。
GitHub では `<ユーザー名>/` が付くので、名前に自分の名前を入れる必要はありません。

### エージェントに頼む

適当なディレクトリでエージェントを起動して、こう頼むのが一番早いです。

```
https://github.com/gamako/cs-sensei の template/ の中身を使って、
my-sensei という名前で新しいプロジェクトを始めたい。
コピー元の履歴は引き継がず、自分の初回コミットから始めたい。
できたら AGENTS.md を読んで、そのまま学習を始めて
```

これで手元にリポジトリができます。GitHub にも置きたければ、続けて push を頼んでください。

### 自分でやる

```bash
git clone --depth 1 https://github.com/gamako/cs-sensei.git /tmp/cs-sensei
mv /tmp/cs-sensei/template my-sensei
rm -rf /tmp/cs-sensei
cd my-sensei
git init -b main
git add -A && git commit -m "chore: cs-sensei から作成"
```

GitHub に置くなら、`gh` があればそのまま作成して push できます。

```bash
gh repo create my-sensei --private --source=. --push
```

`gh` を使わないなら、画面で空のリポジトリを作ってから push します。

```bash
git remote add origin <作ったリポジトリの URL>
git push -u origin main
```

git clone を経由せず、`template/` だけを落とすこともできます。

```bash
mkdir my-sensei
curl -sL https://github.com/gamako/cs-sensei/archive/refs/heads/main.tar.gz \
  | tar xz -C my-sensei --strip-components=2 cs-sensei-main/template
```

**「Use this template」と「Import repository」は使わないでください。** リポジトリ全体が
`template/` ごと入ってしまいます。Import ではコピー元の履歴も付いてきます。

**フォークも避けてください。** 学習ログを溜め続けるリポジトリなので、fork 関係が
残っていると PR のデフォルトが upstream 向きになって邪魔になります。

## 構成

```
├── README.md    このファイル。テンプレートの説明とコピー手順
└── template/    ここの中身がコピー先になる
    ├── README.md    コピー先の説明
    ├── AGENTS.md    エージェントの振る舞いを決める文書
    ├── log/         学習記録
    └── work/        課題の作業場所
```

`template/` の中のファイルは、コピー先で読まれる前提で書いてあります。
テンプレート固有の話（コピー手順、fork を避ける理由）はこのファイルに集約してください。

## 対応エージェント

Claude Code / Codex / GitHub Copilot。
`template/AGENTS.md` が本体で、`template/CLAUDE.md` と
`template/.github/copilot-instructions.md` はそこへの参照です。

エージェントを増やすときは、参照ファイルを 1 つ足すだけで済みます。

## ライセンス

[CC0 1.0](LICENSE)。`template/` をコピーして使うときに、出典表記も
ライセンス文の同梱も要りません。自分のリポジトリとして好きに扱ってください。
