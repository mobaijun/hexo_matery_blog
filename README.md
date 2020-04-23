<p align="center"><img width="15%" src="https://www.mobaijun.com/medias/avatar.jpg"/></p>
<h4 align="center">框架师</h4>
<table align="center">
    <tr>
        <td align="center"><img width="78px" height="78px"
                                src="https://gitee.com/static/images/logo-black.svg?t=158106664"/>
        </td>
        <td align="center"><img width="78px" height="78px"
                                src="http://pic.51yuansu.com/pic2/cover/00/30/78/581091674a0d3_610.jpg"/>
        </td>
        <td align="center"><img width="78px" height="78px"
                                src="http://i-2.yiwan.com/2015/10/24/765d53b8-d8f7-44b9-bd78-9807cc99ea3e.png"/>
        </td>
        <td align="center"><img width="78px" height="78px"
                                src="https://www.mobaijun.com/medias/avatar.jpg"/>
        </td>
    </tr>
    <tr>
        <td align="center">Gitee</td>
        <td align="center">GitHub</td>
        <td align="center">Coding</td>
        <td align="center">博客</td>
    </tr>
</table>

请您阅读时注意,这不是生成后的网页文件，是您可以直接使用的源码，您只需要把博客相关信息换成您自己的就可以部署了，对于新手或者不懂编程的小伙伴来说，简直是福音，极大简化了您构建博客的工作量和复杂度，每个人都可以下载并修改成自己喜欢样式！如果你有修改想法，欢迎给我`star`！

**博客基于`Hexo`框架搭建，用到[hexo-theme-matery](https://github.com/shw2018/hexo-theme-matery)主题,并在此基础之上做了很多修改，修复了一些bug，增加了一些新的特性和功能，博客地址：[https://mobaijun.com](https://mobaijun.com)，博客演示：[mobaijun.com](https://mobaijun.com)。**

**简单使用方法**：

1. `star` 本项目
2. 安装[Git](https://git-scm.com/downloads), 安装[nodeJS](https://nodejs.org/en/)
3. 你可以直接`fork`一份源码到你的仓库，`clone`到本地
4. 在本地博客仓库运行`npm i`命令安装依赖包
5. 修改配置信息，改成自己的信息
6. 运行命令`hexo  clean`（清除生成文件），`hexo g`（生成网页）， `hexo  s`（本地预览），`hexo d`（部署）

## 特性

**原主题特性**:

- 简单漂亮，文章内容美观易读
- [Material Design](https://material.io/) 设计
- 响应式设计，博客在桌面端、平板、手机等设备上均能很好的展现
- 首页轮播文章及每天动态切换 `Banner` 图片
- 瀑布流式的博客文章列表（文章无特色图片时会有 `24` 张漂亮的图片代替）
- 时间轴式的归档页
- **词云**的标签页和**雷达图**的分类页
- 丰富的关于我页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
- 可自定义的数据的友情链接页面
- 支持文章置顶和文章打赏
- 支持 `MathJax`
- `TOC` 目录
- 可设置复制文章内容时追加版权信息
- 可设置阅读文章时做密码验证
- [Gitalk](https://gitalk.github.io/)、[Gitment](https://imsun.github.io/gitment/)、[Valine](https://valine.js.org/) 和 [Disqus](https://disqus.com/) 评论模块（推荐使用 `Gitalk`）
- 集成了[不蒜子统计](http://busuanzi.ibruce.info/)、谷歌分析（`Google Analytics`）和文章字数统计等功能
- 支持在首页的音乐播放和视频播放功能

 **增加的工作或特性(未打钩的是已做但还没更新到源码的)**:

- [x] 修改了原主题的一些很多`bug`    
- [x] 加入图片懒加载功能，在根目录配置文件开启和关闭     
- [x] 增加`留言板`功能           
- [x] 在关于板块,加入`简历`功能页    
- [x] 支持`emoji`表情，用`markdown emoji`语法书写直接生成对应的能**跳跃**的表情。   
- [x] 增加网站运行时间显示  
- [x] 增加`动漫模型`     
- [x] 整体替换Banner图片和文章特色图片
- [x] 加入`AES`加密方法
- [x] 加入实用的快捷导航栏      
- [x] 修改了一些控件的参数   
- [x] 修改部分样式,比如: 文章卡片,固定高度,使其不至于因为文章摘要的长短不同导致卡片大小不一使页面布局很不美观,类似的还有友链卡片,优化了页面内容布局,视觉更整齐美观          
- [x] 解决首页文章列表卡片上方 `border-radius`圆角失效的bug  
- [x] 添加页面樱花飘落动效           
- [x] 添加鼠标点击烟花爆炸动效   
- [x] 加入鼠标点击文字特效   
- [x] 加入了网页加密功能,屏蔽鼠标右键键盘事件
- [x] 添加页面雪花飘落动效            
- [x] 添加在线聊天插件            
- [x] 调整线聊天插件参数，使之能够随着鼠标滑动位置自适应调整 
- [x] 加入了首页自动获取段子
- [x] 加入了自动获取古诗词
- [x] 解决了分页加载头部音乐/视频/格言bug
- [x] 替换搜索框样式和背景
- [x] 修改首页名称字体
- [ ] 持续更新...

>**更多详情教程，强烈推荐看我写的：[ windows环境下搭建一个Hexo博客 ]( https://mobaijun.com/posts/259861027.html )**
>
>**最后，如果项目和教程对你有所帮助或者你看见了还算比较喜欢，欢迎给我`star`，谢谢您！**

有什么问题可以在文章最后评论区**留言和讨论**，当然，欢迎点击文章最后的打赏按键，请博主一杯冰阔乐，笑～
<table align="center">
    <tr>
        <td align="center"><img width="200px" height="200px"
                                src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/zf/alipay.jpg"/>
        </td>
        <td align="center"><img width="200px" height="200px"
                                src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/zf/wechat.jpg"/>
        </td>
        <td align="center"><img width="200px" height="200px"
                                src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/zf/zan.jpg"/>
        </td>
    </tr>
    <tr>
        <td align="center">支付宝</td>
        <td align="center">微信支付</td>
        <td align="center">赞赏</td>
    </tr>
</table>