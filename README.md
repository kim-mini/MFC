# MFC 공부 기록

`enum` : 변수들을 열거해 놓는다

```cpp
// typedef : 별칭을 붙여 준다

typedef enum func{
  EXAMPLE_ONE // assingned 0
  EXAMPLE_TWO // assingned 2
}F;
```

`MmodDefine` : 모델 정의하는 함수

```cpp

MmodDefine( 모델버퍼, 타입, 원본이미지, 좌표x, 좌표y, x길이, y길이)

```

`MimOpen` : 영역을 이치화처리를 하고 작은 잡음들을 제거해준다 

`MimBinarize` : 영상을 이진화해서 배경픽셀을 0, blob픽셀을 다른 값으로 나타낸다

`MbufExport` : 데이터를 파일로 저장하기 위한 함수

```cpp

MbufExport(FileName, FileFormat, SrcBufId);

```

  -  파일이름
  -  파일포멧
  -  저장할 이미지버퍼


### 선그리기

`CreatePen` : 선을 만드는 함수

```cpp

CreatePen(pen style, width, color)

```

  - 선의 종류 : PS_SOLID, PS_DASH, PS_DASHDOT, PS_DASHDOTDOT, PS_NULL
  - 선의 굵기
  - 선의 색깔

`oldpen` = pDC->SelectObject(&pen); : 펜을 DC에 등록

`MoveTo (x, y)` : 현재 포지션을 특정한 좌표(x, y)로 이동

`LineTo (x, y)` : 현재 포지션에서 (x, y)좌표까지 선을 그림 

`pDC->SelectObject();` : DC를 아용해 펜을 원위치로 돌려놓는다

  - `GDI`는 `Graphic Device Interface`이다 (그래픽 장치 접근 혹은 접속) GDI는 `화면에 어떠한 접근하는 것을 담당`하는데 (화면에 글을 쓰거나 그림을 넣거나 하는 행동)
  - `DC`는 `Device Context`이다 (장치 내용 혹은 관계) `GDI를 추상화한 것이 DC`
  
`pen.DeleteObject();` : 사용이 완료된 펜 삭제

---

`MappTimer` : 시간을 측정하는 함수

코드가 돌아가는데 걸리는 시간을 측정하는 코드

```cpp   

MappTimer(M_TIMER_RESET, M_NULL);

/*이곳에 시간측정 대상이 되는 프로세스가 들어간다.*/

MappTimer(M_TIMER_READ, &Time);

```

`sprintf (str, "string")` : 문자열에 서식문자열을 저장한다

`fprintf (fp, "string")` : fp가 가르키는 파일에다가 문자열 쓰기

`GetLocalTime` : 현재의 시간을 받을 수 있는 함수

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME, *LPSYSTEMTIME;

// 사용할 떄는 변수의 주소를 넣어준다
GetLocalTime(&systime)
systime.wYear // << 이런식으로 쓰면 년도가 출력이 된다
```

---

## 처음 초기화 설정할 때 버튼의 글자 컨트롤 하기

```cpp
GetDlgItem( 버튼ID )->SetWindowTextW( TEXT );
```

## 다이알로그창 종료

```cpp
AfxGetMainWnd()->PostMessage(WM_CLOSE);
```
## 체크박스 체크 여부 확인

```cpp
((CButton*)GetDlgItem( 버튼ID ))->GetCheck()
```

  - 체크가 되어있으면 `TRUE`
  - 체크가 안되어있으면 `FALSE`를 반환한다

## Grid control

그리드 컨트롤 창을 만들어서 `row`, `column`을 지정하여 레이아웃을 만들 수 있다
