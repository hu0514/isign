1 下载代码
git clone https://github.com/apperian/isign
2 进入isign目录执行安装命令
sh version.sh
python setup.py build
python setup.py install
3 从开发者账号下载.p12证书及.mobileprovision配置文件
4 提取p12文件为pem格式
isign_export_creds.sh *.p12
生成的文件默认存放在 /root/.isign/目录
5 将下载的配置文件 改名为isign.mobileprovision 并放在/root/.isign/目录
6执行重签名命令
isign -o out.ipa my.ipa

isign 命令也可以指定各参数位置 具体请参照官网
官网：https://github.com/apperian/isign

