在 Linux 上运行 Sugarchain 节点
----------------------------------

Sugarchain节点仅为帮助全节点钱包加快数据同步速度，出于对性能的考虑，我们强烈推荐您使用`64位`版本软件。

## 最低配置
```
CPU: 1 core
内存: 1024 MB (至少2048 MB swap)
硬盘: 3.65 GB
```

可选项: 如果你仅有1024M内存，那你需要为系统额外设置一个2048M的swap.
- SWAP: https://github.com/sugarchain-project/doc/blob/master/swap.md

可选项: 'UTF-8' 与 '时区'
- https://github.com/sugarchain-project/doc/blob/master/UTF%2Btimezone.md

## 下载
- URL: https://github.com/sugarchain-project/sugarchain/releases/latest
- 文件名: `sugarchain-0.16.3.x-x86_64-linux-gnu.tar.gz`

```
wget filename
```

## 校验 & 解压
```
sha256sum filename # check if hash match
tar -xvzf filename
```

## Crontab

- 运行 crontab
```bash
crontab -e
```

- 添加以下内容:
  * 在每次启动时删除 `debug.log` 以减少硬盘占用.
  * 在系统启动时以`后台驻留`方式启动开放节点.

```bash
# delete logs
@reboot rm $HOME/.sugarchain/debug.log

# run daemon
@reboot $HOME/sugarchain-0.16.3/bin/sugarchaind -server=1 -rpcuser=rpcuser -rpcpassword=rpcpassword -daemon
```

## 防火墙
为Sugarchain开放一些防火墙端口
  * `34230`: Sugarchain主网
  * `44230`: 测试网 (可选)

```
sudo ufw allow 34230 && \
sudo ufw allow 44230 && \
sudo ufw enable && \
sudo ufw status
```

## CLI命令
https://github.com/sugarchain-project/doc/blob/master/cli.md