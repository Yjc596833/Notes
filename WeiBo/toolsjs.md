<!--
 * @Author: your name
 * @Date: 2021-03-05 17:29:03
 * @LastEditTime: 2021-04-08 18:53:22
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\WeiBo\toolsjs.md
-->

new NumTransform("transform", { value: `${options.likes}` }).number

``` javascript
icon图标弹窗
MsgLayer("msgicon",{"icon":3,msg:"******"})

Guid
GUID(12,16)

表情regex
(new ContentRegex("emoji",{"content":commentMsg})).content

(new ContentRegex("emojireverse",{"content":commentMsg})).content

通用ajax请求方式
new ClickConfirmModal(
    {
        funcitonType: "ajax",
        callBackFunctionType: "callBackRefreshFavoriteTag",
        target: _this,
        opts: {
            async: false,
            type: "post",
            url: "/BlogFavorite/UpdateFavoriteBlog",
            param
        },
    });

//删除a标签，并保留内容
forwardBody = forwardBody.replace(/(<\/?a.*?>)/g, '').trim();


获取转发的message
(new AJAXForwardContent("forwardmessage", { "forwardcommentguid": artBody.attr("data-guid") })).content

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


    /* 用户点赞或取消赞 */
    $(document).on('click', '.ajax-likes', function (event) {
        event = event || window.event;
        event.stopPropagation();
        let _this = $(event.target).closest('a');
        let blogId = $(_this).closest('tbody').find('.blog-ajax-comment').attr("data-blog-id");
        if (_this.hasClass('blog-like')) {
            new AJAXLikes("sublike", "renderlike", _this, {
                type: 'post',
                url: '/BlogComment/UpdateBlogLikes',
                param: {
                    likeType: 1,
                    blogId: blogId,
                    userId: adminID
                }
            })
        }
        else {
            new AJAXLikes("addlike", "renderlike", _this, {
                type: 'post',
                url: '/BlogComment/UpdateBlogLikes',
                param: {
                    likeType: 0,
                    blogId: blogId,
                    userId: adminID
                }
            })
        }
    })


 window.common.ReviewConfirmModal({ Content: "Ta发布的微博在信息流将置顶显示。" })

 
/* 渲染数据 */
    new RenderView(
    {
        funcitonType: "ajax",
        callBackFunctionType: "callBackRenderUsergroups",
        target: _this,
        opts: {
            async: true,
            type: "get",
            url: "/Recommend/GetUserGroup",
            param: {
                PageIndex:1,
                userId: adminID
            }
        },
    });
```