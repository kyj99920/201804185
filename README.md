# 201804185
import nltk
from konlpy.tag import Twitter
from wordcloud import WordCloud, STOPWORDS
from PIL import Image
from bs4 import BeautifulSoup
import urllib
from urllib.request import urlopen
import warnings; warnings.filterwarnings('ignore')
import matplotlib
matplotlib.rc('font', family='Malgun Gothic')
import matplotlib.pyplot as plt
import time

tmp1 = 'https://search.naver.com/search.naver?where=kin&sm=tab_jum&query=%EB%A7%88%EC%BC%93%EC%BB%AC%EB%A6%AC'
html = tmp1 + '&grade=0&choice=0&sec=0&nso=so%3Ar%2Ca%3Aall%2Cp%3Aall&query={input}&c_id=&c_name=&sm=tab_pge&kin_start={n}'
openurl = urlopen(html.format(input=urllib.parse.quote('신종 코로나'), n=1))
soup = BeautifulSoup(openurl, 'html.parser')
tmp = soup.find_all('dl')

tmp_list = []
for line in tmp:
    tmp_list.append(line.text)
