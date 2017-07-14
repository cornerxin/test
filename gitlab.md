####　git安装部署
- yum install "Development Tools"
- yum install gettext-devel openssl-devel perl-CPAN perl-devel zlib-devel
- wget https://github.com/git/git/archive/v2.9.2.tar.gz
- tar xvf v2.9.2.tar.gz
- cd git-2.9.2
- make configure
- ./configure --prefix=/usr/local/git --with-iconv=/usr/local/libiconv
- make all doc
- make install install-doc install-html
- sudo vim /etc/profile
- export PATH=/usr/local/git/bin:$PATH
- source /etc/profile
- git --version

#### 建议使用 Omnibus 包安装 GitLab ，因为它安装起来更快、更容易升级版本，而且包含了其他安装方式所没有的可靠性功能。同时我们强烈推荐承载 GitLab 运行的服务器 至少分配4GB的内存 给 GitLab 。
#### 1. 安装并配置必要的依赖关系

如果你想使用 Postfix 发送邮件，请在安装过程中根据提示选择 'Internet Site'。 你也可以用 Sendmail 或者 配置一个自定义的 SMTP 服务 并 把它作为一个 SMTP 服务器。

在 CentOS 系统上，下面的命令将会打开系统防火墙 HTTP 和 SSH 的访问。

- sudo yum install curl openssh-server openssh-clients postfix cronie
- sudo service postfix start
- sudo chkconfig postfix on
- sudo lokkit -s http -s ssh
#### 2. 添加 GitLab 镜像源并安装

- curl -sS http://packages.gitlab.com.cn/install/gitlab-ce/script.rpm.sh | sudo bash
- sudo yum install gitlab-ce

#### 如果你不太习惯使用命令管道的方式安装镜像仓库，你可以在这里找到 完整的安装脚本 或者 选择系统对应的安装包 使用下面的命令手动安装。

- curl -LJO https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el6/gitlab-ce-XXX.rpm
- rpm -i gitlab-ce-XXX.rpm

#### 3. 配置并启动 GitLab

- sudo gitlab-ctl reconfigure

#### 4. 通过浏览器访问上一步配置的域名

第一次访问 GitLab，系统会重定向 url 到重置密码的页面，你需要输入初始化管理员账号的密码。 设置完成后，系统会重定向到登录界面，你就可以使用刚才输入的密码登录系统了。

系统默认的管理员账号为 root， 登录系统后，你可以修改管理员账号为自己喜欢的账号。