# FFMPEG-QURIES

https://superuser.com/questions/1761958/ffmpeg-error-when-i-use-2-videos-this-command-works-well-but-when-i-give-more

ffmpeg  -i out1.mp4 -i out2.mp4 -i out3.mp4 -filter_complex "[0:v][1:v]xfade=radial:duration=3:offset=6.006009000000001 [x1],[1:v][2:v]xfade=dissolve:duration=3:offset=14.030023 [x2],[0:a]adelay=0|0 [a1],[1:a]adelay=6006.009|6006.009 [a2],[2:a]adelay=11524.014000000001|11524.014000000001 [a3],[a1][a2][a3]amix=inputs=3 [fina],[x2][fina]concat=n=1:v=1:a=1:unsafe=1 [video][audio]" -map "[video]" -map "[audio]"  -pix_fmt yuv420p  -y trans.mp4

  ABOVE COMMAND GENERATES ERROR  :  Filter xfade:default has an unconnected output
  
  WHAT DOES IT MEAN ?

ZOOM IN & STAYS & OUT , BUT DIDN'T WORK

ffmpeg  -loop 1 -t 60 -i ERR1.PNG -filter_complex "[0:v]zoompan=z='if(between(in_time,15,25),min(zoom+0.05,1.5),1.3)':d=900:x='if(gte(zoom,1.5),x,x+10)':y='if(gte(zoom,1.5),y,y-2)':s=1280x720 [out];[out]zoompan=z='if(between(in_time,35,40),max(zoom-0.05,1),1)':d=900:x='if(lte(zoom,1.5),x,x-10)':y='if(lte(zoom,1.5),y,y+2)':s=1280x720 [out1];[out1]trim=duration=40 [trim],[trim]setpts=N/FRAME_RATE/TB [v]"  -map "[v]"  -c:v libx264  -y output.mp4 

