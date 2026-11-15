### Phase 3: 本番反映と正式リリース (v0.3.0)
`develop` で検証・整備した内容を本番ブランチ（`main`）へ統合し、配布用テンプレートとしての正式リリース（タグ付与）を行います。

- [ ] **マージ済み作業ブランチの整理**:
  - [ ] GitHub 上で PR マージ後に「Delete branch」ボタンを押してリモートブランチを削除
  - [ ] ローカルを `develop` に切り替え、マージ済みの `feature/<作業内容>` ブランチを削除
- [ ] **main ブランチへの統合（PR作成とマージ）**:
  - [ ] GitHub 上で `base: main` ← `compare: develop` のプルリクエストを作成
  - [ ] PR タイトルを設定（例: `Release v0.2.0: ブランチ保護ルールの導入`）
  - [ ] 差分を確認し、PR をマージ（保護ルールが有効なため PR 経由が必須）
- [ ] **正式リリースタグの作成と公開**:
  - [ ] GitHub の「Releases」画面から **Draft a new release** を開く
  - [ ] **Target**: `main` を選択
  - [ ] **Tag version**: `v0.2.0` を新規入力して指定
  - [ ] リリースタイトル・説明を入力し、**Publish release** を実行
- [ ] **手元（ローカル）の最新化**:
  - [ ] ローカルの `main` をチェックアウトし、最新コミットを pull: `git pull origin main`
  - [ ] リモートで作成した正式タグを手元に同期: `git fetch --tags`