# ajax-jsonp
这是一个实现跨越的请求
$(function() {
    $("#submit").click(function() {
        var data = {
            name: $("#name").val(),
            id: $("#id").val()
        };
        $.ajax({
            type: 'POST',
            data: data,
            url: 'http://localhost:3000/ajax/deal',
            dataType: 'json',
            cache: false,
            timeout: 5000,
            success: function(data) {
                console.log(data)
            },
            error: function(jqXHR, textStatus, errorThrown) {
                console.log('error ' + textStatus + ' ' + errorThrown);
            }
        });
    });
});
23:30:23
lightweight boy 2017/6/1 星期四 23:30:23
function jsonpCallback(data) {
    console.log("jsonpCallback: " + data.name)
}
$("#submit").click(function() {
    var data = {
        name: $("#name").val(),
        id: $("#id").val()
    };
    $.ajax({
        url: 'http://localhost:3001/ajax/deal',
        data: data,
        dataType: 'jsonp',
        cache: false,
        timeout: 5000,
        // jsonp 字段含义为服务器通过什么字段获取回调函数的名称
        jsonp: 'callback',
        // 声明本地回调函数的名称，jquery 默认随机生成一个函数名称
        jsonpCallback: 'jsonpCallback',
        success: function(data) {
            console.log("ajax success callback: " + data.name)
        },
        error: function(jqXHR, textStatus, errorThrown) {
            console.log(textStatus + ' ' + errorThrown);
        }
    });
});
23:42:29
lightweight boy 2017/6/1 星期四 23:42:29
$(function() {
    $("#submit").click(function() {
        var data = {
            name: $("#name").val(),
            id: $("#id").val()
        };
        $.ajax({
            type: 'POST',
            data: data,
            url: 'http://localhost:3001/cors',
            dataType: 'json',
            cache: false,
            timeout: 5000,
            success: function(data) {
                console.log(data)
            },
            error: function(jqXHR, textStatus, errorThrown) {
                console.log('error ' + textStatus + ' ' + errorThrown);
            }
        });
    });
});
