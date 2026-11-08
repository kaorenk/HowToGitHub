# HowToGitHub 🚀

GitHubを用いた実践的なワークフローとGit操作を段階的に学ぶハンズオン形式のロードマップです。  
課題を達成したら、チェックボックスを `[x]` に更新して進捗を記録しましょう。


## 📌 ブランチ運用ルール

本リポジトリでは、チュートリアル教材の改善と学習の実践をシンプルに進めるため、以下のブランチ構成で運用します。

### 主要ブランチ
- **`main`**: 配布用テンプレート（完成版）。チェックボックスは未チェック（`[ ]`）の状態で保持します。
- **`develop`**: 学習・作業の統合スペース。日々の課題検証、チェックの記録、解説の加筆はすべてここへ集約します。

### タグ運用の基本ルール
バージョニングとリリースの目的に応じて、タグを付与する対象ブランチを切り分けます。

| 対象ブランチ | タグの種類 | 命名規則の例 | 用途・意味 |
| :--- | :--- | :--- | :--- |
| **`develop`** | プレリリース / 検証タグ | `v0.1.0-alpha`, `v0.1.0-beta` | 学習段階の節目や動作検証、途中経過の記録用 |
| **`main`** | 正式リリース / 配布用タグ | `v0.1.0`, `v1.0.0` | 教材として完成・確定したスナップショット用 |

### 作業ブランチの運用
作業を行う際は、用途（学習実践か、教材の加筆修正か）を問わず、すべて `develop` から **`feature/<作業内容>`** ブランチを切って作業します。

- **命名規則**: `feature/<作業内容>` （例: `feature/phase1-basic-workflow`）
- **マージ先**: `develop`
- **作業内容**: 課題の実行、チェックボックス `[x]` の更新、解説文の追記など、気になった修正はすべて同じブランチ内で同時にコミットして構いません。

> **💡 mainブランチ（配布用）への反映について:**  
> 教材が一通り完成し、白紙テンプレートとして `main` へ反映したくなった段階で、チェックボックス `[x]` を `[ ]` に一括置換して `main` 宛てにマージします。

---

## 🗺️ 学習ロードマップ (Learning Roadmap)

### Phase 1: 基本ワークフローと2つのマージ方式 (v0.1)
まずは保護ルールがない状態で、ローカル完結とリモート（PR）経由の挙動の違いを比較・理解します。


- [ ] **作業ブランチの作成（いずれかの方法で作成）**:
  - [ ] **方法1（ローカル推奨）**: 
    - [ ] ローカルの `develop` をプルして最新化: `git pull origin develop`
    - [ ] `develop` から作業ブランチを作成: `git switch -c feature/<作業内容>`
  - [ ] **方法2（GitHub Web画面）**: 
    - [ ] GitHub上のブランチ選択ドロップダウンから `develop` をベースに新規ブランチ名を入力
    - [ ] ローカルでフェッチして作成したブランチを取得・切り替え
- [ ] **変更とコミット**:
  - [ ] ファイル（README等）を編集・修正
  - [ ] 変更内容をコミット: `git commit -m "docs: ..."` 
- [ ] **PR（Pull Request）経由でのマージ体験**:
  - [ ] 作業ブランチをリモートへ push: `git push -u origin <ブランチ名>`
  - [ ] GitHub上で `develop` 宛てのPR（Pull Request）を作成
  - [ ] 差分を確認し、GitHubのWeb画面上でマージを実行
- [ ] **マージ結果の手元同期とタグ付け**:  
  - [ ] ローカルの `develop` を pull して最新化:  `git pull origin develop`
  - [ ] GitHubの画面（Releases / Tags）からWeb上でタグ `v0.1.0-alpha` を作成・公開
  - [ ] ローカル側でリモートタグを取得して確認: `git fetch --tags`  
- [ ] **（任意・比較検証）ローカルで直接マージ体験**:
  - [ ] ローカルの `develop` に切り替えて `git merge`
  - [ ] ローカルでタグを作成: `git tag v0.1.0-alpha`  
  - [ ] `develop` とタグをリモートへ push: `git push origin develop --tags`   
  - [ ] GitHub上でPRを通さず、ローカルのコミットやタグが直接反映される挙動を確認

---

### Phase 2: ブランチ保護ルールの導入と検証 (v0.2)
チーム開発の安全を守るため、`main` と `develop` への直接 push を禁止する保護ルールを導入します。  

GitHub のリポジトリ画面より、新規ルールセットを作成します。  
`Settings` > `Rules` > `Rulesets` > **New branch ruleset**

- [ ] **ブランチ保護（Repository Rulesets）の設定**:
  - [ ] **Ruleset Name**: 任意の名前を設定（例: `Protect main and develop`）
  - [ ] **Enforcement status**: `Active`（有効）を選択
  - [ ] **Target branches**: `main`（Include default branch）と `develop`（Include by pattern）を指定
  - [ ] **Restrict deletions** を有効化
    - 誤って基幹ブランチが削除されるのを防ぐ
  - [ ] **Block force pushes** を有効化
    - 履歴を上書き・破壊する強制プッシュを防ぐ
  - [ ] **Require a pull request before merging** を有効化
    - 直接 push を禁止し、必ず PR 経由でのマージを強制する
    - ※1人運用の場合は「Required approvals」を `0` に設定
- [ ] **ブロック動作の検証**:
  - [ ] ローカルの `develop` で直接コミットを作成し、`git push origin develop` を実行
  - [ ] エラー（`push declined due to repository rule violations` 等）で push が拒否される挙動を確認する
  - [ ] （後処理）検証用のコミットを取り消す（リセット）、または修正反映のためコミットを引き継いで新しい作業ブランチを作成する
---