## **AI-PPT**

---

# 목차
1. 개요
    - 서비스 목적 및 배경
    - 서비스 설명
    - 서비스 구조
2. 유사 서비스 분석
3. 사용된 오픈소스 소프트웨어
4. DFD (Data-Flow-Diagram)

### RQ-트랜스포머

### 설명

39 억 개의 매개변수(파라미터)로 구성된 RQ-트랜스포머는 3000만 쌍의 텍스트-이미지를 학습한 텍스트-투-이미지(text-to-image) AI 모델로, 계산 비용을 줄이고 이미지 생성 속도를 높인 동시에 이미지의 품질을 크게 끌어올린 모델이다. 

이는 초거대 멀티 모달 인공지능(AI) 민달리(minDALL-E)의 업그레이드 버전으로, 기존의 민달리 대비 모델 크기는 3배, 이미지 생성 속도와 학습 데이터 셋 크기는 2배 늘림으로써 공개된 이미지 생성 모델 중 국내 최대 크기의 이미지 생성 모델이다.

### 특징

처음 보는 텍스트의 조합을 이해하고, 이에 대응하는 이미지를 생성할 수 있다. 예로 ‘사막에 있는 에펠탑(the Eiffel Tower in the desert)’이란 텍스트 조건을 입력하면 그에 알맞은 이미지를 생성한다.

고해상도 이미지를 2차원 코드맵으로 표현한 기존 기술과 달리, 3차원 코드맵으로 표현된 이미지를 순차적으로 예측해 생성하도록 했다.
RQ-트랜스포머는 이미지 압축에 따른 손실이 적어, 높은 품질의 이미지를 저해상도 코드맵으로 표현할 수 있다. 기존 이미지 생성 모델보다 적은 계산 비용과 높은 이미지 생성 속도를 달성할 수 있다.

### 참고

kakaobrain : [https://www.kakaobrain.com/contents?contentId=56634a7c-30c6-491a-be86-e0d57b982adf](https://www.kakaobrain.com/contents?contentId=56634a7c-30c6-491a-be86-e0d57b982adf)

카카오브레인, 이미지 생성 AI 모델 'RQ-트랜스포머' 공개 : [https://www.digitaltoday.co.kr/news/articleView.html?idxno=441815](https://www.digitaltoday.co.kr/news/articleView.html?idxno=441815)

적는 대로 그려준다, 카카오브레인이 만든 초거대 AI 모델 : [https://economist.co.kr/2022/04/19/it/general/20220419132937654.html](https://economist.co.kr/2022/04/19/it/general/20220419132937654.html)

github url : [https://github.com/kakaobrain/rq-vae-transformer](https://github.com/kakaobrain/rq-vae-transformer)

### 라이센스

The `source codes` are licensed under **[Apache 2.0]**(LICENSE.apache-2.0) License.

The `stage2 pretrained weights` are licensed under **[CC-BY-NC-SA 4.0]**(LICENSE.cc-by-nc-sa-4.0) License.

CC BY NC SA license (저작자 표시-비영리-동일조건변경허락)

- 저작물 ‧ 저작자명 및 출처, CCL 조건을 표시하면 자유롭게 이용할 수 있지만, 상업적으로는 이용할 수 없습니다.
- 상업적 이용을 원하면 저작권자와 별도의 계약이 필요합니다.
- 또한, 저작물을 이용하여 새롭게 저작물(2차적 저작물)을 제작하는 것은 허용하되, 새로운 저작물에 원 저작물과 동일한 라이선스를 적용해야 합니다.


### PptxGenJS

### 설명

This library creates Open Office XML (OOXML) Presentations which are compatible with Microsoft PowerPoint, Apple Keynote, and other applications.
이 라이브러리는 Microsoft PowerPoint, Apple Keynote 및 기타 응용 프로그램과 호환되는 Open Office XML (OOXML) 프레젠테이션을 만듭니다.

자바스크립트를 사용하여 웹 페이지에서 동작하게 하기 편하고, PPT파일 생성, 텍스트나 글상자등 각종 객체를 만들 수 있습니다. 그리고 마스터 슬라이드 편집까지 가능하기 때문에 템플릿을 수정하는 것도 가능합니다.

### 참고

Github : https://github.com/gitbrent/PptxGenJS

Official site : https://gitbrent.github.io/PptxGenJS

About master slide : https://gitbrent.github.io/PptxGenJS/docs/masters/

### About ppt_test.html

1.생성된 ppt를 열면 손상되었으니 복구~ 라고 뜨는데 복구 누르시면 됩니다

2.처음에는 이미지 파일 경로를 받아서 pptx를 만들려고 했는데 그렇게 하니까 브라우저의 보안 정책에 걸립니다(cors 정책) 브라우저에서 보안 정책을 건드릴 수 있긴 한데 일단 별도 작업 없이 돌아가게 하고 싶어서 input file에서 받은 파일을 base64로 변환한 뒤 사용하고 있습니다. 복구~ 뜨는 것도 아마 그거 때문일 겁니다

3.현재 구현된 부분은 이미지를 넣으면 그 이미지를 제목 슬라이드의 배경으로 하는 부분까지입니다

### License
MIT 라이센스입니다.

The MIT License (MIT)

Copyright (c) 2015-2022 Brent Ely

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

