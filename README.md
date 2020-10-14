# ffmpegStreamming

## 비디오 파일 스트리밍 전송하기  
- c:/에 ffmpeg 설치 후, 환경변수 설정 path에 c:/ffmpeg/bin을 추가할 것
- mkv, mp4 파일 스트리밍 테스트 완료  
- 스트리밍 서버 켜기  
```
./rtsp-simple-server
```

- 스트리밍 서버에 원하는 파일 반복으로 스트리밍 하기  
```
ffmpeg -re -stream_loop -1 -i file.ts -c copy -f rtsp rtsp://localhost:8554/mystream
```

- 스트리밍 되는 영상 보기  
```
ffplay rtsp://localhost:8554/mystream
```
[참조 링크(github)](https://github.com/aler9/rtsp-simple-server)  


- 스트리밍 서버에 원하는 파일 한 번 스트리밍 하기  
```
ffmpeg -re -i d:\source.mkv -c copy -f rtp_mpegts rtp://127.0.0.1:9000
```

- 스트리밍 되는 영상 보기  
```
ffplay rtp://127.0.0.1:9000
```


## 웹캠 스트리밍 하기  
- 연결된 웹캠 이름 확인하기  
```
ffmpeg -list_devices true -f dshow -i dummy  
```
- ffmpeg로 rtsp 서버에 스트리밍하기 1  
```
ffmpeg -f dshow -rtbufsize 64M -i "HD Pro Webcam C920" -s 320x200 -f rtp_mpegts rtp://127.0.0.1:9000
```

- ffplay로 스트리밍 보기 1  
```
ffplay rtp://127.0.0.1:9000
```

- ffmpeg로 rtsp 서버에 스트리밍하기 2  
```
ffmpeg -f dshow -i video="HD Pro Webcam C920" -f rtsp -rtsp_transport tcp rtsp://localhost:8554/visual
ffmpeg -f dshow -video_size 1920*1080 -i video="HD Pro Webcam C920" -f rtsp -rtsp_transport tcp rtsp://localhost:8554/visual
```

- ffplay로 스트리밍 보기 2  
```
ffplay rtsp://localhost:8554/visual
```
- 브라우저에서 보려면 주소창에 rtsp 주소만 넣으면 됨  

[ffmpeg 설명서](https://trac.ffmpeg.org/wiki/EncodingForStreamingSites)  
[참조 링크 1](https://icodebroker.tistory.com/6350)  
[참조 링크 2](https://icodebroker.tistory.com/6351)
[참조 링크 3](https://realapril.tistory.com/41)  
[ffmpeg 사용법](https://peche326.tistory.com/58)   
[유튜브 다운로드](https://mrs0m30n3.github.io/youtube-dl-gui/)  
