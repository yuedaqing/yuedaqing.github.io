title: Jenkins——CI\CD部署教程
---
# 全局配置
## 配置访问仓库凭据
### 管理Jenkins![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011918864-4670b793-9ebd-488d-a407-98dc9651f28a.png#averageHue=%23f5f2f1&clientId=u9bb056de-ec78-4&from=paste&height=712&id=u2bd4d32b&originHeight=1423&originWidth=681&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=95946&status=done&style=none&taskId=u4916b08b-c205-40cc-a2b2-df02045451f&title=&width=340.5)
### 配置git仓库凭证![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011937874-96de3b46-5613-4e89-bc82-094ca58006af.png#averageHue=%23faf9f9&clientId=u9bb056de-ec78-4&from=paste&height=831&id=u81ffa345&originHeight=1661&originWidth=3199&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=451904&status=done&style=none&taskId=u88bb5a37-2b72-4ec6-881e-a001e421edd&title=&width=1599.5)
### 添加凭据![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011984226-283927ed-6c64-4052-bd24-93061586f1e7.png#averageHue=%23dfdfde&clientId=u9bb056de-ec78-4&from=paste&height=544&id=u9b6b02ea&originHeight=1087&originWidth=1629&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=190407&status=done&style=none&taskId=ud122d5e7-7b98-47eb-b901-f2054d0ebcb&title=&width=814.5)
### 选择仓库认证方式
### 如：用户名与密码![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723012311947-f6436790-510e-4dcd-9fb0-11c3450d3843.png#averageHue=%23ebebeb&clientId=u9bb056de-ec78-4&from=paste&height=605&id=ue068d72e&originHeight=1209&originWidth=2787&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=133500&status=done&style=none&taskId=u04130998-7415-4dc8-8330-f2f4aaef64f&title=&width=1393.5)
## 配置部署的远程服务器
### 管理Jenkins![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011918864-4670b793-9ebd-488d-a407-98dc9651f28a.png#averageHue=%23f5f2f1&clientId=u9bb056de-ec78-4&from=paste&height=712&id=usCKi&originHeight=1423&originWidth=681&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=95946&status=done&style=none&taskId=u4916b08b-c205-40cc-a2b2-df02045451f&title=&width=340.5)
### 进入系统配置![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723012555253-57c74a81-1e61-42e6-a146-518a9b4382b8.png#averageHue=%23faf9f8&clientId=u9bb056de-ec78-4&from=paste&height=722&id=u8506ceb1&originHeight=1443&originWidth=3055&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=454201&status=done&style=none&taskId=ua8722447-2780-4ae5-a3e0-08c0e9722ab&title=&width=1527.5)

3. ![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723012739071-0311be34-a3dc-44ba-982e-ec9045dc3d23.png#averageHue=%23fdfcfc&clientId=u9bb056de-ec78-4&from=paste&height=831&id=ud3072f0b&originHeight=1661&originWidth=3199&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=194602&status=done&style=none&taskId=uf452422c-96d2-4d52-8223-2802eb47262&title=&width=1599.5)
# 构建任务流程
## 新建项目![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011610280-1c0ef25a-fc1b-409c-967d-9b68d781ec57.png#averageHue=%23e8e5e5&clientId=u9bb056de-ec78-4&from=paste&height=739&id=u0cc9d520&originHeight=1477&originWidth=681&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=107279&status=done&style=none&taskId=u774d62ac-f0a6-4a01-bd7c-ad0decdb451&title=&width=340.5)

1. 输入项目名称![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011674855-baa389e0-5fa4-43a1-ba0b-8c7ab143ff35.png#averageHue=%23e8e8e7&clientId=u9bb056de-ec78-4&from=paste&height=835&id=u3eaa3068&originHeight=1669&originWidth=2761&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=354252&status=done&style=none&taskId=uceef0a3b-3940-4fc3-8645-dfb5e1e8342&title=&width=1380.5)
## 选择构建Maven项目
## 填写任务保留天数![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723011759529-1cb96457-bfcd-46c4-8756-b20016768bc8.png#averageHue=%23f6f5f5&clientId=u9bb056de-ec78-4&from=paste&height=574&id=u01224862&originHeight=1147&originWidth=2039&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=110170&status=done&style=none&taskId=uf3fb575d-5f58-471c-9b2c-be70b18f70d&title=&width=1019.5)
## 选择JDK 版本![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723012810378-20ec26d3-fa9e-4586-8981-5168d5959c18.png#averageHue=%23f8f8f8&clientId=u9bb056de-ec78-4&from=paste&height=158&id=u63cb25e5&originHeight=315&originWidth=1931&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=25252&status=done&style=none&taskId=ufecd6d29-02b1-4f41-beed-c593ff34a0b&title=&width=965.5)
## 配置Git

   1. 注意：**Git仓库地址必须与你当前jenkins所在的服务器网络互通**![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723012941536-bfa0bbd5-2b34-4115-96a6-6d60b14228f3.png#averageHue=%23f2f1f0&clientId=u9bb056de-ec78-4&from=paste&height=627&id=u19bb8031&originHeight=1253&originWidth=1957&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=132933&status=done&style=none&taskId=ueafbbfd9-7d03-42c4-bfff-cc8d8fe653b&title=&width=978.5)
## 构建触发器![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723013023408-701eb40d-ddf1-44c2-a573-fce5d60fad2a.png#averageHue=%23f5f5f5&clientId=u9bb056de-ec78-4&from=paste&height=794&id=u06ffe179&originHeight=1587&originWidth=1931&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=179794&status=done&style=none&taskId=u5298faa5-ce07-4a5a-b2a5-cbc008a82b3&title=&width=965.5)
## 配置Maven打包命令

   2. ![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723013068672-89f16b3c-67f7-4725-88ef-f4f7e549831b.png#averageHue=%23f8f8f8&clientId=u9bb056de-ec78-4&from=paste&height=337&id=u09e14b0b&originHeight=673&originWidth=1963&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=45144&status=done&style=none&taskId=uee78118d-01b3-4a46-8c4a-5275291112a&title=&width=981.5)
   3. 打包注意：
      1. 父子级项目: parent->childApplication
         1. 直接打包子级即可：clean package -pl childApplication -am -amd
      2. 多级嵌套项目：祖级->父级->子级
         1. clean package -pl 父级/子级 -am -amd
         2. 如果依赖是父级依赖祖级，子级依赖父级，并且子级使用到了祖级包里的类，需要子级pom文件声明祖级依赖。笔者遇到了这种情况，不然会打包失败！！！
   4. Maven参数解释：
| 参数 | 全称 | 释义 | 说明 |
| --- | --- | --- | --- |
| -pl | --projects | Build specified reactor projects instead of all projects | 选项后可跟随{groupId}:{artifactId}或者所选模块的相对路径(多个模块以逗号分隔) |
| -am | --also-make | If project list is specified, also build projects required by the list | 表示同时处理选定模块所依赖的模块 |
| -amd | --also-make-dependents | If project list is specified, also build projects that depend on projects on the list | 表示同时处理依赖选定模块的模块 |
| -N | --Non-recursive | Build projects without recursive | 表示不递归子模块 |
| -rf | --resume-from | Resume reactor from specified project | 表示从指定模块开始继续处理 |

## 现在可以测试 jenkins打包了！！！如果打包成功接着往下配置服务器资源！
## 配置远程服务器资源![image.png](https://cdn.nlark.com/yuque/0/2024/png/29559801/1723013807374-408b8c1d-4ca1-4864-a43d-d4189ab8ea9e.png#averageHue=%23efedec&clientId=u9bb056de-ec78-4&from=paste&height=801&id=u04b59328&originHeight=1601&originWidth=1901&originalType=binary&ratio=3.5&rotation=0&showTitle=false&size=251243&status=done&style=none&taskId=u8acd2166-b4d2-4848-b035-dac898146fe&title=&width=950.5)

- source files： 源文件。如果要传输文件夹内所有文件和文件夹则需要在文件夹路径后加两个*符号，如上图所示；
- Remove Prefix：移除前缀，是指源文件的前缀，比如现在我们只是传输html文件夹里的所有文件，但是html文件夹本身不需要在远程服务器出现，那么就需要将其移除，如上图所示；
- Remote directory 远程服务器目录，注意该目录是相对于刚刚系统设置里ssh servers里设置的路径
- exec command 在传输完成后执行的命令，一般为清理文件、复制文件、重启一些服务等等。
至此，已经配置完毕。
- 

## 遇到的问题：jenkins使用shell脚本执行nohup java -jar包失败。[jenkins使用shell脚本执行nohup java -jar包失败_nohup java -jar不生效-CSDN博客](https://blog.csdn.net/joshua317/article/details/125871391)

   9. jenkins默认会在构建完成后，杀掉构建过程中由shell命令触发的衍生进程。jenkins根据BUILD_ID识别某个进程是否为构建过程的衍生进程，故修改BUILD_ID后，jenkins就无法识别是否为衍生进程，则此进程能在后台保留运行。结论就是Jenkins程序只负责运行伪命令行nuhup 命令，并不保证是否成功运行 nuhup后面的命令。
   10. 解决方案：
```shell

OLD_BUILD_ID=$BUILD_ID
 
echo $OLD_BUILD_ID
 
export BUILD_ID=dontKillMe

#执行脚本---start
sh /data/softeware/xxx.sh  注意：脚本必须全路径
#执行脚本---end
#改回原来的BUILD_ID值
 
export BUILD_ID=$OLD_BUILD_ID
 
echo $BUILD_ID
#改回原来的BUILD_ID值
 
export BUILD_ID=$OLD_BUILD_ID
 
echo $BUILD_ID
```

1. **参考文章**：[Jenkins实现java+maven自动部署_jenkins+pipeline+java+maven-CSDN博客](https://blog.csdn.net/delongcpp/article/details/105500369)
# Jenkins角色权限配置

- 参考文章：[Jenkins Pipeline用户权限管理新技巧：打造安全高效的流水线！](http://www.360doc.com/content/24/0524/08/1314937_1124161901.shtml)

	
