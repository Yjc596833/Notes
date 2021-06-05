
ajax() 回调既不进入success,也不进入error的解决：
ajax的异步传输还未完成验证，页面已进行刷新。由于页面用的是layui框架（基于bootstrap）.bootstrap框架下form表单中的按钮被点击后悔自动刷新页面。解决方法：将form改为div即可，页面样式不会发生变化

校验用户权限：

JWT.InstialAjaxValidate();
let accessToken = JWT.GetAccessToken();

beforeSend: function (xhr) {
    xhr.setRequestHeader("Content-Type", "application/json; charset=utf-8");
    xhr.setRequestHeader("Authorization", "Bearer " + accessToken);
},

 error: function (xhr) {
                if (xhr.status == 401) {
                    let errorMsg = xhr.statusText;
                    console.info("errorMsg:", errorMsg);
                    if (errorMsg == "Unauthorized" && JWT.GetAjaxFlag()) {
                        if (JWT.GetAjaxCount() > 1) {
                            console.log("多次校验用户Token未授权,返回登录界面");
                            window.location.href = `${config.BaseAddress}/Login/Index`;
                        }
                        console.log("未授权，用户重新请求个人信息模块");
                        JWT.IncrAjaxCount();
                        JWT.SetAjaxFalse()
                        //表示过期，需要自动刷新
                        JWT.GetTokenAgain(UserBlogInfo);
                        JWT.SetAjaxTrue();
                        return;
                    } else {
                        //表示是非法请求，给出提示，可以直接退回登录界面
                        console.info("GetMsg:", "非法请求");
                        window.location.href = `${config.BaseAddress}/Login/Index`;
                    }
                }
                console.info("GetMsg失败状态", xhr.status);
                window.location.href = `${config.BaseAddress}/Login/Index`;
            }
${config.DocumentAddress}

${config.ServerBaseAddress}

`${config.ServerBaseAddress}/api/
            
`${config.BaseAddress}/


data:JSON.stringify(commentForwardOptions),
    beforeSend: function (xhr) {
            xhr.setRequestHeader("Content-Type", "application/json; charset=utf-8");
     },