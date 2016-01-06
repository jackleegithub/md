#SSHD设置
SSH有两个版本，一个是SSH2，另一个是OpenSSH，红帽用的是OpenSSH，可以使用ssh-keygen进行转换，
* SSH2转OpenSSH:`ssh-keygen -i `
* OpenSSH转SSH2:`ssh-keygen -e `

要使用Public key 认证，必须在服务端设置，sshd的配置文件在/etc/ssh/sshd-configure.
* PubkeyAuthentication yes #允许公钥认证
* AuthorizedKeysFile .ssh/authorized_keys #保存公钥的认证文件
在红帽里把公钥附加在文件authorized_keys中。
