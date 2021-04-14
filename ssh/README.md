# ssh 最初にすること

    公開鍵と秘密鍵を配置するディレクトリを作成する。
    '$ mkdir ~/.ssh'

    自分だけが見れる権限設定をする。
    '$ chmod 700 ~/.ssh'

    鍵の作成
    '$ ssh-keygen -t rsa'

    'Enter file in which to save the key (/Users/(username)/.ssh/id_rsa):'
    鍵の名前を聞かれる。何も入力せずEnterを押すとデフォルトでid_rsaとid_rsa.pubの秘密鍵と公開鍵が作成される。すでに存在する場合は上書きされるから注意

    'Enter passphrase (empty for no passphrase):'
    sshアクセスするときのパスワードを聞かれる
    何も入力せずEnterを２回押せばいい

    ~/.ssh/configを作成し、その中に
        'Host github github.com
            HostName github.com
            IdentityFile ~/.ssh/id_git_rsa #ここに自分の鍵のファイル名
            User git'
        を保存する
