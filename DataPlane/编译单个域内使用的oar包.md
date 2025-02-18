# 编译单个域内使用的oar包
首要目的是测试编译的oar包能否在2.6版本的onos上正常运行。其次，可以作为编译历史提交代码的oar包的参考。
## 修改依赖版本
在basic-multi-modal目录中修改pom.xml中的一些字段3.0.0为2.6.1
```
    <parent>
        <groupId>org.onosproject</groupId>
        <artifactId>onos-dependencies</artifactId>
        <version>2.6.1-SNAPSHOT</version>
    </parent>
```
## 回到历史版本
只编译历史版本的话需要回滚到代码不包含处理Tna逻辑的部分。
```
git log --oneline
git checkout 0725ffe
```
## 编译oar包
输出路径在basic-multi-modal/target下，首先把之前的oar删掉
```
rm -rf basic-tna-1.0.1-SNAPSHOT.oar
```
然后在basic-multi-modal目录下执行`sudo make pipeconf`。接着在target目录下可以看到重新编译出的OAR包。(如果编译失败，可能是网络原因，重新编译即可)
```
[INFO] Building jar: /mvn-src/target/basic-tna-1.0.1-SNAPSHOT-tests.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  17:27 min
[INFO] Finished at: 2025-02-18T07:15:56Z
[INFO] ------------------------------------------------------------------------
*** ONOS pipeconf .oar package created succesfully
/home/onos/project/basic-multi-modal/target/basic-tna-1.0.1-SNAPSHOT.oar
onos@onos-KVM:~/project/basic-multi-modal$ ls
app.xml  cluster2  cluster3  docker-compose.yml  features.xml  Makefile  netcfg_gen.py  p4src  pom.xml  README.md  src  target  tofino-netcfg.json  tofino-netcfg.json.bak  tofino-test.json
onos@onos-KVM:~/project/basic-multi-modal$ cd target/
onos@onos-KVM:~/project/basic-multi-modal/target$ ls
basic-tna-1.0.1-SNAPSHOT.jar  basic-tna-1.0.1-SNAPSHOT-tests.jar  generated-sources       maven-archiver  oar               test-classes
basic-tna-1.0.1-SNAPSHOT.oar  classes                             generated-test-sources  maven-status    surefire-reports
```