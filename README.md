# MFC공부 기록

MmodDefine : 모델 정의하는 함수

```cpp

MmodDefine( 모델버퍼, 타입, 원본이미지, 좌표x, 좌표y, x길이, y길이)

```

MimOpen : 영역을 이치화처리를 하고 작은 잡음들을 제거해준다 

MimBinarize : 영상을 이진화해서 배경픽셀을 0, blob픽셀을 다른 값으로 나타낸다

MbufExport : 데이터를 파일로 저장하기 위한 함수

```cpp

MbufExport(FileName, FileFormat, SrcBufId);
// 파일이름, 파일포멧, 저장할 이미지버퍼

```
