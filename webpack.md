## 一.关于CLI.

  CLI是在执行webpack命令时后面紧随的参数，用于做不同的配置，例如:执行webpack --debug 将会覆盖webpack的config中的debug,设置为true

## 二.关于nodejs API.

  主要是对wepack.config进行compile.

## 三.关于configuration(主要用到的几个配置)

  ### 1.context: 默认的解析目录（绝对路径），为entry的相对路径进行解析铺垫,(默认应该为webpack执行的当前路径).  
  ### 2.entry: 模块构建的入口文件(其中路径是相对于context设置的路径，而不是config文件的路径).  
    (1)string类型: 模块构建的入口文件.  
    (2)array类型: 将数组内的文件合并打包到main.js里.  
    (3)object类型: 每个key对应一个bundle，生成不同的bundle，内部机制同上面两种.  
    (4)方法类型（动态入口）: 方法或者promise返回一个路径动态生成入口文件.    
  ### 3.output：生成文件，包括输出文件和输出路径等  
    (1)filename: 为生成的文件进行命名.  
    (2)path: 生成文件的地址（绝对路径）.  
    (3)publicPath: 文件产生后的链接地址，用在<script>或者<link>或者url()里的前缀地址。  
    (4)chunkFilename: 生成的chunk文件名.  
    ...  
  ### 4.module: 配置loaders  
    (1)loaders: array，每个item都包含
        test: 检测文件（正则）
        exclude: 不检测的文件
        include: 
        loader: 用!串联不同的loader
        loaders: loader的数组

    (2)preLoaders,postLoaders: 语法和loaders一样
        preLoaders: 在调用loaders之前加载的loader，例如JSHint，代码检查.  
  ### 5.resolve:  
    (1)alias: 用别名代替具体地址加快webpack过程.  
    (2)root: 一个包括所有module的绝对路径.  
    (3)modules: 默认为node_modules，绝对路径或者相对路径都行，可以添加路径在node_modules前（前边的先被搜索到）.  
    (4)fallback: 在root和modulesDirectories都找不到的modules的地址.  
    (5)extensions: 用于配置程序可以自行补全哪些文件后缀.  
  ### 6.plugins: 编译时不同的plugins  
  ### 7.devtool: 开发模式下的工具(source-map).  
  ...
