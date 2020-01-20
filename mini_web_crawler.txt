# -*- coding: utf-8 -*-
"""
Created on Mon Jan 20 23:56:55 2020

@author: Sourav Saraf
"""

import urllib.request,urllib.parse,urllib.error
from bs4 import BeautifulSoup
import ssl
ctx=ssl.create_default_context()
ctx.check_hostname=False
ctx.verify_mode=ssl.CERT_NONE

url=input("Enter URL:-")
position=int(input("Enter position of the url in the list:-"))
count=int(input("Enter the number of times you want to repeat the process:-"))
for i in range(count):
    html=urllib.request.urlopen(url,context=ctx).read()
    soup=BeautifulSoup(html,'html.parser')
    
    u=[]
    t=[]
    tags=soup('a')
    for tag in tags:
        x=tag.get('href',None)
        u.append(x)
        t.append(tag.text)
    url=u[position-1]
print("\nYour result is:-",t[position-1])