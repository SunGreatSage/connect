过年回到老家，GitHub 的SSH拉代码一直出现问题，我又不太喜欢GitHub Desktop，所以修改了下gotoh-connect
修改过的Connect支持多平台，为了避免很多小伙伴没有编译环境，我编译后会发布到Releases，自行下载即可。
首先，你还是需要一台国外的可以 ssh 的机器，或者 ssh 帐号的，又或者你有SOCKS5代理

# 步骤

1. ssh
平时工作的时候，还是需要让 ssh 连接保持的。
```
   ssh -D <port> <username>@<server>
   ssh -D 8989 user@11.1.11.1
   ```
2. 修改 ~/.ssh/config
Windows路径下为：C:\Users\你的用户名\\.ssh
下面是我的config：

```
Host github.com
     HostName           github.com
     User               Kael
     IdentityFile       C:\Users\你的用户名\.ssh\id_ed25519
     IdentitiesOnly     yes
     ProxyCommand connect -S 127.0.0.1:1080 %h %p
```

127.0.0.1:1080上述1080请修改成你的代理端口，connect.exe请放到C:\Windows\system32目录下或C:\Windows\都可以，然后保持你代理畅通，或者SSH链接正常即可，到这里开始愉快的玩耍吧。
