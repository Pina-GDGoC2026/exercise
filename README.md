# GDGoC GitHub練習 🚀

このREADMEに自己紹介を追加し、Pull Request（PR）を通してmainに取り込んでみましょう。
**ブランチを作る → READMEを編集 → PRを作る → CIの成功を確認 → 仲間にApproveをもらう → マージ**を練習します。

所要時間は約30分。2人1組で、お互いのPRをレビューします。3人ならA→B→C→A、1人なら運営にレビューを頼んでください。
mainはbranch protectionで保護します。**PR・他の人のApprove・CIの成功がそろうまでマージできません。**

## 1. 準備する

GitHubアカウント、Git、好きなエディタを用意し、このリポジトリへの招待を承認します。
共有リポジトリに直接ブランチを作る方式なので、参加者にはWrite権限が必要です。

```sh
git --version
git clone https://github.com/Pina-GDGoC2026/exercise.git
cd exercise
```

すでにcloneしている場合は、そのフォルダを開くだけでOKです。
初めてGitを使う場合は、コミットに記録する名前とメールアドレスも設定します。

```sh
git config --global user.name "自分の名前"
git config --global user.email "GitHubで使用するメールアドレス"
```

設定済みなら変更不要です。メールを公開したくない場合は、GitHubの **Settings → Emails** にあるnoreplyアドレスを使ってください。
HTTPSの認証にはGitHubのアカウント用パスワードは使えません。ログインで困ったら運営に相談しましょう。

## 2. 自分のブランチを作る

以下の `your-id` は、すべて自分のGitHubユーザー名に置き換えてください。

```sh
git switch main
git pull --ff-only origin main
git switch -c intro/your-id
```

ブランチは、自分の変更を進める作業場所です。mainへ直接pushせず、PRで取り込みます。

## 3. このREADMEに自己紹介を追加する

エディタで `README.md` を開き、**一番下の「参加者の自己紹介」に自分の行を1行追加**してください。
説明や他の人の自己紹介はそのまま残します。本名や連絡先は不要です。
最初の自己紹介と、その直前のコメント行との間には、空行を1行入れてください。

次の例を自分の言葉に変えて追加します。先頭の `-` の後ろには、半角スペースを1つ入れてください。

```markdown
- @your-id / 呼ばれたい名前 / 好きなこと：散歩 / 作りたいもの：空き教室を探すアプリ
```

保存したら、変更を確認してコミット・pushします。

```sh
git diff
git add README.md
git diff --staged
git commit -m "docs: READMEに自己紹介を追加"
git push -u origin intro/your-id
```

`commit` は変更を手元に記録し、`push` はその記録をGitHubへ届けます。
差分表示から抜けられないときは `q` を押してください。

## 4. Pull Requestを作る

1. GitHubで **Pull requests → New pull request** を開く。
2. **base: main / compare: intro/自分のユーザー名** を選ぶ。
3. タイトルを `自己紹介を追加: 自分のユーザー名` にする。
4. 本文に「何を変更したか」と「レビューしてほしいこと」を書く。
5. **Files changed** で、READMEに自分の1行だけが追加されているか確認してPRを作る。

PRは「この変更をmainに入れてよいか」を相談する場所です。
Approveがない状態では、マージがブロックされていることを確認しましょう。CIが失敗している場合も、そのままではマージできません。

## 5. CIの成功を確認する

PRを作るとGitHub Actionsの **Practice CI / test** が動き、PrettierでREADMEの書式を自動チェックします。
PRの **Checks** を開き、最新コミットの `test` が緑になったことを確認しましょう。

書式の指摘が出た場合はログを確認し、READMEを直して同じブランチにコミット・pushします。CIは自動で再実行されます。困ったら運営に相談してください。
Node.jsとnpmが使える人は、次のコマンドで書式を自動で整えることもできます。

```sh
npx --yes prettier@3.9.10 --write README.md
```

## 6. ペアのレビューとApproveをもらう

1. ペアに自分のPRのURLを送り、レビューを頼む。
2. レビュアーは **Files changed** を開き、自己紹介が追加され、他の人の行や説明が消えていないか確認する。
3. 追加された行の横の **＋** から、感想や質問を1つ書いて **Start a review** を選ぶ。
4. 問題がなければ **Review changes → Approve → Submit review** で送信する。
5. 作業者はコメントを読み、返信する。役割を交代して、ペアのPRもレビューする。

レビューはSubmitするまで相手に届きません。自分自身のPRはApproveできません。
修正が必要なら、同じブランチでREADMEを直してコミット・pushしてください。既存PRが更新されるので、PRを作り直す必要はありません。
その場合は新しいコミットのCIが成功したことを確認し、修正後の内容に改めてApproveをもらいます。

## 7. マージして手元を更新する

1. **他の人のApprove**と、**最新コミットのtest成功**がそろったことを確認する。
2. **Squash and merge → Confirm squash and merge** でマージする。
3. PR画面の **Delete branch** でGitHub上の作業ブランチを削除する。
4. 手元もmainへ戻して更新する。

```sh
git switch main
git pull --ff-only origin main
```

READMEを開き、自分と仲間の自己紹介があることを確認できたら完了です！
ペアのPRが後からマージされたら、もう一度pullしてみましょう。

> **コンフリクトが出たら：** みんなが同じREADMEを編集するので、追加した行がぶつかる場合があります。運営とPRの **Resolve conflicts** を開き、両方の自己紹介を残して `<<<<<<<`・`=======`・`>>>>>>>` の印を削除します。解決をコミットしたら、新しいコミットのCI成功を確認し、もう一度レビューを受けてください。force pushは不要です。

## 完了チェック

このチェックリストは各自で振り返るためのものです。README上でチェックを書き換える必要はありません。

- [ ] mainとは別のブランチでREADMEを書き換えた
- [ ] PRの差分を確認した
- [ ] 最新コミットのCIが成功したことを確認した
- [ ] ペアのPRをレビューし、自分のPRにもApproveをもらった
- [ ] マージして、pullで変更を手元へ取り込んだ

<details>
<summary>運営向け：開始前の設定</summary>

教材をmainへpushしてから、次の設定を行います。これらはREADMEやCIだけでは強制できないため、GitHub側での設定が必要です。

1. Issuesはこの演習では使いません。参加者をWrite権限で招待し、招待を承認してもらいます。
2. GitHub Actionsを有効にし、初回pushの **Practice CI / test** が成功したことを確認します。READMEは整形済みの状態で配布します。
3. mainをデフォルトブランチにし、Squash mergeを有効にします。
4. **Settings → Branches** のbranch protection、または **Rules → Rulesets** でmainに次を設定します。
   - **Require a pull request before merging**：有効
   - **Require approvals**：1件
   - **Dismiss stale pull request approvals when new commits are pushed**：有効
   - **Require status checks to pass before merging**：`test` を必須に指定（先ほど成功した実際のチェックを選択）
   - **Do not allow bypassing the above settings**：有効。Rulesetsの場合はバイパスできる人を設定しない
   - force pushとmainの削除：不許可
5. 練習中に更新作業が増えすぎないよう、**Require branches to be up to date before merging** は必須にしない設定を推奨します。
6. 別のアカウントと、Approve前・CI成功前はマージできず、両方がそろうとマージできることを予行します。

保護ルールの利用可否はリポジトリのプラン・公開設定によります。開始前に適用されていることを確認してください。
別のリポジトリで使う場合は、手順1のclone先URLも変更します。

参考：[Prettier CLI](https://prettier.io/docs/cli) / [保護ブランチ](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)

</details>

## 参加者の自己紹介

<!-- この下に、自分の自己紹介を1行追加してください。 -->
