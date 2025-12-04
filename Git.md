# Git

```bash
# 先获取 GitLab 账号密码，再生成 shh 公钥并粘贴到 GitLab 账号上，完成后获得 url
# 配置信息
git config --list                                      > 查看配置信息列表
git config --global user.name 'JunYangQi'              > 配置用户名
git config --global user.email 'JunYang194@Gmail.com'  > 配置邮箱
ssh-keygen -t rsa -C 'JunYang194@Gmail.com'            > 生成 SHH 公钥

# 仓库管理
git clone url                                          > 克隆到本地库
git remote add origin url                              > 添加一个远程仓库
git remote -v                                          > 列出当前仓库中已配置的远程仓库，并显示它们的URL

# 拉取代码并推送到远程库
git init                                               > 定义当前文件夹为 git 仓库
git add .                                              > 推送到暂存区
git commit -m '备注'                                    > 推送到本地仓库
git pull origin 分支名                                  > 拉取到本地库
git push origin 分支名                                  > 推送到远程库

# 查看代码命令
git reflog                                             > 查看commit历史记录
git status                                             > 查看本地所有已更改的文件
git diff 文件名                                         > 查看本地对应文件的更改
git checkout .                                         > 取消本地所有文件的改动
git checkout 文件名                                     > 取消本地对应文件的改动
git reset --hard 版本号                                 > 版本回退

# 强制覆盖本地代码
git fetch --all                                        > 获取最新的远程分支
git reset --hard                                       > 放弃本地修改，直接覆盖

# 分支管理
git branch                                             > 查看分支
git branch 分支名                                       > 新建分支
git branch -M 分支名                                    > 重命名分支
git branch -D 分支名                                    > 删除分支
git checkout 分支名                                     > 切换分支
git checkout -b 分支名                                  > 新建并切换分支
git merge 分支名                                        > 合并分支

# Git-pull进入vim窗口解决办法
首先按ESC键退出编辑状态，然后按shift+;键，再按wq!保存退出，按q!则为不保存退出；
```

# Xshell

```shell
sudo -u ubuntu -i  > 切换到对应用户分支
```

