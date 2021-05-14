# ssh key

端末ごとにsshキーで認証する方法。

githubアカウントを2つ以上同じ端末で使用すると

httpsでプッシュやクローンができなくなる場合がある。

1. ssh-keygenを実行して秘密鍵と公開鍵を作成。
    - `ssh-keygen -t rsa -C '<email>'`
    - 鍵は.ssh/に作成される。
2. ssh.pub(公開鍵のなかみを)コピー
3. Githubを開く。
4. Settings > SSH and GPG keys > New SSH keysを開く
5. 公開鍵を貼り付け
    - 以降、sshのurlをリモートレポジトリをクローン、プッシュする。
