# Git

```bash
# 先获取 GitLab 账号密码，再生成 shh 公钥并粘贴到 GitLab 账号上，完成后获得 url
# 配置并克隆到本地库
git config --global user.name 'JunYangQi'                  > 配置用户名
git config --global user.email 'junyang.qi@eigen.capital'  > 配置邮箱
ssh-keygen -t rsa -C 'Email'            > 生成 SHH 公钥
git config --list                       > 查看配置信息列表
git clone url                           > 克隆到本地库
git fetch                               > 获取最新的远程分支
git merge name                          > 合并分支
git reset --hard                        > 放弃本地修改，直接覆盖

# 拉取代码并推送到远程库
git init                                > 定义当前文件夹为 git 仓库
git add .                               > 推送到暂存区
git commit -m '备注'                     > 推送到本地仓库
git pull origin name                    > 拉取到本地库
git push origin name                    > 推送到远程库

# 查看代码命令
git status                              > 查看更改的结果
git diff                                > 查看更改的地方
git reflog                              > 查看历史记录
git reset --hard 版本号                  > 版本穿梭
git checkout 文件名                      > 穿梭到该文件上个版本

# 分支管理
git branch                              > 查看分支
git branch name                         > 新建分支
git branch -M name                      > 重命名分支
git branch -D name                      > 删除分支
git checkout name                       > 切换分支
git checkout -b name                    > 新建并切换分支

# Git-pull进入vim窗口解决办法
首先按ESC键退出编辑状态，然后按shift+;键，再按wq!保存退出，按q!则为不保存退出；
```

# Xshell

```shell
sudo -u ubuntu -i  > 切换到对应用户分支
```

