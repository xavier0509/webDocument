# webDocument
- **web打包-------fis3**

> 一.fis3打包工具（http://fex-team.github.io/fis3/docs/beginning/intro.html）
> * FIS3 是面向前端的工程构建工具。解决前端工程中性能优化、资源加载（异步、同步、按需、预加载、依赖管理、合并、内嵌）、模块化开发、自动化工具、开发规范、代码部署等问题。
就项目而言，打包工具能够做到资源的定位、压缩，产生文件指纹，对于发布、更新等步骤起到帮助。<br/>


>1.安装node和npm（https://nodejs.org）
> * 安装node和npm（新版本的node自带npm）<br/>
> * Windows 用户安装完成后需要在 CMD 下确认是否能执行 node 和 npm<br/>
> * 命令：node -v             npm -v<br/>


>2.安装fis3（cmd下执行）
> * npm install -g fis3<br/>
> * 安装完成后执行 fis3 -v 判断是否安装成功<br/>
> * 升级fis3 npm update -g fis3<br/>
> * 重装fis3 npm install -g fis3<br/>

>3.命令使用
> * 进入项目根目录，执行命令：
fis3 release -d \<path\>,
\<path\> 为任意目录，即打包后文件生成的目录<br>

>全局或本地安装插件 
npm install [-g] fis3-hook-relative 

>启用插件 
fis.hook('relative'); 

>fis3打包工具能够针对png，jpg等文件产生文件指纹，并进行资源定位。
但该方式在js文件或 html中的script标签内的内容中出现的文件将不起作用，需另作处理，使用编译函数 __uri(path) 来定位资源
例如：
```
document.getElementById('pic_info').src = app.rel_html_imgpath(__uri("../images/login.png"))
```
>在css文件中或html中style标签内的内容，则采用url(path) 以及 src=path 字段来替换
而app.rel_html_imgpath()函数则是对编译后的指纹进行的一个处理，代码如下：
```
rel_html_imgpath:function(iconurl) 
{
        console.log(app.canonical_uri(iconurl.replace(/.*\/([^\/]+\/[^\/]+)$/, '$1')));
        return app.canonical_uri(iconurl.replace(/.*\/([^\/]+\/[^\/]+)$/, '$1'));
}

canonical_uri:function(src, base_path) 
{
        var root_page = /^[^?#]*\//.exec(location.href)[0],
        root_domain = /^\w+\:\/\/\/?[^\/]+/.exec(root_page)[0],
        absolute_regex = /^\w+\:\/\//;
        // is `src` is protocol-relative (begins with // or ///), prepend protocol  
        if (/^\/\/\/?/.test(src)) 
        {  
        src = location.protocol + src; 
        }  
    // is `src` page-relative? (not an absolute URL, and not a domain-relative path, beginning with /)  
        else if (!absolute_regex.test(src) && src.charAt(0) != "/")  
        {  
            // prepend `base_path`, if any  
            src = (base_path || "") + src; 
        }
    // make sure to return `src` as absolute  
        return absolute_regex.test(src) ? src : ((src.charAt(0) == "/" ? root_domain : root_page) + src);  
}
```
>在完成页面开发之后，先自行在本地服务器上进行测试，代码上传到服务器上，
在电视上通过CordovaTest.apk进行测试。
在确认没有问题之后，发出邮件给运维人员进行正式环境(https://webapp.skysrt.com) 的部署。
