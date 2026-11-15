### Phase 1: 基本ワークフローと2つのマージ方式 (v0.1.0)
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
