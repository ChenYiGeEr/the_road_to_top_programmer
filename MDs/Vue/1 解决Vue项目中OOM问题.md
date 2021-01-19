#####  解决Vue项目运行过程报错JavaScript heap OOM(内存溢出)

###### 1.全局安装 **increase-memory-limit**

`npm install -g increase-memory-limit`

###### 2.进入工程目录下，执行以下命令

`increase-memory-limit`

###### 3."'node --max-old-space-size=xxxx"' 不是内部或外部命令，也不是可运行的程序

仅需在 node_modules 文件夹搜索 "%_prog%" 替换成 %_prog% (即去掉双引号)

若是无法全局替换 node_modules 文件的 "%_prog%" 需要暂时删除红框部分，替换完再添加上。（【文件-首选项-设置】搜索 Search: Exclude）如图

![img](https://github.com/ChenYiGeEr/the_road_to_top_programmer/blob/main/MDs/Vue/pictures/clipboard.png)

