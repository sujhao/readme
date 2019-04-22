# nodejs使用官方Google Protobuf 3 

## 1.首先获取protobuf.

打开命令行输入以下命令 来获取nodejs的pb库.

npm install google-protobuf
或者通过下面的方式也是我推荐的方式下载需要的库.

在自己的项目文件夹下创建一个 package.json文件.

{
  "name": "KOOKEngine",
  "description": "KOOKEngine Game Framwork!",
  "version": "1.0.0",
  "dependencies": {
    "google-protobuf" : "3.2.0"
  },
  "scripts": {
  },
  "author": "EnelWang",
  "license": "ISC"
}
可以看到指定了pb的版本.
然后通过命令方便的来安装到目录下.(如果想安装其他的库,在字典内添加更多的库)

npm install
之后会自动安装 依赖库. 这是commonJS规范.具体参见相关文档.

## 2.下载protobuf的命令行工具

https://github.com/google/protobuf/releases

什么平台上面开发自己选择.

## 3.配置相关平台的protoc命令行工具到系统PATH目录.

测试是否protoc配置成功. 任意目录下输入


protoc --version
## 4.编写一个proto文件

syntax = "proto3";

message SearchRequest {
  string name = 1;
  string password = 2;
}
起名为 base.proto

## 5.编译这个proto文件,生成可用的代码

在该文件目录下使用命令


protoc --js_out=import_style=commonjs,binary:. base.proto
之后生成 base_pb.js 该文件就是nodejs可以使用的序列化文件了

## 6.我们创建一个 main.js的 js文件.里面编写


var basepb = require('./base_pb');
console.log(basepb);
 
var message = new basepb.SearchRequest();
console.log(message);
 
message.setName("TS");
message.setPassword("123456");
 
var bytes = message.serializeBinary();
console.log(bytes);
 
var message2 = basepb.SearchRequest.deserializeBinary(bytes);
console.log(message2);
## 7.运行测试结果
node main.js
通过该命令则可运行程序查看运行结果.