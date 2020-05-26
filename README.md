# iterm2-zmodem
在 Mac 下，实现与服务器进行便捷的文件上传和下载操作

# 步骤

1.安装支持rz和sz命令的lrzsz：`brew install lrzsz`

2.下载iTerm2-zmodem
```
sudo wget https://raw.github.com/coding-lee/iterm2-zmodem/master/iterm2-send-zmodem.sh -O /usr/local/bin/iterm2-send-zmodem.sh

sudo wget https://raw.github.com/coding-lee/iterm2-zmodem/master/iterm2-recv-zmodem.sh -O /usr/local/bin/iterm2-recv-zmodem.sh

sudo chmod 777 /usr/local/bin/iterm2-*
```

3.检查是否安装成功

```bash
ls -lah /usr/local/bin/sz
ls -lah /usr/local/bin/rz

ls -lah /usr/local/bin/iterm2-*
```

4.设置Iterm2的Tirgger特性，profiles->default->editProfiles->Advanced中的Tirgger

    添加两条trigger，分别设置 Regular expression，Action，Parameters，Instant如下：

```
1.第一条
        Regular expression: rz waiting to receive.\*\*B0100
        Action: Run Silent Coprocess
        Parameters: /usr/local/bin/iterm2-send-zmodem.sh
        Instant: checked
2.第二条
        Regular expression: \*\*B00000000000000
        Action: Run Silent Coprocess
        Parameters: /usr/local/bin/iterm2-recv-zmodem.sh
        Instant: checked
```
