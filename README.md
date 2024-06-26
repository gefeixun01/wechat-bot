# 微信机器人

+ 详情请联系QQ：3122142139
+ 文档交流学习使用。

* 关于python实现各种功能可以参考：
* [纯python实现获取sessionid（无需注入）](https://blog.csdn.net/gefeixun/article/details/136895388?spm=1001.2014.3001.5502)
* [纯python实现获取code（无需注入）](https://blog.csdn.net/gefeixun/article/details/136972594?spm=1001.2014.3001.5502)
* [纯python实现小程序云函数抓包（附完整代码）](https://blog.csdn.net/gefeixun/article/details/137029885?spm=1001.2014.3001.5502)
* [纯python实现微信发文本消息（附完整代码，无需注入，非frida）](https://blog.csdn.net/gefeixun/article/details/137039169?spm=1001.2014.3001.5502)


## 调用示例
```python
{
class WeChatapi():
    def __init__(self):
        self.url = 'http://127.0.0.1:9001'

    def Wx_GotoLoginQrCode(self):
        api=f'{self.url}/Wx_GotoLoginQrCode'
        response = requests.get(api)
        response.encoding = 'gbk'
        qr=response.text
        print(qr)

    def StartWeChat(self):
        api = f'{self.url}/StartWeChat'
        response = requests.get(api)
        response.encoding = 'gbk'
        qr = response.text
        print(qr)

    def Wx_SendMsg(self):
        url = f'{self.url}/Wx_SendMsg'
        post_data = {"to_wxid":"wxid_563b189nwsu22","content":"测试"}
        response = requests.post(url, data=json.dumps(post_data,ensure_ascii=False).encode('GBK'))
        response.encoding='gbk'
        print(response.json())
        
if __name__ == '__main__':
    wechatapi = WeChatapi()
    wechatapi.StartWeChat()
}
