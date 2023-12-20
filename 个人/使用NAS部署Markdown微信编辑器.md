晚上在GitHub上逛的时候偶然发现一个“Markdown微信编辑器”的开源项目。  
可以利用Markdown语法书写微信公众号文章。  
部署貌似很简单，支持多种部署方式，其中包括Docker。  
此时，我想起我家里的NAS支持Docker，于是我决定试着将该Markdown微信编辑器部署至我的NAS中。  
在这篇文章里，我将为大家详细介绍这个过程。
### 工具
- 绿联云DX4600
### 准备工作
首先，我们在电脑上启动绿联云客户端，并打开Docker。
![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703085665120-4fad6066-6fbc-402d-b0df-b992f91545db.png)

### 获取镜像
在镜像管理中，我们选择“镜像仓库”，输入“`doocs/md:latest`”并进行搜索。 

![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703085765597-74cd81f8-12ee-46c9-a9e2-d1acf3781be5.png)

在搜索结果中我们找到相应的镜像，点击“下载”。
![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703085851776-b13b8333-c954-4393-ab28-39543cddefaf.png)

### 创建容器
下载成功后，我们点击“容器管理”，然后选择“添加”刚才下载的镜像。在这个阶段，我们要设置容器的参数。

![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703085897947-762b2159-0d2c-4caf-a6ca-cbc90cf38165.png)

> 一个重要的设置就是端口映射。  

我们需要将容器的端口正确映射到NAS的端口，这样我们才能在浏览器中通过这个端口访问到刚创建的容器。例如，我这里将容器的8080端口映射到了NAS的80端口。
![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703085930200-d6ea22ea-2f85-4765-b87d-e924230e9681.png)

### 启动容器
设置好容器参数后，我们点击“创建后启动容器”按钮。稍等片刻，我们就能看到新建容器已经成功启动了。  
为了方便实时访问，我们还可以创建一个快捷方式，这样就不再需要每次输入ip地址了。  
![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703086011312-e07e23dd-4d21-4537-b9cb-bfc465c917a5.png)

好了，我们通过快捷方式或者浏览器输入地址就可以打开编辑器编写文章了。

没错，这篇文章就是使用这个Markdown微信编辑器写的。


![](https://raw.githubusercontent.com/youyiying/blogs/master/2023/12/20/1703086607605-3cc1aea9-e239-4466-ab24-5084ce7d6ab1.png)

### 总结
不得不说绿联云DX4600的Docker部署还是比较方便的，简单的配置就成功将Markdown微信编辑器部署到了NAS的Docker中。  

