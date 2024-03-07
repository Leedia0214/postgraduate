## BRTV-微博爬虫指南

##### 前提准备:

userlistid名单.txt

weibopostprocess

微博爬虫github

##### 操作：

1、将“微博爬虫github”里的weibo文件夹删去

2、

2.1：将“微博爬虫github”里userid_list.txt的内容换成templsit.txt的内容；

2.2：打开config.json：调整下面两个时间，设为周四到周三；

```
"since_date": "2024-3-1",
"end_date": "2024-3-6",
```

2.3：如遇cookie失效：

1. 用Chrome打开https://passport.weibo.cn/signin/login；
2. 输入微博的用户名、密码，登录， 登录成功后会跳转到[https://m.weibo.cn](https://m.weibo.cn/);
3. 按F12键打开Chrome开发者工具，在地址栏输入并跳转到[https://weibo.cn](https://weibo.cn/)，
4. 依此点击Chrome开发者工具中的Network->Name中的weibo.cn->Headers->Request Headers，"Cookie:"后的值即为我们要找的cookie值，复制即可

3、进入“微博爬虫github”，在控制台中输入：

```
python -m weibo_spider
```

3.1：可能无法一次全部运行成功，可以每次选中30-40个数据进行爬取

3.2：如果没有成功执行完毕，等程序自己运行完毕，删除userid_list.txt里前几个已执行的内容（数字编号后有人名的），再次执行代码`python -m weibo_spider`，直至全部运行成功。

4、待全部运行成功后，“微博爬虫github”里的weibo文件夹替换到“weibopostprocess”内

5、进入“weibopostprocess”，在控制台中输入：

```
python postprocess.py
```

6、“weibopostprocess”文件夹里的csv文件即为所求。

