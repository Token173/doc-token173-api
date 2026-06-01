# n8n 工作流获取本地图片生成视频例子

 n8n 工作流获取本地图片生成视频例子  
 一、首先第一个节点选择触发方式，第二个节点选择从本地磁盘获取文件，第三个节点选择请求数据接口生成视频，第四个节点查询生成的视频 

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606569/image-preview)
 二、点进去读取文件
1.选择第一个从本地获取图片；  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606570/image-preview)
 2.第二个是文件地址需要注意文件地址斜杠"\"从磁盘复制出来的需要换成： "/"  ；  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606571/image-preview)
 三、点进第一个请求里
method 根据需要用到的接口的请求方法来，url是接口请求地址，验证的类型选 选择第二个，  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606572/image-preview)
 权限选Bearer Auth  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606573/image-preview)
 新增 在里面填令牌，可以在全部的http请求使用这个权限  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606574/image-preview)
 如果上面那个权限不行，就在Send Headers打开  在里面 Name输入：Authorization，
在Value输入：Bearer+令牌(Bearer和令牌中间有一个空格)  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606575/image-preview)
 2.在打开send Body根据文档输出相应的参数传参类型选择Form Data  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606576/image-preview)
 3.传图片这个位置比较特殊，左边是我们在上一个节点获取的本地的图片,
在传图片是选择n8n Binary File 能够获取左边的内容，value 里面填入data就是左边整个图片  

![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606577/image-preview)
 四、打开第四个节点
1.其他的配置都跟上面一样，但是因为是查询接口那么要看id在那个位置，如果https://xxxx:xxxx/xxxx/{id}  这种格式id在接口的最后的，就需要把左边上一个节点接口获取的id放入这个位置，可以手动输入，也可以点击左边我红圈位置的Tid标识符，拖拽到接口最后的位置，呈现如图所示  


![image.png](https://api.apifox.com/api/v1/projects/5443236/resources/606578/image-preview)
