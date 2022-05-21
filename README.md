# manifest
## 不同的Repo（Github,Gitlab）配置各自的账号去提交
一、配置.ssh文件
ssh-keygen -t rsa -C"你的邮箱"
将公匙拷贝到github ssh key
在.shh下新建config文件
```
#one                                        
Host github
HostName github.com
User one
IdentityFile ~/.ssh/id_rsa_one
#second                            
Host gitlab
HostName gitlab.com
User second
IdentityFile ~/.ssh/id_rsa_second
```
然后执行

```
    ssh-agent bash
    ssh-add id_rsa_one
    ssh-add id_rsa_second
```
测试一下,测试命令
```
ssh -T git@github 
ssh -T git@gitlab
```
接着取消global的user和email
```
　　　　git config --global --unset user.name
　　　　git config --global --unset user.email
```

在不同repo配置各自的user.email
```
　　　　git config user.email "你的第一个github邮箱地址"
　　　　git config user.name "one"

　　　　git config user.email "你的第二个gitlab邮箱地址"
　　　　git config user.name "second"
```
