# week01
from requests_html import HTMLSession

session = HTMLSession()

r = session.get('https://python.org/')

get函数+函数

### 获取页面上的所有链接。
all_links =  r.html.links
print(all_links)

### 获取页面上的所有链接，以绝对路径的方式。
all_absolute_links = r.html.absolute_links

print(all_absolute_links)


## **举例** 

rom requests_html import HTMLSession


session = HTMLSession()

r = session.get("https://news.cnblogs.com/n/recommend")

### 通过CSS找到新闻标签

news = r.html.find('h2.news_entry > a')

for new in news:

    print(new.text)  # 获得新闻标题

    print(new.absolute_links)  # 获得新闻链接


# 实例
# 00: 使用...

from requests_html import HTMLSession

# 01: 使用session

session = HTMLSession()

r = session.get("https://news.cnblogs.com/")

# 02: 使用.find ???? (CSS selector; r.html.find)

# 通过CSS找到新闻标签

news = r.html.find('h2.news_entry > a')

# 03: 结果輸出

for new in news:

    print("标题:", new.text)  # 获得新闻标题

    print("链接:", new.absolute_links)  # 获得新闻链接

> 尽量选用一些文字和图片比较整齐的图文列表

## 第二组
from requests_html import HTMLSession

session = HTMLSession()


r = session.get("https://www.liepin.com/zhaopin/?key=python")


# 通过xpath找到工作标签

news = r.html.xpath('//div[@class="job-info"]/h3/a')

#             以下所有^^   [@attribute]條件  

for new in news:

    print("工作",new.text)  # 获得工作标题

    print("工作",new.absolute_links)  # 获得工作链接


## 第三组

挖掘图片

1、from IPython.core.display import display, HTML


display(HTML('<img src="https://httpstatusdogs.com/img/418.jpg" alt="">'))


2、from IPython.core.display import display, Markdown


display(Markdown('![](https://httpstatusdogs.com/img/418.jpg)'))


3、from requests_html import HTMLSession


from IPython.core.display import display, Markdown

session = HTMLSession()

r = session.get("https://cn.bing.com/images/trending")

# 通过xpath找到工作标签
items = r.html.xpath('//img/@src')

for url in items:
    print(url)  # 获得图片src url
    display(Markdown('![]({url})'.format(url=url)))  # 展示图片 



















