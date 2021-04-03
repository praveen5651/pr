# send bulk messages on whatsapp
import pyautogui as pg
import webbrowser as web
import time
import pandas as pd
data=pd.read_csv("give excel file path")

data_dict=data.to_dict('list')
numbers=data_dict['numbers']
messages=data_dict['message']
combo=zip(numbers,messages)
first=True
for numbers,messages in combo:
    time.sleep(4)
    web.open('https://web.whatsapp.com/send?phone='+numbers+'&text='+messages)
    if first:
        time.sleep(6)
        first=False
    width,height=pg.size()
    pg.click(width/2,height/2)
    pg.press('enter')
    time.sleep(8)
    pg.hotkey('ctrl','w')
