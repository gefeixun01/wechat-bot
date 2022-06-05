# wechat-bot
可以获取小程序code加好友等等
## 请求地址
http://127.0.0.1:8805
## 获取小程序code

+ type：		get_code	  →  固定值
+ wxid：	需要操作为微信
+ appid：	小程序appid，传入空值则表示获取最后打开的小程序的code

{
'type':'get_code',
'wxid':'wxid_ogddw0322',
'appid':'xxxxxxxx',
}
## 通过群id获取群成员wxid
+ type：	get_wxid_from_chatroom	  →  固定值
+ wxid：    需要操作的微信id
+ chatroomid：	 群id

{
'type':'get_wxid_from_chatroom',
'wxid':'wxid_m4xxzn7sxzm22',
'chatroomid':'25607067974@chatroom',
}
## 通过wxid添加好友
+ type：	add_friend_wxid	固定值
+ wxid	：	需要操作的微信id
+ add_wxid	：	需要添加的人的微信id
+ hello	：打招呼的内容

{
    "type": "add_friend_wxid",
    "wxid": "wxid_m4xxzn7sxzm22",
    "add_wxid": "hytpnpn",
    "hello": "你好，个非寻",
}
## 通过V3数据添加好友
+ type：	add_friend_v3	固定值
+ wxid：		需要操作的微信id
+ v3：		可通过‘网络查找陌生人信息’接口获取
+ add_type：	1	添加的类型：1=qq 3=微信号  10和13=通讯录  14=群聊  15=手机号  17=名片  30=扫一扫 6=单向添加
+ hello	：	打招呼的内容

{
    "type": "add_friend_wxid",
    "wxid": "wxid_m4xxzn7sxzm22",
    "add_wxid": "hytpnpn",
    "hello": "你好，个非寻",
}
## 网络查找陌生人信息
+ type：	add_friend_v3	固定值
+ wxid：		需要操作的微信id
+ phone_qq		查找的电话号码或者QQ号码

{
    "type": "search_stranger",
    "wxid": "wxid_m4xxzn7sxzm22",
    "phone_qq": "3122142139",
}
## 启动微信
+ type：	start_wx	  →  固定值

{
'type':'start_wx',
}
## 打开内置浏览器
+ type：	open_url	  →  固定值
+ wxid：    需要操作的微信id
+ url：	 url地址

{
'type':'open_url',
'wxid':'wxid_m4xxzn7sxzm22',
'url':'www.baidu.co'
}
## 获取登陆微信列表
+ type：	get_robot	  →  固定值

{
'type':'get_robot',
}
## 发文本消息
+ type：	open_url	固定值
+ wxid：		需要操作的微信id
+ to_wxid：		对方的微信id
+ msg		消息内容

{
'type':'open_url',
'wxid':'wxid_m4xxzn7sxzm22',
'url':'www.baidu.co'
}
## 在群里发@文本消息
+ type：	send_at_msg	固定值
+ wxid：		需要操作的微信id
+ to_wxid：		对方的微信id
+ msg：		消息内容
+ chatroomid	：	微信群id
+ nickname：		@的人的备注名或者昵称

{
    "type": "send_at_msg",
    "wxid": "wxid_m4xxzn7sxzm22",
    "to_wxid": "hytpnpn",
    "msg": "个非寻666",
    "chatroomid": "chatroomid132123",
    "nickname": "个非寻",
}
## 发图片消息
+ type：	send_image	固定值
+ wxid	：	需要操作的微信id
+ to_wxid	：	对方的微信id
+ path	：	图片的绝对路径

{
    "type": "send_image",
    "wxid": "wxid_m4xxzn7sxzm22",
    "to_wxid": "hytpnpn",
    "path": "C:\Users\Admin\aaa.png",
}
## 发文件消息
+ type：	send_file	固定值
+ wxid	：	需要操作的微信id
+ to_wxid	：	对方的微信id
+ path	：	文件的绝对路径

{
    "type": "send_file",
    "wxid": "wxid_m4xxzn7sxzm22",
    "to_wxid": "hytpnpn",
    "path": "C:\Users\Admin\aaa.png",
}
## 确认收款
+ type：	send_file	固定值
+ wxid	：	需要操作的微信id
+ from_wxid		给你转账的微信id
+ transferid		从收款的消息中获取

{
    "type": "collection",
    "wxid": "wxid_m4xxzn7sxzm22",
    "from_wxid": "hytpnpn",
    "transferid": "1206540006500654454658",
}
## 消息回调
+ 地址：http://127.0.0.1:8880
+ msgtype：	friend→私聊和公众号消息；groud→群聊消息；revoke→对方实时撤回的消息
+ robot：	接收到消息的微信id
+ friendwxid：	发送消息的微信号
+ content：	消息的原始内容
+ path：	文件或者图片下载后的路径（设置自动下载图片，否则接收不到图片）
+ chatroomid：	微信群id，当消息为群消息时有该字段
+ senderid：	消息为群消息时，发送该消息的微信id
+ type：	消息类型，该值为整数型，1："文本消息类型"， 3： "图片消息"，34："语音消息"， 43："小视频消息"，62："短视频消息"，47："表情消息"，49："多媒体消息"，37："好友请求"，42："分享名片"，10000, "系统消息"，10002, "撤回消息"
+ self：	是否为自己发送的消息，否：0，是：1

### 私聊消息
{"msgtype":"friend",
 "robot":"huangpan181",
 "friendwxid":"wxid_m4xxzn70sxzm22",
 "content":"111",
 "path":"",
 "type":"1",
 "self":"1"
}
### 群聊消息
{
  "msgtype": "groud",
  "robot": "huangpan181",
  "chatroomid": "23987715429@chatroom",
  "senderid": "wxid_m4xxzn70sxzm22",
  "content": "个非寻",
  "path": ""
  "type":"1",
  "self":"1"
}
### 实时撤回的消息
{'msgtypr': 'revoke', 
 'robot': 'huangpan181', 
 'wxid': 'wxid_m4xxzn70sxzm22', 
 'content': '个非寻'
}
