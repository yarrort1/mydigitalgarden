---
{"dg-publish":true,"permalink":"/softwares/obsidian/Obsidian 简明发布方式/"}
---

# Obsidian 简明发布方式

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-2)前言

使用 Obsidian 写好笔记后，有的时候想把自己的笔记分享给朋友，有的时候想把笔记发布到网络上，作为个人博客或者数字花园。而 Obsidian 是基于本地存储的 markdown 笔记，这就意味着无法直接生成网页链接发给朋友，要么使用 Obsidian 的官方发布服务，要么通过部署个人网站将 markdown 文件生成网页进行发布。现有介绍较多的一些发布方案已经足够简单，但是往往需要电脑端，需要 git，需要简单的代码等等，门槛还是略高。因此本文介绍一种更为简单可用的 Obsidian 发布方式。

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-3)概述

本文介绍一种简单明了的 Obsidian 发布方式，不需要电脑，不需要会代码，不需要特殊网络，不需要使用其他软件，仅仅需要在手机上点点点即可完成。  
这些通过使用插件 [Digital Garden 98](https://github.com/oleeskild/Obsidian-Digital-Garden) 来实现，笔记文件托管在 [GitHub 15](https://github.com/) 上，通过 [Netlify App 72](https://app.netlify.com/) 部署发布，不需要任何费用。  
不知道为什么介绍使用这个插件的文章很少，而我在配置的时候也踩了两个坑，导致一开始并没用发布成功。  
现在就一步一步的跟着做吧。如果你也想拥有自己的个人博客或者说数字花园。

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-4)第一步 部署网站

是的没错，我们现在就开始部署网站了![:blush:](https://forum-zh.obsidian.md/images/emoji/twitter/blush.png?v=12 ":blush:")。

1. 点击 [Deploy to Netlify 199](https://app.netlify.com/start/deploy?repository=https://github.com/oleeskild/digitalgarden)
    
2. 点击网页中 “Connect to GitHub” 按钮。如果要登录的话就注册一个 Github 账号登录。  
    
    [![Screenshot_2023-05-12-15-32-58-814_com.lemurbrowser.exts.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/1/10fdff674ffd2fe134c444f14fa86bc3acb94579_2_230x500.jpeg)
    
    1080×2340 164 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/1/10fdff674ffd2fe134c444f14fa86bc3acb94579.jpeg "Screenshot_2023-05-12-15-32-58-814_com.lemurbrowser.exts.jpg")
    
3. 在 “Repository name” 框中输入一个存放笔记的 Github 仓库名称。或者直接使用默认的 “digitalgarden”。  
    
    [![Screenshot_2023-05-12-15-34-09-601_com.lemurbrowser.exts.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/0/06a91eb3cdf2746e93005240f768ff283ef7651d_2_230x500.jpeg)
    
    1080×2340 123 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/0/06a91eb3cdf2746e93005240f768ff283ef7651d.jpeg "Screenshot_2023-05-12-15-34-09-601_com.lemurbrowser.exts.jpg")
    
4. 点击 “Save & Deploy” 按钮。
    
5. 出现下面这个界面就说明部署好了。  
    
    [![Screenshot_2023-05-12-16-18-40-675_com.lemurbrowser.exts.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/b/bed2d577163f2b136aed38dfcd1901609ebe6986_2_230x500.jpeg)
    
    1080×2340 184 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/b/bed2d577163f2b136aed38dfcd1901609ebe6986.jpeg "Screenshot_2023-05-12-16-18-40-675_com.lemurbrowser.exts.jpg")
    
6. 上图中 “Permalink” 这个链接点进去就是你的网站啦。当然现在还没有内容。  
    
    [![Screenshot_2023-05-12-16-19-44-251_com.lemurbrowser.exts.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/4/4f7664c2cd58ddb2857260cf688e98562997df1e_2_230x500.jpeg)
    
    1080×2340 122 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/4/4f7664c2cd58ddb2857260cf688e98562997df1e.jpeg "Screenshot_2023-05-12-16-19-44-251_com.lemurbrowser.exts.jpg")
    

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-5)第二步 安装插件

在 Obsidian 插件市场中搜索下载安装即可。

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-6)第三步设置插件

1. 获取 Github 密钥。点击 [access token 61](https://github.com/settings/tokens/new?scopes=repo)，noto 输入框随便填一下英文名称，expiration 选 no expiration。往下滑点击 "Generate token"按钮并复制密钥待用。  
    
    [![Screenshot_2023-05-12-17-32-07-343_com.lemurbrowser.exts.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/d/dd04f43f8e15a1c19c1f8f324e0942e3fefd4167_2_230x500.jpeg)
    
    1080×2340 281 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/d/dd04f43f8e15a1c19c1f8f324e0942e3fefd4167.jpeg "Screenshot_2023-05-12-17-32-07-343_com.lemurbrowser.exts.jpg")
    
2. 打开插件 “Digital Garden” 的设置页面。将之前设置的"Repository name"填入 repo name，username 填入 Github 的用户名，token 填入上面一步获得的密钥。URL 填入之前的"Permalink"。  
    
    [![IMG_20230512_174133.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/7/7ef3c1ea80e49f85d8d30fd1a081fd110408ad29_2_230x500.jpeg)
    
    1080×2340 282 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/7/7ef3c1ea80e49f85d8d30fd1a081fd110408ad29.jpeg "IMG_20230512_174133.jpg")
    
3. 继续往下滑动设置页面，将下图中"Slugify Note URL"的选项关掉。  
    
    [![Screenshot_2023-05-12-17-40-23-752_md.obsidian-edit.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/1/168af920a52e3985089aafbc691e0003e066d3c9_2_230x500.jpeg)
    
    1080×2340 273 KB
    
    ](https://forum-zh.obsidian.md/uploads/default/original/2X/1/168af920a52e3985089aafbc691e0003e066d3c9.jpeg "Screenshot_2023-05-12-17-40-23-752_md.obsidian-edit.jpg")
    

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-7)第四步发布笔记

好啦现在就可以发布笔记到你的网站上啦。  
打开笔记页面，搜索并打开命令 “Digital Garden: Quick Publish And Share Note”，笔记就发布好啦，并且自动将页面链接复制到剪贴板上，过一会在浏览器打开链接就可以看到发布好的页面![:rocket:](https://forum-zh.obsidian.md/images/emoji/twitter/rocket.png?v=12 ":rocket:")。  

[![Screenshot_2023-05-12-17-48-01-209_md.obsidian-edit.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/e/e57c14f6216839c9579888c11325307fc10fcbdf_2_230x500.jpeg)

1080×2340 178 KB

](https://forum-zh.obsidian.md/uploads/default/original/2X/e/e57c14f6216839c9579888c11325307fc10fcbdf.jpeg "Screenshot_2023-05-12-17-48-01-209_md.obsidian-edit.jpg")

 

[![IMG_20230512_175117.jpg](https://forum-zh.obsidian.md/uploads/default/optimized/2X/c/cf04bec6158e2dd6db2b6f7c438e537c63f1b197_2_690x168.jpeg)

IMG_20230512_175117.jpg1080×264 56.5 KB

](https://forum-zh.obsidian.md/uploads/default/original/2X/c/cf04bec6158e2dd6db2b6f7c438e537c63f1b197.jpeg "IMG_20230512_175117.jpg")

  
这一篇教程就通过"Digital Garden" 发布成功了，可以点击查看 [Obsidian 简明发布方式]( [https://enneaa.netlify.app/📜页面/Obsidian 123](https://enneaa.netlify.app/%F0%9F%93%9C%E9%A1%B5%E9%9D%A2/Obsidian) 简明发布方式/)

##### [](https://forum-zh.obsidian.md/t/topic/19256#h-8)坑在哪里

其实这个插件的使用非常简单，插件开发者也提供了[使用说明 50](https://dg-docs.ole.dev/getting-started/01-getting-started/)，大家可以探索更多具体的用法。  
但是对于国内的中文使用者，有两个地方稍不注意就会导致发布不成功。  
一是上面步骤中 "Slugify Note URL"的选项一定要关掉。不然只要笔记的路径或笔记本名里面有中文，就无法生成正确的链接地址，导致无法访问发布的笔记。  
二是官方默认的网站部署网站部署服务是 [Vercel 13](https://vercel.com/dashboard)，在国内网络环境下打不开，想正常使用还得绑定域名，又更麻烦了。用 [Netlify 72](https://app.netlify.com/) 就可以直接访问了，不存在这个问题。

##### [](https://forum-zh.obsidian.md/t/topic/19256#digital-garden-9)“Digital Garden” 发布方式的优点

在开头已经说了很多这个发布方式的优点，最最主要的就是非常非常简单。笔记写好，小手一点，笔记就发出去了。  
后面我还发现了一个另外的惊喜，就是它可以自动将笔记中的本地图片上传到 Github 里面，完全不需要配置额外的图床，真的很棒。  
并且，居然还提供网站的 RSS，我的主站地址是 [https://enneaa.netlify.app/ 220](https://enneaa.netlify.app/) ，那么 RSS 订阅地址就是 [ä¹æ¨ð² 13](https://enneaa.netlify.app/feed.xml) 。

以上就是全部内容，希望能给大家带来一些帮助。