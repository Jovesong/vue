## vue jsonp 
1. 描述：使用jsonp实现跨域请求
2. 解决方法： npm install jsonp --save
3. 代码演示：

    	jsonp('http://www.example.com/foo', null, function (err, data) {

			if (err) {
				console.error(err.message);
			} else {
				console.log(data);
			}
		});

4. 链接：[https://github.com/axios/axios/blob/master/COOKBOOK.md#jsonp](https://github.com/axios/axios/blob/master/COOKBOOK.md#jsonp " vue+jsonp跨域")
## 
## invalid host header
1. 描述：使用webpack dev server通过本地IP启动服务器后invalid host header的错误解决办法
2. 解决方法： 
 
			webpack.config.js文件内的webpackDevServer配置如下
			devServer: {
			    contentBase: __dirname,
			    compress: true,
			    port: 9000,
			    inline: true,
			    host: '0.0.0.0'
			}
		要加一个
        disableHostCheck: true


3. 链接：[http://www.whidy.net/%E4%BD%BF%E7%94%A8webpack-dev-server%E9%80%9A%E8%BF%87%E6%9C%AC%E5%9C%B0ip%E5%90%AF%E5%8A%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%90%8Einvalid-host-header%E7%9A%84%E9%94%99%E8%AF%AF%E8%A7%A3%E5%86%B3.html](http://www.whidy.net/%E4%BD%BF%E7%94%A8webpack-dev-server%E9%80%9A%E8%BF%87%E6%9C%AC%E5%9C%B0ip%E5%90%AF%E5%8A%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%90%8Einvalid-host-header%E7%9A%84%E9%94%99%E8%AF%AF%E8%A7%A3%E5%86%B3.html "invalid host header") ---invalid host header
##


## 微信授权登录
1. 描述： redirecturi 域名与后台域名不一致 1003
2. 解决方法： 
3. 
	
		授权后重定向的回调链接地址要与微信公众平台网页授权用户基本信息要在同一文件夹下
		微信公众平台网页授权域名与授权后重定向的回调链接地址域名一致

![文件位置](https://i.imgur.com/jEpYfFC.png)
![网页授权域名](https://i.imgur.com/JiOzJ5M.png)
##

## HTML5 History 模式
1. 描述: 用Vue-cli脚手架建立一个项目后,npm run build 压缩打包后关于nginx与Tomcat配置
2. 解决方法:
    
  			
        nginx文件内的nginx.conf配置如下:
		server {
        	listen       3000;
        	server_name  192.168.1.210;

	        location / {
	            root   /usr/www/dist;
	            index  index.html index.htm;
	            try_files $uri $uri/ /index.html; //HTML5 History 模式配置
	        }
        }
        tomcat下WEB-INF文件夹下web.xml配置如下:
		<?xml version="1.0" encoding="ISO-8859-1"?>
		<web-app xmlns="http://java.sun.com/xml/ns/javaee"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
		                      http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
		  version="3.0"
		  metadata-complete="true">
			<display-name>webapp</display-name>
			<description>
			     webapp
			</description>
		    <error-page>  
			   <error-code>404</error-code>  
			   <location>/</location>  
			</error-page>  
		</web-app>
 3.链接: 
 a. [http://https://router.vuejs.org/zh-cn/essentials/history-mode.html](http://https://router.vuejs.org/zh-cn/essentials/history-mode.html "HTML5 History 模式")  ---nginx HTML5 History 模式
 b.[https://segmentfault.com/q/1010000010079589](https://segmentfault.com/q/1010000010079589 "tomcat之history模式配置") -----tomcat服务如何配置vue-router的history模式
##

##tomcat Server.xml Context配置
1. 描述:Tomcat中给server.xml加入<Context>元素

	<Context>代表了运行在<Host>上的单个Web应用，一个<Host>可以有多个< Context>元素，每个Web应用必须有唯一的URL路径，这个URL路径在<Context>中的属性
	
	path中设定。<Context>元素的属性: 
	
	path:指定访问该Web应用的URL入口，如：http://127.0.0.1:8080/helloApp1。 
	
	docBase:指定Web应用的文件路径，可以给定绝对路径，也可以给定相对于<Host>的appBase属性的相对路径，如果Web应用采用开放目录结构，则指定Web应用的根目录，如果Web应用是个war文件，则指定war文件的路径。
	
	
	reloadable:如果这个属性设为true，tomcat服务器在运行状态下会监视在WEB-INF/classes和WEB-INF/lib目录下class文件的改动，如果监测到有class文件被更新的，服务器会自动重新加载Web应用。
	
	在开发阶段将reloadable属性设为true，有助于调试servlet和其它的class文件，但这样用加重服务器运行负荷，建议在Web应用的发布阶段将reloadable设为false。
2. 配置:
	
		tomcat Server.xml Context配置: 
	     <Host name="localhost"  appBase=""
	            unpackWARs="true" autoDeploy="true"
	            xmlValidation="false" xmlNamespaceAware="false">
			<Context docBase="webapps/hello" path="/hello"  reloadable="true" ></Context>
	    </Host>

3. 链接:[https://www.cnblogs.com/langren1992/p/5220736.html](https://www.cnblogs.com/langren1992/p/5220736.html "Server.xml Context配置")
##

## rimraf
1. 描述: rimraf 包的作用：以包的形式包装rm -rf命令，用来删除文件和文件夹的，不管文件夹是否为空，都可删除.
2. 安装: npm install rimraf --save-dev
3. 使用:

  		cmd下: rimraf 文件名
		文件中: 
		const rimraf = require('rimraf');
		rimraf('./test.txt', function (err) { // 删除当前目录下的 test.txt
		  console.log(err);
		});

##
		        
     

		