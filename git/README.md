# git　config 設定
    ユーザ名とメアドの登録
    '$  git config --global user.name "{user_name}"'
    '$  git config --global user.email ###@example.com'

# ssh 接続できるように設定

    公開鍵と秘密鍵を配置するディレクトリを作成する。
    '$ mkdir ~/.ssh'

    自分だけが見れる権限設定をする。
    '$ chmod 700 ~/.ssh'

    鍵の作成
    '$ ssh-keygen -t rsa'

    'Enter file in which to save the key (/Users/(username)/.ssh/id_rsa):'
    鍵の名前を聞かれる。
    例: id_git_rsa
    何も入力せずEnterを押すとデフォルトでid_rsaとid_rsa.pubの秘密鍵と公開鍵が作成される。すでに存在する場合は上書きされるから注意

    'Enter passphrase (empty for no passphrase):'
    sshアクセスするときのパスワードを聞かれる
    何も入力せずEnterを２回押せばいい

    公開鍵をGitHubに登録する
        ' https://github.com/settings/ssh '
        で公開鍵の設定ができる

        「title」に公開鍵名、「key」に公開鍵の中身を入れる

    接続を確かめる
        '$ ssh -T git@github.com'
        Hi (account名)! You've successfully authenticated, but GitHub does not provide shell access.
        これが帰ってくればOK

        ただし、鍵を作るときに名前を指定していれば、うまくいかない

        ~/.ssh/configを作成し、その中に
        'Host github github.com
            HostName github.com
            IdentityFile ~/.ssh/id_git_rsa #ここに自分の鍵のファイル名
            User git'
        を保存すれば、

        '$  ssh -T github'

        で接続できる。