# 新余学院图书馆占座系统

> 本项目供学习交流使用，使用本项目造成的一切后果自行承担
> 
> 本项目在该原项目基础上添加了自动签到功能预约座位后，三秒后自动签到，避免被系统认为恶意占座
> 
> 原项目
[河北科技师范学院图书馆占座系统](http://www.cnblogs.com/sxdcgaq8080/p/7894828.html)
>
> 请注意，项目搭配的抓包软件可能有问题，请自行解决抓包问题
> 
> 需要抓取的字段为：sid,openid,cookie,token
>
> 将抓取到的字段放到txt文件中，添加项目的源路径，如sid.txt,openid.txt这样
> 

#### 补充
- **若实在不会使用本项目，这里提供一个手动远程签到的方法，
- **1,正常预约座位后，在微信的座位浏览界面，复制当前连接，将链接后面的token字段提取出（不包括token=本身），若存在"["与"]"中括号，请将"["改成"%5B","]"改成"%5D"
- **2,将上述修改后的字段拼接到"http://xyc.q2q365.com/qckj/seat/seat_signinall?str=http://xyc.q2q365.com/qckj/seat/seat_signinall?str="之后，合成一个链接
- **3,将该链接微信发送给自己或者任何人，点击访问该链接，即可完成签到
- **若提示二维码已过期，重复一次上述操作即可

  
#### 以下皆为原作者的话

#### 使用前先安装依赖
```bash
pip install -r requirements.txt
```

#### 使用说明：
- **1，首先运行Fidder.exe文件，右键该文件，选择以管理员方式打开。（打开后若弹出windows防火墙，请点击允许）**
- **2，打开后，在保持该软件运行的前提下，打开电脑端微信，进入高校鸿芒公众号->座位空间管理。即正常的占座流程，进入首页。**
- **3，进入首页后，回到Fidder.exe软件，可看到sid success!  openid success!   cookie success!等字样。此时即可关闭该软件。（若没有看到success字样，请关闭公众号并重新进入一下座位空间管理。）**
- **4，打开运行lib.py。会弹出GUI页面。输入座位号和房间号即可进行抢座。**

#### 功能说明：
- **1，输入座位号和房间号后，点击右侧的保存信息即可将输入的信息保存下来，下次打开软件时自动按照保存的信息抢座。**
- **2，lib软件打开后会自动运行一次抢座功能，若此时没有保存的信息，会自动中断程序，等待用户交互。**
- **3，运行程序即为：抢座功能。点击运行程序也会运行抢座功能。**
- **4，取消预约会取消当前已经预约但未签到的座位**
- **5，重复占座可以理解为：点击一次取消预约，点击一次运行程序。也就是说，重复占座会将当前已经占座的信息退掉，然后重新按照用户输入的座位号进行占座。**
- **6，在运行 本程序时若是非预约时间，则会进入等待状态，等到06:00:00分时，以每0.5秒抢座一次的速度进行抢座，直到抢座成功为止。**

#### 注意：
- **每次操作的有效期为1小时，即：每过一小时，都要按照使用步骤操作一遍。**
- **由于小程序cookie的有效期只有1小时，所以就导致了该程序存在较大的局限性：必须得5点多起床操作一次，更新cookie才可以保证程序正常运行。**
- **本作者能力有限，上述的局限性无法完善，该项目仅作交流学习使用！**

> #### 作者有话说
> - 1，该项目为半成品项目，因为小程序登录需要过微信Oauth2登录验证，本作者能力有限无法使用python实现，所以用易语言打包了一份抓包软件。以便可以抓取到cookie和微信id。
> - 2，若易语言软件无法使用，请自行解决抓包问题，只需将cookie和微信两个id放入相应txt文件中依旧可用。欢迎各位大佬提交Pr。
> - 3，本作者已从科师毕业，所有项目均不再维护，不保证程序可以一直使用。
