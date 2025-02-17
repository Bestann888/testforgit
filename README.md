
将你的 Git 连接方式从 HTTPS 更改为 SSH。SSH 连接通常更加稳定，并且可以避免一些 TLS 连接问题。
===================================
PS D:\My Project> git remote -v
origin  https://github.com/Bestann888/testforgit.git (fetch)

origin  https://github.com/Bestann888/testforgit.git (push)

PS D:\My Project> git remote set-url origin git@github.com:Bestann888/testforgit.git  
PS D:\My Project> git remote -v                                                       
origin  git@github.com:Bestann888/testforgit.git (fetch)

origin  git@github.com:Bestann888/testforgit.git (push)

PS D:\My Project> git push -u origin main  
===================================

将 Git 连接方式从 HTTPS 改为 SSH 是一种常见的做法，尤其是在遇到 TLS 连接问题时，SSH 通常会更加稳定。以下是如何操作的步骤：

1. 生成 SSH 密钥对

如果你的电脑上还没有 SSH 密钥对，你需要先生成一对。打开你的终端（Git Bash、命令行等），输入以下命令：

Bash

ssh-keygen -t rsa -b 4096 -C "你的邮箱地址"
-t rsa 指定密钥类型为 RSA。
-b 4096 指定密钥长度为 4096 位，这是一个推荐的长度。
-C "你的邮箱地址" 添加一个注释，通常是你的邮箱地址。
按照提示操作，通常情况下直接回车使用默认文件名和位置即可。

2. 将公钥添加到 GitHub

找到你的公钥文件。默认情况下，公钥文件位于 ~/.ssh/id_rsa.pub （Windows 系统可能在 C:\Users\YourUserName\.ssh\id_rsa.pub）。用文本编辑器打开它，复制里面的内容。
登录 GitHub，进入 “Settings” -> “SSH and GPG keys” -> “New SSH key”。
粘贴你的公钥内容，并为这个密钥起一个描述性的名字（例如 “My Laptop”）。
点击 “Add SSH key”。
3. 修改 Git 仓库的远程 URL

查看你当前的远程仓库 URL：

Bash

git remote -v
如果显示的是 HTTPS URL，例如：

origin  https://github.com/Bestann888/testforgit.git (fetch)
origin  https://github.com/Bestann888/testforgit.git (push)
你需要将其修改为 SSH URL。

将远程 URL 修改为 SSH 格式：

Bash

git remote set-url origin git@github.com:Bestann888/testforgit.git
注意将 Bestann888/testforgit.git 替换为你的 GitHub 用户名和仓库名。

再次查看远程仓库 URL，确认已修改成功：

Bash

git remote -v
现在应该显示 SSH URL：

origin  git@github.com:Bestann888/testforgit.git (fetch)
origin  git@github.com:Bestann888/testforgit.git (push)
4. 测试 SSH 连接

你可以尝试运行以下命令来测试 SSH 连接是否配置正确：

Bash

ssh -T git@github.com
如果一切正常，你应该会看到一条欢迎信息，表明你已成功通过身份验证。

5. 推送代码

现在，你应该可以使用 SSH 连接来推送你的代码了：

Bash

git push -u origin main
注意事项

密码短语（Passphrase）： 如果你在生成 SSH 密钥对时设置了密码短语，每次使用 SSH 连接时都需要输入密码短语。
SSH Agent： 为了避免每次都输入密码短语，你可以使用 SSH Agent。SSH Agent 会在后台运行，帮你管理你的密钥。
权限： 确保你的 SSH 私钥文件（id_rsa）的权限设置正确，通常应该是 600（只有你有读写权限）。
关键：将你的 Git 连接方式从 HTTPS 更改为 SSH。SSH 连接通常更加稳定，并且可以避免一些 TLS 连接问题。
echo "# testforgit" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/Bestann888/testforgit.git
git push -u origin main
git remote add origin https://github.com/Bestann888/testforgit.git
git branch -M main
git push -u origin main
