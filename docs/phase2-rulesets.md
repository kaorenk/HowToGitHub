### Phase 2: ブランチ保護ルールの導入と検証 (v0.2.0)
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
