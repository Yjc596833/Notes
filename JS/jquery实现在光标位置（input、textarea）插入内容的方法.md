<!--
 * @Author: your name
 * @Date: 2021-03-19 14:25:32
 * @LastEditTime: 2021-03-19 14:25:58
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\JS\jquery实现在光标位置（input、textarea）插入内容的方法.md
-->
HTML代码：

<input id="phone"/>
<button type="button" onclick="insertContent()">插入</button>
JS代码：

function insertContent() {
        $("#phone").insertAtCaret("要插入的内容");
    }

(function($){
        $.fn.extend({
            insertAtCaret: function(myValue){
                var $t=$(this)[0];
                if (document.selection) {
                    this.focus();
                    sel = document.selection.createRange();
                    sel.text = myValue;
                    this.focus();
                }
                else
                if ($t.selectionStart || $t.selectionStart == '0') {
                    var startPos = $t.selectionStart;
                    var endPos = $t.selectionEnd;
                    var scrollTop = $t.scrollTop;
                    $t.value = $t.value.substring(0, startPos) + myValue + $t.value.substring(endPos, $t.value.length);
                    this.focus();
                    $t.selectionStart = startPos + myValue.length;
                    $t.selectionEnd = startPos + myValue.length;
                    $t.scrollTop = scrollTop;
                }
                else {
                    this.value += myValue;
                    this.focus();
                }
            }
        })
    })(jQuery);
 

上面的方法并不适用于在textarea文本框中插入数据，如下方法可以解决这个问题：

JS代码：

$('#textarea').on('select',function () {
    message.setCaret(this);
}).on('click',function () {
    message.setCaret(this);
}).on('keyup',function () {
    message.setCaret(this);
});

$('#insert').on('click',function () {
    var textareaStr = $('#textarea').val();
    message.insertAtCaret($('#textarea')[0],$("#nick").val());
});

var message = {
    setCaret: function (textObj) {
        if (textObj.createTextRange) {
            textObj.caretPos = document.selection.createRange().duplicate();
        }
    },

    insertAtCaret: function (textObj, textFeildValue) {
        if (document.all) {
            if (textObj.createTextRange && textObj.caretPos) {
                var caretPos = textObj.caretPos;
                caretPos.text = caretPos.text.charAt(caretPos.text.length - 1) == ' ' ? textFeildValue + ' ' : textFeildValue;
            } else {
                textObj.value = textFeildValue;
            }
        } else {
            if (textObj.setSelectionRange) {
                var rangeStart = textObj.selectionStart;
                var rangeEnd = textObj.selectionEnd;
                var tempStr1 = textObj.value.substring(0, rangeStart);
                var tempStr2 = textObj.value.substring(rangeEnd);
                textObj.value = tempStr1 + textFeildValue + tempStr2;
            } else {
                alert("This version of Mozilla based browser does not support setSelectionRange");
            }
        }
    }
}
 

上面的方法对于input输入框同样适用。