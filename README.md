## ESP32-Cam timelapse
Esp32-cam will take a picture and go to a deep sleep mode for next 30 seconds. Gap between two pictures is about 38 seconds. 
The pictures will be saved in directories named dir1, dir2, etc for each session. It will create new directory when it's started or at reset.

# Steps
1. Upload the code to esp32-cam using arduino ide(make sure you have added esp32 boards in arduino ide).
2. Deploy the esp32-cam where you want to take pictures.
3. After you get the pictures, copy the pictures to a directory and run following commands
```
printf "file '%s'\n" *.jpg | sort -V > fraglist.txt
ffmpeg -f concat -i fraglist.txt -framerate 30 -c:v libx264 -pix_fmt yuv420p out.mp4
```
You can change the framerate as per your need, I've choosen 30.
