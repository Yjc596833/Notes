<!--
 * @Author: your name
 * @Date: 2021-03-02 12:07:06
 * @LastEditTime: 2021-03-03 15:39:22
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\WeiBo\yjcomment.md
-->


```  html
######提交评论按钮：
$(document).on('click', '.btn-publishComment', function (event)

######controller:
/BlogComment/AddBlogComment
```
```  html
######图片显示Regex正则表达式处理：
window.yjccommon.imgRegex

######controller:
/Emoji/GetRegexEmoji
```

```  html
######评论加载：
window.yjccommon.renderCommentSortlist

######controller:
 /BlogComment/GetBlogComments
```

```  html
######回复：
$(document).on('click', '.btn-modal-commentReply', function (event) 

######controller:
/BlogComment/AddBlogComment
```


```  html
######删除：
$(document).on('click','.comment-replyDel',function(event)

######controller:
/BlogComment/DelBlogComment
```

####### 常用弹窗
``` html
window.yjccommon.operationWPVView({ icon: "success", msg: "删除回复成功" });
window.yjccommon.operationWPVView({ icon: "error", msg: "操作失败，请稍后重试" });

```

```  html
######评论点赞：
 $(document).on('click', '.comment-like', function (event

######controller:
/BlogComment/CommentLikesOperations