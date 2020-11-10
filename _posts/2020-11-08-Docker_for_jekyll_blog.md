---
layout: post
title:  "Docker编译jekyll博客网页"
date:   2020-11-08
categories: work
---
### 主题流程摘要
<div class="mermaid">
graph TD;
    A[下载主题]-->B[镜像配置];
    B[镜像配置]-->C[启动服务];
</div>

### 第一步

下载jekyll的minima主题的代码

### 第二步

编辑docker-compose的配置文件

```yml
jekyll:
  image: jekyll/jekyll:4.0
  container_name: jekyll
  stdin_open: true
  entrypoint: ["sh"]
  ports:
    - 8080:4000
    - 8443:35729
  volumes:
    - ./:/srv/jekyl
```

通过运行`docker-compose up`启动验证jekyll服务，该服务支持热更新。


### 第三步

把代码github上，在外网就可以访问得到了。

### 附录一 添加mermaid插件

在markdown中通过添加标签mermaid以引入代码块，但是在jekyll中没有对应的标签，需要采用另外方式。

1. 在md文件末尾添加一下内容

```javascript
<script src='https://unpkg.com/mermaid@7.1.2/dist/mermaid.min.js'></script>
<script>mermaid.initialize({startOnLoad:true});</script>
```

2. 在对应代码块中添加对应内容包起来

```html
<div class="mermaid">

</div>
```


![img](/assets/ljh.png)

<script src='https://unpkg.com/mermaid@7.1.2/dist/mermaid.min.js'></script>
<script>mermaid.initialize({startOnLoad:true});</script>