Wechat-sdk-php
==============
呵呵，大家好。这个微信php类库来自于网络上多人智慧的结晶，特别是被动响应部分基本上都是来自于：dodgepudding。在此向那些牛人们致敬。 说明一下，我是个菜鸟，所以在代码上特别的凌乱，希望有热心人士指点。

使用方法
--------
require("./Wechat.class.php");
    $options = array(
            'etoken'=>'ddfdfasd',  //微信公共平台设置的接口token
            'account'=>'ligboy@gmail.com', //微信公共平台账号，您不需要主动发送消息不需要设置
            'password'=>'********',  //微信公共平台账号密码，您不需要主动发送消息不需要设置
    );
    $wechatObj = new Wechat($options);  //创建Wechat的实例并初始化参数
    $wechatObj->setCookiefilepath("./app/Runtime/");  //设置cookie文件保存目录
    $wechatObj->setWebtokenStoragefile("./app/Runtime/webtoken.txt");  //设置webtoken的保存路径（包括文件名），您不需要主动发送消息不需要设置

    //被动响应实例

    $wechatObj->valid(); //验证请求来源是否合法，在通过平台验证后可以去掉，但是不安全啊。
    $msgtype = $weObj->getRev()->getRevType();
    switch(msg$type) {
        case Wechat::MSGTYPE_TEXT:
                $wechatObj->text("你好我是微信小机器人")->reply();
                exit;
                break;
        case Wechat::MSGTYPE_EVENT:
                $revEvent = array();
                $revEvent = $this->wechatObj->getRevEvent();
                switch ($revEvent['event']) {
                    //关注订阅事件
                    case "subscribe":
                        $wechatObj->text("你好我是微信小机器人")->reply();
                        break;
                    //取消关注订阅事件
                    case "unsubscribe":
                        //做一些删除用户记录之类的事情
                        break;
                }
                break;
        case Wechat::MSGTYPE_IMAGE:
                break;
        case Wechat::MSGTYPE_VOICE:
                break;
        case Wechat::MSGTYPE_MUSIC:
                break;
        case Wechat::MSGTYPE_LOCATION:
                break;
        case Wechat::MSGTYPE_LINK:
                break;
        default:
                $wechatObj->text($wechatObj->wechatObj)->reply();
    }



    //主动发送消息示例

    //群发消息
    $fakeids = array("823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881","823058881");
    //接收返回结果数组
    $batresult = $wechatObj->batSend($fakeids,"这是一种问候啊！\n下个10分钟再见。");

    //单条消息发送
    $singleresult = $wechatObj->send("823058881", "这是一种问候啊！");
