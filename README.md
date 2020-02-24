# Mason
Self-study AI
#!/usr/bin/python
#-*-coding:utf-8-*-
import re
import requests
q=requests.get(url='http://www.doutula.com/photo/list/?page=31')
d=q.content.decode(encoding='utf-8')
# print(d)
r1=re.compile(r'data-original="(.*?)" alt="(.*?)"' )
data=re.findall(r1,d)
# print(data)
for i in data:
urls=[]
urls.append(i[0])
# print(urls)
for j in urls:
req = requests.get(url=f'{j}')
jiegou = req.content
f = open(file=f'C:/Users/WFT/Desktop/斗图啦/{i[1]}.gif', mode='wb')
f.write(jiegou)
print(f'{i[1]}.gif')

