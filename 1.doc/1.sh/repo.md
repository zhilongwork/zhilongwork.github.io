
<pre>
mkdir ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
# 如果上面的地址无法访问，可以用下面的：
# curl -sSL  'https://gerrit-googlesource.proxy.ustclug.org/git-repo/+/master/repo?format=TEXT' |base64 -d > ~/bin/repo
chmod a+x ~/bin/repo
echo PATH=~/bin:$PATH >> ~/.bashrc
source ~/.bashrc
</pre>
<pre>
# 拉取LubanCat_Linux_Generic_SDK
repo init -u https://github.com/LubanCat/manifests.git -b linux -m lubancat_linux_generic.xml

#如果运行以上命令失败，提示：fatal: Cannot get https://gerrit.googlesource.com/git-repo/clone.bundle
#则可以在以上命令中添加选项 --repo-url https://mirrors.tuna.tsinghua.edu.cn/git/git-repo

.repo/repo/repo sync -c -j4
</pre>
