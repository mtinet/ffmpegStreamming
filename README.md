# ffmpegStreamming

## 비디오 파일 스트리밍 전송하기  
- c:/에 ffmpeg 설치 후, 환경변수 설정 path에 c:/ffmpeg/bin을 추가할 것
- mkv, mp4 파일 스트리밍 테스트 완료  
```
ffmpeg -re -i d:\source.mkv -c copy -f rtp_mpegts rtp://127.0.0.1:9000
```
```
ffplay rtp://127.0.0.1:9000
```

## 웹캠 스트리밍 하기  
- 웹캠 이름 확인하기  
```
ffmpeg -list_devices true -f dshow -i dummy  
```
- ffmpeg로 rtsp 서버에 스트리밍하기  
```
ffmpeg -maxrate 800k -bufsize 3000k -f dshow -i video="HD Pro Webcam C920" -f rtsp -rtsp_transport tcp rtsp://localhost:8554/visual
```
- ffplay로 스트리밍 보기  
```
ffplay rtsp://localhost:8554/visual
```
- 브라우저에서 보려면 주소창에 rtsp 주소만 넣으면 됨  


[참조 링크 1](https://icodebroker.tistory.com/6350)  
[참조 링크 2](https://realapril.tistory.com/41)  
