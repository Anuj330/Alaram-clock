# Alaram-clock

from tkinter import *
from tkinter import Label , Tk
from datetime import datetime
from playsound import playsound
import time 

clock = Tk() 
clock.title("Digital Clock") 
clock.geometry("1050x450") 

text_font= ("Boulder", 68, 'bold')
background = "Purple"
foreground= "white"
border_width = 15

label = Label(clock, font=text_font, bg=background, fg=foreground, bd=border_width  ) 
label.grid(row=0, column=1)

def digital_clock(): 
   now = time.strftime("%H:%M:%S")
   label.config(text=now) 
   label.after(200, digital_clock)
   label.pack()

def Alarm_time(set_an_time):

    while True:
        time.sleep(1)
        current_time = datetime.now()
        now_hour = current_time.strftime("%H")
        now_minute = current_time.strftime("%M")
        now_second = current_time.strftime("%S")
        #print("The Set Date is:",date)
        print(current_time)
        if now_hour == hour.get():
            if now_minute == min.get():
                if now_second == sec.get():
                    print("Time to Wake up")
                    playsound("Alarm.mp3")
                    break
def actual_time():
    set_an_time = f"{hour.get()}:{min.get()}:{sec.get()}"
    Alarm_time(set_an_time) 


time_format=Label(clock, text= "Enter time in 24 hour format!", fg="white",bg="blue",font="Arial").place(x=60,y=120)
addTime = Label(clock,text = "Hour    Min        Sec  ",font=60).place(x = 110)
setYourAlarm = Label(clock,text = "When to wake you up",fg="blue",relief = "solid",font=("Helevetica",9,"bold")).place(x=220, y=75)

hour = StringVar()
min = StringVar()
sec = StringVar()


hourTime= Entry(clock,textvariable = hour,bg = "pink",width = 15).place(x=110,y=30)
minTime= Entry(clock,textvariable = min,bg = "pink",width = 15).place(x=150,y=30)
secTime = Entry(clock,textvariable = sec,bg = "pink",width = 15).place(x=200,y=30)

submit = Button(clock,text = "Set Alarm",fg="red",width = 10,command = actual_time ).place(x =110,y=70)

digital_clock()
clock.mainloop()

