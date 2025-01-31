---
title: 音乐
date: 2024-12-21 19:53
type: 'music'
aplayer: true
orderby: random
order: 1
top_img: https://pic.3gbizhi.com/uploads/20250123/f6d92e642c5611068c943bee32505b7b.png
cover: https://pic.3gbizhi.com/uploads/20250123/f6d92e642c5611068c943bee32505b7b.png
---

<!--
userServer: 指定调用的 API ，可选 netease, tencent, kugou, xiami, baidu ，分别对应网易云音乐、QQ音乐、酷狗音乐、虾米音乐、百度音乐
userType: 指定调用类型，可选 song, playlist, album, search, artist ，分别对应单曲、歌单、专辑、搜索结果、艺术家
userId：播放列表，这个播放列表可以登陆上述音乐网站，然后点击相应的音乐分类，然后可以浏览器的url中的id参数得到
-----------------------------------
©著作权归作者所有：来自51CTO博客作者生而为人我很遗憾的原创作品，请联系作者获取转载授权，否则将追究法律责任
基于Hexo和Butterfly创建个人技术博客，(14) 给博客站点添加Aplayer音乐
https://blog.51cto.com/arch/7066880
-->



<div id="music-page">
</div>
<script>
    var userId = "4939918079";
    var userServer = "netease";
    var userType = "playlist";
</script>
<link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/aplayer@1.10.1/dist/APlayer.min.css">
<script src="https://cdn.jsdelivr.net/npm/aplayer@1.10.1/dist/APlayer.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/meting@2.0.1/dist/Meting.min.js"></script>

<script>
    const params = new URLSearchParams(window.location.search);
    var _param = {
         getCustomPlayList: function () {
            const musicPage = document.getElementById("music-page");
            const playlistType = params.get("type") || "playlist";
            if (params.get("id") && params.get("server")) {
                var id = params.get("id");
                var server = params.get("server");
                musicPage.innerHTML = `<meting-js listMaxHeight="600px"id="${id}"server="${server}"type="${playlistType}"mutex="true"preload="auto"order="random"autoplay="true"></meting-js>`;
            } else {
                musicPage.innerHTML = `<meting-js listMaxHeight="600px"id="${userId}"server="${userServer}"type="${userType}"mutex="true"preload="auto"order="random"autoplay=true></meting-js>`;
            }
        }
    };

    _param.getCustomPlayList();
    const vh = window.innerHeight * 1;
    document.documentElement.style.setProperty('--vh', `${vh}px`);
    window.addEventListener('resize', () => {
        let vh = window.innerHeight * 1;
        document.documentElement.style.setProperty('--vh', `${vh}px`);
    });

</script>