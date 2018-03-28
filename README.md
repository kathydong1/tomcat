如何用Tomcat部署前端静态文件

我们可以把静态文件直接放到webapps下面。当只是运行一个项目的时候，这种方法还好，但是当你涉及到两个以上项目的时候，就麻烦了。配置虚拟目录有两种方法。

一、直接在servler.xml里修改 
1. 首先找到Tomcat下的conf文件夹下的server.xml。 
2. 通过习惯用的编辑器打开server.xml，可以看到Host标签，默认就有一个，一个Host代表一个站点，找到Host结束标签，我们在这中间配置虚拟路径。 
3. 以如下配置为例。

path指虚拟目录，与浏览器访问的路径相关，如果直接是path=”/”，访问就是http://localhost:8080/XX.jsp
如果为空串，也是一样，如果加了项目名，访问路径也要加，如path=”/home”,访问就是http://localhost:8080/home/XX.jsp。

docBase指实际存在路径，一般在硬盘里。如果我们的文件home直接放在了E盘下，那docBase=“E:\home”

reloadable指有文件更新时，是否重新加载，一般设置为true，设置为true后，不需重新启动，就能验证我们的改动，不过修改了java文件后，可以重新编译需要一小会，在IDE下的控制台里可以看见输出，一般没有输出滚动出来的时候，就可以了。这三个一般经常设置。

debug指等级，一般设置为debug=“0”，提供最少的信息。设不设置无大影响。

<Context path="/home" debug="0" docBase="E:\home" reloadable="true" />
