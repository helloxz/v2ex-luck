# v2ex-luck

V2EX T楼抽奖

## 使用方法

首先通过浏览器F12工具获取HTML节点，

![](https://img.rss.ink/imgs/2022/04/08/fe293aabe7508979.png)

```html
<div class="box">
...
</div>
```

然后将HTML内容存到一个文本中，比如`v2ex.txt`



最后使用shell随机抽取3名幸运用户：

```bash
grep -oh 'member/.*</a>' v2ex.txt|grep -v "xiaoz"|grep -v "@"|grep -oh ">[a-zA-Z0-9]*<"|grep -o "[a-zA-Z0-9]*"|uniq|shuf -n3
```

1. 正则筛选出所有楼层用户

2. 去除自己的楼层账号`xiaoz`

3. `uniq`去重重复楼层的用户

4. `shuf`随机去除3行作为幸运用户



![](https://img.rss.ink/imgs/2022/04/08/a63f5897e74e4885.png)
