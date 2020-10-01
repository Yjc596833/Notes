1.检查SSH Key是否存在
```
    ls ~/.ssh/
```

2.不存在则生成新的SSH key

```
    ssh-keygen t- rsa -b 2048 -C "15868707168@163.com"
    直接回车，输出
```

3.将SSH key 添加到ssh-agent

```
    先确认ssh-agent处于启用状态：eval"$(ssh-agent -s)"
    如果输出类似 Agent pid 54 等
    然后将SSH key添加到ssh-agent:
    ssh-add ~/.ssh/id_rsa
    输入刚才设置的密码，如果没有输入，则直接回车
```

4.将SSH key添加到GitHub账户中
```
    直接打开id_rsa.pub这个文件，全选复制；
    打开github->settings->ssh and gpg keys ->new ssh key ->粘贴.
```

问题：执行ssh-add 时如果出现 Could not open a connection to...
```
    ssh-agent bash
```