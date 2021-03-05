<!--
 * @Author: your name
 * @Date: 2021-01-19 12:00:58
 * @LastEditTime: 2021-03-04 13:11:08
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\WeiBo\JQ组件.md
-->

#### scrollerFocus关注滚动推荐

``` html
  <div class="focus-wrap">
    <button type="button" class="btn btn-flat-person px-3 pb-1 person-btn scroller-opt-btn" onclick="scrollerFocusFunctionPops(this)"><i class="fa fa-sort-desc" aria-hidden="true"></i></button>
    <div class="focus-recommend">
    </div>
 </div>

```

#### 消息提示弹窗

``` html
<div class="group-msg mt-2 margin-left-18 ">
    <span>
        <i class="fa fa-check-circle text-success S-fb17" aria-hidden="true"></i>
    </span>
    <span class="text-muted">
        成功添加组员到 ${curLength} 个分组
    </span>                                                                
</div>
```


##### emoji表情显示和输入框
``` html
<div class="emoji-wrap wpv-box-flex wpv-box-column">
<div class="wpv-box-flex" >
    <!--头像-->
    <a href="javascript:void(0)"> <img class="img-circle img-35" src="./images/user.png" alt="爱你一万年"></a> 
    <!--输入框-->
    <div class="wpv-box-item-flex con1 text">                              
        <textarea class="emoji-area enter-comment form-control" style="height: 38px;" placeholder="发表你的评论"></textarea>
    </div>
</div>
<div class="wpv-box-flex">
    <div class="margin-left-45 width-percent-100">
        <div class=" comment-expand  wpv-box-flex wpv-box-spaceBetween">
            <!--emoji-->
            <div class="emoji-normal">                                                       
                
            </div>
            <!--评论按钮-->   
            <div>                                 
                <a href="javascript:void(0)" class="btn btn-flat-light  btn-Comment"  onclick="window.yjccommon.commentSubmitBtn(this)">评论</a>       
            </div>                                                                   
        </div>                                                                  
    </div>
</div>         
</div>

```

#####  checkbox 样式
``` html
<label class="checkbox-main margin-left-20 padding-top-7">
    <input type="checkbox" class="S-fb12">
    <span class="S-fb12 S-icon margin-left-15 W-fb500">同时转发</span>
</label>

```


####  scroll-div 
```
    $(document).find('.scroll-modal-container').scroll(function(){
        /* scroll-modal-container */
        let scrollModalContainerHeight=$(document).find('.replyDetail-view .scroll-modal-container').height();//滚动视图高度
        scrollModalHeight=$(this)[0].scrollHeight;
        scrollModalTop=$(this)[0].scrollTop;
        if(scrollModalTop+scrollModalContainerHeight>=scrollModalHeight-40){
            console.log(replyOptions)
            renderReplySortlist(replyOptions);
        } //因为scroll-modal-container的上下内边距是
    })    
```


#### 遮盖层常用样式
```
    eg1:
    .wpv-picture-hover{
        filter: opacity(0);
        pointer-events: none;
        background-color: rgba(0, 0, 0, 0.15);
    }
```

#### JS返回当前时间
```
tools.js

/*返回当前时间：
 eg1: new TimeFormat("minute", curTime).currentTime；返回对应的时间格式样式：2021年3月4日 12:45
 eg2: new TimeFormat("second", curTime).currentTime；返回对应的时间格式样式：2021年3月4日 12:45:36
 */
 ```