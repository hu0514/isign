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

建立下载链接
1、ipa的下载地址放到plist的文件中，链接指定plist（plist格式见下文）

2、plist的链接要求一定是https的，而且必须是公网ssl，自签名及免费的https不可用。

3、链接格式要求一定是符合苹果规范的，itms-services://?action=download-manifest&url=https://****/***.plist

可使用github操作
具体方法：将plist上传到github上，查看plist内容页面上右上角点击“Raw”

使用该地址链接格式为https://raw.githubusercontent.com/用户名/项目名/master/xxxx.plist

拼接链接：itms-services://?action=download-manifest&url=https://raw.githubusercontent.com/用户名/项目名/master/xxxx.plist

在iphone手机中打开Safari，访问该链接，提示“在"iTunes"中打开链接吗？"，点击打开

提示“raw.githubusercontent.com”要安装“XXXXX”，点击安装即可在线下载安装ipa

.plist格式
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>assets</key>
			<array>
				<dict>
					<key>kind</key>
					<string>software-package</string>
					<key>url</key>
					<string>http://xxxxxxxxxxxxxxxxxxx/xxx.ipa</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>full-size-image</string>
					<key>needs-shine</key>
					<true/>
					<key>url</key>
					<string>http://xxxxxxxxxxxxxxxxxx.png</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>display-image</string>
					<key>needs-shine</key>
					<true/>
					<key>url</key>
					<string>http://xxxxxxxxxxxxxxxxxx.png</string>
				</dict>
			</array>
			<key>metadata</key>
			<dict>
				<key>bundle-identifier</key>
				<string>com.xxxx.demo</string>
				<key>bundle-version</key>
				<string>1.0.0</string>
				<key>kind</key>
				<string>software</string>
				<key>title</key>
				<string>XXXX App download</string>
			</dict>
		</dict>
	</array>
</dict>
</plist>