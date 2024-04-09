import requests
from lxml import etree
import re
monv = ""
ai= 0
魔女_9 = ""
bilibili_all_list = []
header = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36"
}
url = 'https://www.bilibili.com/v/popular/rank/all'
resp = requests.get(url,headers=header)
text = resp.text
html = etree.HTML(text)
魔女 = html.xpath('//ul[@class="rank-list"]/li[@*]/div[@class="content"]/div[@class="info"]/a/text()')
爱 = html.xpath('//ul[@class="rank-list"]/li[@*]/div[@class="content"]/div[@class="info"]/div[@class="detail"]/span[@class="data-box"][1]/text()')
playlist = []
for target_listt in 爱:
    playlist.append(re.sub('\n|\s','',target_listt)) 
#print(playlist)
titlelsit = []
for target_listt in 魔女:
    titlelsit.append(target_listt)
#print(titlelsit)
#魔女.append()
#int(魔女)
#for target_list in zip(titlelsit,playlist):
    
for target_listt in 魔女:
    ai = ai+1
    monv = ("monvai魔女"+str(ai)+(target_listt)+"\n")
    魔女_9 = (魔女_9+monv)
#with open(r"./db_text.txt","w",encoding="utf-8"):
#f.weite(魔女_9)
#import pandas as pd
#data = pd.Dataframe(data=魔女_9,columns=[排名])
#data.to_excel(r"./db.text.xlsx",encoding="utf-8")
_bilibili_video_nameAndnum = []
for _bilibili_video_name,_bilibili_video_play_num in zip(titlelsit,playlist):
    _bilibili_video_nameAndnum=[_bilibili_video_name,_bilibili_video_play_num]
    bilibili_all_list.append(_bilibili_video_nameAndnum)
print(bilibili_all_list)
ccc = ""
for _target_id in bilibili_all_list:
    ccc = ccc +str(_target_id) +"\n"
f = open("./魔女.txt","w",encoding="utf-8")
f.write(ccc)
f.close()
