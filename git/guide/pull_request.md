# プルリクエストの手順

1. `github`で対象のレポジトリを`fork`
2. `fork`したレポジトリを`clone`
    - `git clone url`
3. 新しいブランチを作成し、移動
    - `git branch branch_name`
    - `git checkout branch_name`
4. コードを修正
5. コミット
    - `git add`
    - `git commit`
6. リモート追跡ブランチを更新
    - `git fetch`
7. リモート追跡ブランチを結合
    - `git rebase origin/main` 
8. 衝突が発生した場合、衝突箇所を修正して、`rebase`
    - `git rebase --continue`
9. リモートブランチにプッシュ。
    - `git push origin branch_name`
10. `github`でブランチをプルリクエスト
11. 元レポジトリは`github`でプルリクエストをマージ
12. ローカルレポジトリに反映
    - `git pull origin master`