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

/* 加关注功能[独立的功能] */
$(document).on('click', '.ajax-focus', function (event) {
    event = event || window.event;
    event.stopPropagation();
    let _this = $(event.target);
    new AJAXFollow("focus", "focussuccess", _this, {
        type: 'post',
        url: '/Recommend/FollowInterested',
        param: {
            userId: adminID,
            focusUserId: _this.find('a').attr("data-userid")
        }
    })
})

/* 加关注功能[article右侧下拉中的关注选项] */
$(document).on('click', '.article-parent-focus', function (event) {
    event = event || window.event;
    event.stopPropagation();
    let _this = $(event.target);
    new AJAXFollow("focus", "focussuccessforarticle", _this, {
        type: 'post',
        url: '/Recommend/FollowInterested',
        param: {
            userId: adminID,
            focusUserId: _this.attr("data-key")
        }
    })
})

```