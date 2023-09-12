# git的学习

查看配置表

```bash
git config -l
```

修改配置

```bash
git config --global user.name '[username]'
```

# git基本理论

![image-20230908204608237](C:\Users\junwe\AppData\Roaming\Typora\typora-user-images\image-20230908204608237.png)

## 本地仓库搭建

初始化

```bash
git init
```

文件存在4种状态

- **untracked:**没有跟踪,通过git add状态变为staged

- **unmodify:**文件已经进库

- **modified:**文件已修改

- **staged:**暂存状态

查看文件状态

```bash
git status [filenames]
```

添加文件到暂存区

```bash
git add [filenames]
git add . //当然文件夹里所有文件
```

暂存区文件到本地仓库

```bash
git commit -m '注释'
```

# 使用github

## 设置本机绑定SSH公钥, 实现免密码登录

### windows:

1. C:\[users]\Administrator\.ssh目录下

```bash
ssh-keygen -t rsa
```

> 官方推荐的rsa加密算法 , 将生成id_rsa.pub和id_rsa两个文件

2. id_rsa.pub文件内容(ssh-rsa ...)复制到Key

> Github > Settings > SSH and GPG keys > New SSH key > Key

### ubuntu:

1.~/目录下

```bash
ssh-keygen -t rsa
```

2.id_rsa.pub文件内容(ssh-rsa ...)复制到Key

```bash
cat ~/.ssh/id_rsa.pub
```

> emmmmm,跟windows的一模一样

## 从本地到远程的流程

1. 在github中新建仓库

> 许可证: GPL-3.0, GPL-2.0 开源但不能商业使用, MIT许可证通常被认为是非常宽松的许可证

2. 将新建的仓库克隆到本地

```bash
git clone [http://....[repositories_name].git]
```

3. 完成修改文件后, 将本地仓库同步到远程仓库

```bash
cd [repositories_name]
git add .
git commit -m "****"
git push
```

