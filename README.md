# SkinAnalyzer_Python

## 주요기능

- python3.8 + opencv 를 사용하여 피부의 모공, 잡티, 주름을 검출 
- flask 서버를 만들어 request 가 오면 분석 결과를 return

## 수행역할
- 설계 및 총 제작

## 사용한 기술
- `cv2`, `dlib`, `flask`

## 대략적인 구현 알고리즘
``` python
# 모공검출

self.adjust_gamma(img,0.2)                      # 1.감마값조절
cv2.cvtColor(_, cv2.COLOR_BGR2GRAY)             # 2.그레이체널화
self.adaptive_his_streching(_)                  # 3.어댑티브 히스토그램 명암대비
cv2.Laplacian(_, cv2.CV_8U, ksize=_)            # 4. 라플라시안 경계값 검출
cv2.subtract(_, _)                              # 5.스트레칭값 - 라플라시안 값
cv2.bitwise_not(_)                              # 6.이미지 반전
cv2.morphologyEx(_, cv2.MORPH_TOPHAT, kernel)   # 7. 탑햇연산
cv2.morphologyEx(_, cv2.MORPH_BLACKHAT, kernel) # 8. 블랙햇연산
cv2.dilate(_,_,iterations=1)                    #
cv2.erode(_,_,iterations=1)                     # 9. 열림연산
cv2.threshold(_, _, _, cv2.THRESH_BINARY)       # 10. 이진화
self.check_eccen3(thresh2, 1, 200, 0.7)         # 11. 타원형체크 (결과값이 원형에 가까운지 검출)

```

