<!--
 * @Author: your name
 * @Date: 2021-03-05 17:29:03
 * @LastEditTime: 2021-03-05 17:58:10
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\WeiBo\toolsjs.md
-->

``` javascript
icon图标弹窗
MsgLayer("msgicon",{"icon":3,msg:"******"})

Guid
GUID(12,16)

表情regex
(new ContentRegex("emoji",{"content":commentMsg})).result


关注
new AJAXFollow("focus","focussuccess",_this, {
    type: 'post',
    url: '/Recommend/FollowInterested',
    param: {
        userId: 1,
        focusUserId: 2
    }
})
```