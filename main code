from tkinter import * 
from pytube import YouTube
import os

root = Tk()
root.geometry('800x800')
root.resizable(0,0)
root.title("Youtube to MP3 downloader")

#Setting some of the graphic elements and places to enter user input
Label(root,text = 'Youtube Video Downloader', font = ("Times New Roman", 22, "bold")).pack()
link = StringVar()

Label(root, text = 'Paste Link Here:', font = ("Times New Roman",  16,  "bold")).place(x= 320 , y = 60)
link_enter = Entry(root, width = 70,textvariable = link).place(x = 185, y = 90)

stream_num = StringVar() 
Label(root, text = 'Enter Stream:', font = ("Times New Roman", 16, "bold")).place(x= 330 , y = 645)
link_enter = Entry(root, width = 10,textvariable = stream_num).place(x = 332, y = 670)



temp_vids = None 

#Find the different Video Streams and lists them
def Stream_Finder(): 
    video_url =YouTube(str(link.get()))
    videos = video_url.streams.filter(only_audio=True)
    vid = list(enumerate(videos))
    for i in vid: 
        print(i)
        Label(root, text = i, font = ("Times New Roman", 8)).place(x= 70 , y = i[0]*30 + 150)
    print()
    return videos 

#Downloads the Selected Video based on the stream number inputed 
def Downloader(): 
    temp_vids = Stream_Finder() 
    download_stream = int(stream_num.get())
    downloaded_vid = temp_vids[download_stream].download()

    base, ext = os.path.splitext(downloaded_vid)
    downloaded_mp3 = base + '.mp3'
    os.rename(downloaded_vid, downloaded_mp3)

    print("Successfully donwloaded")
    Label(root, text = 'DOWNLOADED', font = ("Times New Roman", 16)).place(x= 325 , y = 710) 

#Defining Buttons to trigger the Stream_Finder() and Downloader() functions
Button(root,text = 'GET STREAMS', font = ("Times New Roman", 14, "bold") ,bg = 'sky blue', padx = 2, command = Stream_Finder).place(x=165 ,y = 650)
Button(root,text = 'DOWNLOAD', font = ("Times New Roman", 14, "bold") ,bg = 'sky blue', padx = 2, command = Downloader).place(x=490 ,y = 650)
root.mainloop()

