本フォルダは「6.22 SSHによるリモートログイン」に対応しています。

# Dockerコンテナ起動後

以下の手順で進めると良いです。

- ssh-client(192.168.1.12)にexecで入る。
- 「ssh user1@192.168.1.11」で、パスワード入力してSSHログインする。
- 一旦、「exit」で抜けた後、
- 「ssh user2@192.168.1.11」で、公開鍵を用いてパスワード入力なしで、SSHログインする。
- 「exit」で抜ける。
- 次にssh-server(192.168.1.11)に、execで入る。
- /etc/ssh/sshd_configを編集し、「PasswordAuthentication no」という行をどこかに追加する（DockerDesktopのFilesから手動で行うと良い）。これでパスワード入力によるSSHログインができなくなる。
- 「service ssh reload」を実行し、設定ファイルを再読み込みさせる。
- 次にssh-client(192.168.1.12)にexecで入る。
- ssh user1@192.168.1.11」で、SSHログインしようとすると失敗する。