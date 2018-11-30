## iOS系统短信过滤规则?
###### 当满足以下任意条件时,iOS 系统不会将收到的短信交由短信过滤器处理
* 发件人在你的通讯录中
* 您曾经给该号码发送过至少3条短信
* 信息是iMessage信息

## 为什么正常短信也会被过过滤?
###### iOS系统的短信过滤机制是基于 (号码会话) 进行过滤, 所以每个会话只要出现过一条垃圾短信,那么这个号码就会被标记,之后的短信都会被过滤

## 一个号码被过滤后如何取消?
###### 选择以下任意一种方案
* 将号码添加到通讯录
* 随便回复3条信息
* 删除会话

## 为何屏蔽后短信应用角标依然存在?
###### iOS系统就是这么设计的, 目前无法修改这个系统行为

## 自定义规则验证说明
###### 目前规则验证支持 (前缀, 后缀, 包含, 正则) 以下 (xxx) 为规则中的匹配规则
* 前缀: 号码或者短信内容 以xxx开头 将会验证成功
* 后缀: 号码或者短信内容 以xxx结尾 将会验证成功
* 包含: 号码或者短信内容 包含xxx 将会验证成功
* 正则: 号码或者短信内容 根据正则表达式验证

## 示例:

```json
{
    // 是否启用号码白名单
    "enableNumberWhite" : true,
    // 是否启用号码黑名单
    "enableNumberBlack" : true,
    // 是否启用关键词白名单
    "enablekeywordsWhite" : false,
    // 是否启用关键词黑名单
    "enablekeywordsBlack" : true,
    "numberWhiteList" : [
        {
          // 具体匹配内容
          "value" : "^\\d{5}$",
          // 规则别名
          "alias" : "不过滤五位数号码",
          // 是否启用这条规则
          "enable" : true,
          "type" : "numberWhiteList",
          // 验证方式 prefix suffix contain regular
          "validation" : "regular"
        }
    ],
    "numberBlackList" : [
        {
          "value" : "18943705413",
          "alias" : "六合彩",
          "enable" : true,
          "type" : "numberBlackList",
          "validation" : "contain"
        }
    ],
    "keywordsWhiteList" : [
        {
          "value" : "验证码",
          "alias" : "验证码",
          "enable" : true,
          "type" : "keywordsWhiteList",
          "validation" : "contain"
        }
    ],
    "keywordsBlackList" : [
        {
          "value" : "3码",
          "alias" : "六合彩",
          "enable" : true,
          "type" : "keywordsBlackList",
          "validation" : "contain"
        },
        {
          "value" : "^【饿了么】.*元大红包",
          "alias" : "饿了么大红包",
          "enable" : true,
          "type" : "keywordsBlackList",
          "validation" : "regular"
        },
    ]
}
```

## 关于自定义规则执行顺序
###### 执行顺序如下, 其中任意一个满足,则不再执行后续规则
* 号码白名单
* 号码黑名单
* 关键词白名单
* 关键词黑名单

## 关于提交样本数据?
###### 收集样本数据,是否为了后续进行机器学习,作为模型训练数据,为后续加入机器学习过滤做准备,
###### 当然这是由您选择是否愿意提交,本应用不会在您不知情的情况下记录你的短信
###### 如何提交,首先请您将你要提交的内容先拷贝一下,然后进入本应用,点击提交样本,本应用会自动从您iPhone的粘贴板中读取

## 关于隐私?
###### APP不会记录您的任何信息,除非您主动提交了样本数据.

## 关于国行手机?
###### 国行手机系统加入了网络数据使用权限,但目前这个权限系统没有提供主动获取的方法,
###### 所以首次安装后,进行 (上传iCloud, 从iCloud同步, 从网络地址导入, 提交样本数据) 时会提示失败,
###### 此时系统会有网络数据使用的权限弹框,请您同意本软件使用网络数据的权限


