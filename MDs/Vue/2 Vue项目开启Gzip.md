##### Vue项目开启Gzip

###### 1.修改config/index.js 中productionGzip: false修改为true;

使用vue-cli生成的项目，会自动配好相关的设置。
如下图找到对应的文件，productionGzip改为true，开启Gzip压缩

![image-20201024184338841](https://github.com/ChenYiGeEr/the_road_to_top_programmer/blob/main/MDs/Vue/pictures/image-20201024184338841.png)

###### 2.找到下图文件，这里是配置Gzip的位置

![image-20201024184741014](https://github.com/ChenYiGeEr/the_road_to_top_programmer/blob/main/MDs/Vue/pictures/image-20201024184741014.png)

```VUE
webpackConfig.plugins.push(
    new CompressionWebpackPlugin({
      // asset: '[path].gz[query]',
	  filename: '[path].gz[query]',
      algorithm: 'gzip',
      test: new RegExp(
        '\\.(' +
        config.build.productionGzipExtensions.join('|') +
        ')$'
      ),
      threshold: 10240,
      minRatio: 0.8
    })
  )
}
```

这里是[compression-webpack-plugin](https://www.npmjs.com/package/compression-webpack-plugin)的配置项信息

###### 3.npm安装compression-webpack-plugin依赖 注意安装1.1.12版本即可

`npm install --save-dev compression-webpack-plugin@1.1.12`

###### 4.npm run build 将项目部署到线上

###### 5.对线上nginx配置开启Gzip

```nginx
    gzip on;
    gzip_buffers 4 16k;
    gzip_comp_level 6;
    gzip_types text/plain application/x-javascript application/javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;
```
