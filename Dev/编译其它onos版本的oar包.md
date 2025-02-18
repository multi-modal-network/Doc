# 编译其它onos版本的oar包
2025-2-18 项目切换onos版本到2.6，需要提供2.6版本的oar包。
## 记录
218.199.84.172进行编译，修改依赖版本，然后重新编译即可。
```
cd /home/onos/onos2.6/basic-multi-modal
nano pom.xml
```
把下面这段代码中的3.0.0修改为2.6.1
```
    <parent>
        <groupId>org.onosproject</groupId>
        <artifactId>onos-dependencies</artifactId>
        <version>3.0.0-SNAPSHOT</version>
    </parent>
```
然后重新编译，在basic-multi-modal目录下输入
```
make pipeconf
```
编译结果在basic-multi-modal/target目录下。