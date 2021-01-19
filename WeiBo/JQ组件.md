<!--
 * @Author: your name
 * @Date: 2021-01-19 12:00:58
 * @LastEditTime: 2021-01-19 12:05:34
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\WeiBo\JQ组件.md
-->

#### scrollerFocus

``` html
  <div class="focus-wrap">
    <button type="button" class="btn btn-flat-person px-3 pb-1 person-btn scroller-opt-btn" onclick="scrollerFocusFunction(this)"><i class="fa fa-sort-desc" aria-hidden="true"></i></button>
    <div class="focus-recommend">
    </div>
 </div>

```

```js
    //渲染他人的ScrollerFocus数据列表
    function renderScrollerFocus(e) {
        let _this = $(e);
        let htmlWrap = ``;
        $.ajaxSettings.async = false;
        //ajax
        $.getJSON("/Recommend/GetInterestedByCert", `{userId:${userId}}`, function (data) {
            if (data.status == 1) {
                htmlWrap += `
                    <!--recommendFocus statt 推荐关注-->
                    <div class="focus-title">
                        <span class="S-fb14">关注推荐</span>
                    </div>
                    <div class="focus-scroll">
                        <ul class="focusitems-ul clearfix" style="width: 3300px;left:0px">`
                let result = JSON.parse(data.result);
                //替换备注名
                for (var i = 0; i < result.length; i++) {
                    htmlWrap += `
                            <li class="focusitems S-bg1">
                                <div class="inner-wrap">
                                    <!--头像-->
                                    <p class="pic-wrap">
                                        <span class="pic-box">
                                        <a href="javascript:void(0)" target="_blank">
                                            <img src="${result[i].headImg}" alt="${result[i].accountName}" title="${result[i].accountName}" class="pic" >
                                        </a>
                                        <a href="javascript:void(0)" target="_blank" class="icon">
                                          <i class="icon-officialcert-gold" aria-hidden="true" title="${window.yjccommon.renderCert(result[i].officialCert)}"></i>
                                        </a>
                                        </span>
                                    </p>
                                    <!--名称-->
                                    <p class="S-fb14 W-fb700 name-wrap W-autohide">
                                        <a href="javascript:void(0)" target="_blank">${result[i].accountName}</a>
                                    </p>
                                    <!--官方认证 或者 个人信息-->
                                    <p class="info-wrap S-fb12">
                                        <a href="_blank" href="javascript:void(0)">${window.yjccommon.renderCert(result[i].officialCert)}</a>
                                    </p>
                                    <!--操作按钮：关注等-->
                                    <p class="option-wrap">
                                        <a href="javascript:void(0)" class="btn btn-flat-light  add-newgroup" style="width: 104px;"><em class="W-em W-em-add">+</em>关注</a>
                                    </p>
                                    <!--× 删除-->
                                    <a href="javascript:void(0)" class="close-wrap">
                                        <span class="S-fb20">×</span>
                                    </a>
                                </div>
                            </li>`
                }
                htmlWrap += `</ul>
                        <a href="javascript:void(0)" class="W-icon scroll-control left">
                            <i class="W-icon W-icon-scroll-arrleft"></i>
                        </a>
                        <a href="javascript:void(0)" class="W-icon scroll-control right">
                            <i class="W-icon W-icon-scroll-arrright"></i>
                        </a>
                    </div>
                    <!--recommendFocus end-->`
                //console.log(htmlWrap)
                console.log($(document).closest('.focus-wrap').find(".focus-recommend"))
                _this.closest('.focus-wrap').find(".focus-recommend").html(htmlWrap);
            }
        })
    }
    //初始化加载隐藏或者显示【推荐关注】的按钮事件
    function scrollerFocusFunction(e) {
        let _this = $(e);
        renderScrollerFocus(_this);
        $(document).find('.focus-recommend').animate({ height: 'toggle' }, 'slow', function () {
            let curVisi = $(document).find('.focus-recommend').css("display");
            if (curVisi == "block") {
                //$(document).find('.focus-recommend').animate({opacity:'1'})
                console.log("显示状态")
                $(document).find('.scroller-opt-btn').html(`<i class="fa fa-sort-asc" aria-hidden="true"></i>`)
                //他的主页和他的相册背景颜色变更
                //$(document).find('.WB-slide').css("background-color","white");
            }
            else {
                console.log("隐藏状态")
                $(document).find('.scroller-opt-btn').html(`<i class="fa fa-sort-desc" aria-hidden="true"></i>`)
                //$(document).find('.WB-slide').css("background-color","#f8f9fa");
            }
        })
    }
    //计算 scrollerView 左右点击次数
    let scrollCount = 0;
    //scrollerView 向右点击
    $(document).on('click', '.focus-scroll .right', function (event) {
        event.stopPropagation();
        scrollWith = $(document).find('.focus-scroll').width();   //content宽度
        let curFocusitemsul = $(document).find('.focusitems-ul');  //ul对象
        let curFocusitemsli = $(document).find('.focusitems-ul>li').width(); //li的宽度
        //console.log("curFocusitemsli:" + curFocusitemsli)
        let focusitemsulWidth = curFocusitemsul.width();           //数据宽度
        //console.log("scrollWith:"+scrollWith)
        let curLeft = curFocusitemsul.css('left').replace('px', "");//当前数据往左移动的距离
        //当前往左移动的px值
        //console.log("curLeft:"+curLeft)
        let letRemove = curLeft - scrollWith;
        //console.log("curLeft-scrollWith:"+letRemove);
        if (Math.abs(letRemove) <= focusitemsulWidth) {
            let curNumber = Math.floor(scrollWith / curFocusitemsli);            //在视图中的完整的focusitem的个数
            let curRemove = -(curFocusitemsli + 10) * curNumber * (scrollCount + 1);   //在视图中的完整的focusitem的个数长度 10 是左右两边的 margin值
            let curLeft = curRemove + "px"
            //console.log("移动后的:curLeft" + curLeft)
            //设置css left 属性值
            curFocusitemsul.css("left", `${curLeft}`);
            scrollCount++;
        }
        else {
            console.log("没有数据了")
        }
    })
    //scrollerView 向左点击
    $(document).on('click', '.focus-scroll .left', function (event) {
        event.stopPropagation();
        scrollWith = $(document).find('.focus-scroll').width();   //content宽度
        let curFocusitemsul = $(document).find('.focusitems-ul'); //ul对象
        let curFocusitemsli = $(document).find('.focusitems-ul>li').width(); //li的宽度
        //console.log("curFocusitemsli:" + curFocusitemsli)
        let focusitemsulWidth = curFocusitemsul.width();           //数据宽度
        //当前的left
        let curLeft = curFocusitemsul.css('left').replace('px', "");//当前数据往左移动的距离
        //在视图中的完整的focusitem的个数
        let curNumber = Math.floor(scrollWith / curFocusitemsli);
        //获取当前的scrollright的点击次数(为正)
        //至少往右滑动了一次
        if (scrollCount > 0) {
            //console.log('点击左按钮')
            let curRemove = parseInt((curFocusitemsli + 10) * curNumber) + parseInt(curLeft);
            //console.log("移动后的:curRemove" + curRemove)
            curLeft = curRemove + "px";
            //console.log("移动后的:curLeft" + curLeft)
            //设置css left 属性值
            curFocusitemsul.css("left", `${curLeft}`);
            scrollCount--;
        }

    })
    //删除scrollerFocus中选中的li
    $(document).on('click', '.focus-scroll li .close-wrap', function (event) {
        event.stopPropagation();
        let _this = $(event.target);
        //获取当前所在的li
        let curLi = _this.closest('li');
        //animate() 效果结束后删除元素
        curLi.animate({ width: '0px' }, function () { curLi.remove() });
        //重新设置设置ul的宽度
        //获取ul下li的个数
        let liCount = $(document).find('.focusitems-ul').children().length;
        //li的宽度
        let curFocusitemsli = $(document).find('.focusitems-ul>li').width();
        //设置focusitems-ul的width
        $(document).find('.focusitems-ul').css("width", liCount * (curFocusitemsli + 10));
    });
    //scrollerView 推荐关注 End

```