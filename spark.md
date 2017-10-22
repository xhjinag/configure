# spark

## 需要jdk(略)

## 需要hadoop，见[hadoop安装](hadoop.md)

## 需要scala

1. 可以使用apt源里的scala

```bash
sudo apt install scala
```

2. 可以去[官网](https://www.scala-lang.org/download/)下载最新版本的scala

解压并拷贝到/usr/share/目录下

```bash
sudo cp -r scala-2.12.4 /usr/share/
```

使用update-alternatives安装并配置scala，

```bash
sudo update-alternatives --install /usr/bin/scala scala /usr/share/scala-2.12.4/bin/scala 100
sudo update-alternatives --config scala
# 如果有多个版本的scala，进行选择配置
```

## 安装spark

去[官网](https://spark.apache.org/downloads.html)下载并解压spark到/opt目录(个人喜好，自行安装的软件放在了/opt目录)，对spark-\*.\*.\*-bin\*文件夹建立软链接到/opt/spark，便于日后更新版本

* 环境变量
```bash
export PATH="/opt/spark/bin:$PATH"
```

## 测试
启动hadoop，打开spark-shell
```
start-dfs.sh
```
# 建立测试用的文件input.txt
> people are not as beautiful as they look, 
> as they walk or as they talk.
> they are only as beautiful  as they love, 
> as they care as they share.
![input.txt](image/spark/0.png)
```bash
spark-shell
# 以下为spark-shell中操作
scala> val inputfile = sc.textFile("input.txt")
scala> val counts = inputfile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey(_+_);
scala> counts.saveAsTextFile("output")
# 打开output文件夹查看输出
cat output/part-*
```
![spark-shell](image/spark/1.png)
![output](image/spark/2.png)

