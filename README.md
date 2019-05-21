# 百度分享2.0支持HTTPS版本

## 介绍

由于百度分享不支持HTTPS协议，当网站开启HTTPS后便不能使用百度分享，所以目前的解决方式是将百度分享本地化。  

该代码于2019年5月12日使用chrome扩展程序"Save All Resources"下载，是目前最新版的百度分享2.0。  

## 修改内容

1. 修改`static\api\js\share.js`文件中的`staticUrl`为`https://cdn.hujinbo.me/libs/baidu-share`；
2. 修改`static\api\js\share.js`文件中的`nsClick`为`https://cdn.hujinbo.me/libs/baidu-share/static/api/img/share/v.gif`；
3. 注释`static\api\js\trans\logger.js`文件的所有内容，去除数据统计分析服务；
4. 注释`static\api\js\trans\trans_weixin.js`中的`r.length>200?p(r,function(e){h(e,!0)}):`，去掉微信URL短网址转换。

## 使用方式

将原有的`http://bdimg.share.baidu.com/static/api/js/share.js`改为`https://cdn.hujinbo.me/libs/baidu-share/static/api/js/share.js`

## 完整示例

将以下HTML代码添加至您的网站页面底部，即可使用HTTPS版本的百度分享功能：

```html
<div class="bdsharebuttonbox">
    <a href="#" class="bds_sqq" data-cmd="sqq" title="分享到QQ好友"></a>
    <a href="#" class="bds_weixin" data-cmd="weixin" title="分享到微信"></a>
    <a href="#" class="bds_tsina" data-cmd="tsina" title="分享到新浪微博"></a>
    <a href="#" class="bds_douban" data-cmd="douban" title="分享到豆瓣网"></a>
    <a href="#" class="bds_qzone" data-cmd="qzone" title="分享到QQ空间"></a>
    <a href="#" class="bds_tieba" data-cmd="tieba" title="分享到百度贴吧"></a>
    <a href="#" class="bds_twi" data-cmd="twi" title="分享到Twitter"></a>
    <a href="#" class="bds_fbook" data-cmd="fbook" title="分享到Facebook"></a>
    <a href="#" class="bds_more" data-cmd="more"></a>
</div>
<script>
    window._bd_share_config = {
        common: {
            bdSign: 'off'
        },
        share: {
            "bdSize": 16
        }
    }
</script>
<script>
    with (document) 0[(getElementsByTagName('head')[0] || body).appendChild(createElement('script')).src = 'https://cdn.hujinbo.me/libs/baidu-share/static/api/js/share.js?cdnversion=' + ~(-new Date() / 36e5)];
</script>
```