## Startup
<p>
根据官网的流程安装的环境只可能应用于开发学习环境，而不可能真正的应用到生产环境的，试问哪个公司APP项目会集Server,Android,iOS为一体
</p>
<p>
服务器端找了台CentOS 7的VPS，安装node环境
(由于一连串的连锁关系，新的 node 需要 gcc 4.8 以下来编译，而 gcc 4.8 在 CentOS 6 上无法 yum 更新，需手动编译)
sudo yum install gcc gcc-c++
下载最新的 node 版本
wget http://nodejs.org/dist/node-latest.tar.gz
tar zxvf node-latest.tar.gz
cd node-vXXX
./configure
make
make install
node --version

npm install -g react-native-cli 全局安装 react-native

react-native init 项目名 (由于是服务器端，考虑删除 ios 和 android 文件夹)
react-native start --port XXX 让它跑在某个端口上

PS:
第二种方法
安装 nvm (node version manager)  github(https://github.com/creationix/nvm)
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh | bash
source ~/.bash_profile
列出需要的版本
nvm list-remote
nvm install vXXX 安装相应的版本
</p>
<p>
客户端由于 facebook 的不更新 pod 。只能使用 npm 来安装本地 react-native 并在 Podfile 中指向 react-native 目录 (facebook虽然不更新 pod，但项目中的 podspec 还是更新的)
</p>

#### 注意 ####
<p>作为远程访问
AppRegistry.registerComponent('ModuleName', () => ProjectName);
ModuleName 和 ProjectName 尽量不要使用相同

搭建一台 nginx 作为反向代理，用于过滤一些不必要的恶意请求，例如 index.ios.js  index.ios.map 及 每次编译生成的 md5文件名的源文件</p>


Reference: 
http://www.hotobear.com/?p=1015 (React Native 初探（iOS）)
http://blog.cnbang.net/tech/2698/?utm_source=tuicool (React Native通信机制详解)



