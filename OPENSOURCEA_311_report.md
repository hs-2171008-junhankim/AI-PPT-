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

# 1. 개요

- 서비스 목적 및 배경

   중요한 발표 자리에서 PPT의 사용은 빈번하다. 그때마다 우리는 PPT에 사용할 템플릿을 고민해야 한다. 인터넷에서 특정 키워드를 검색하여 주제에 맞는 템플릿이 찾아지는 경우에는 그대로 사용하면 되겠지만 찾는데까지 시간이 걸린다는 불편함이 있다. 그리고 주제가 독특한 경우나 한 단어로 표현할 수 없는 주제의 경우에는 적합한 템플릿을 찾기가 어려울 수 있다.  이러한 문제를 해결하고자 본 서비스는 주제에 맞는 PPT 템플릿을 바로 얻을 수 있는 웹 서비스를 제작하게 되었다.

- 서비스 설명

   사용자는 PPT 템플릿을 만들고 싶을 때 본 서비스를 제공하는 웹 사이트에 방문한다. 사용자는 PPT 템플릿에 사용될 키워드를 주제에 대한 설문조사를 진행한다. 만약, 설문조사 결과가 이전의 사용자들과 비슷한 결과로 나타난다면 중간 단계 없이 템플릿을 추천받는다. 사용자가 원하는 템플릿이 없거나 이전의 사용자들과는 다른 설문결과가 나올 경우, 사용자는 AI가 설문결과를 토대로 만든 이미지들 중 원하는 분위기의 이미지를 선택하게 되고 그 이미지를 이용하여 PPT 템플릿을 제공한다.

- 서비스 구조

   먼저, 사용자는 원하는 디자인에 대한 설문조사를 진행한다. 설문결과는 텍스트 형태로 Tensorflow에 전송되고 Text-Classification을 통해 텍스트가 분석되며 설문조사 결과 DB에 전송된다. Tensorflow는 사용자가 원하는 템플릿이 기존 사용자가 사용한 템플릿과 같을 경우 설문조사 DB에서 이미지를 가져와 즉시, PptxGenJS를 통해 템플릿을 제공한다. 사용자가 원하는 템플릿이 기존에 제공된 적 없는 템플릿이라면, 설문결과를 Robotstxt에 전송하여 키워드를 크롤링하고 관련된 키워드들을 바탕으로 RQ-transformer가 관련된 이미지들을 생성한다. 생성된 이미지들은 Go-survey에 전송되어 사용자가 원하는 이미지를 선택할 수 있도록 한 번더 설문조사가 진행된다. 사용자가 이미지를 선택하면, 선택한 이미지를 PptsGenJS에 전송하여 템플릿을 만들어 제공한다. 동시에 생성된 이미지들을 Classify-images에 전송하여 분류하고 설문조사 결과 DB에 전송하여 DB를 계속해서 업데이트 한다.

# 3. 사용된 오픈소스 소프트웨어

### TensorFlow

### 설명

   기존 사용자들이 원했던 템플릿과 같은 템플릿을 원하는 것 같을 때 템플릿을 추천해주는 용도로 사용한다.

tensorflow는 graphs의 형태로 나타내는 프로그래밍 시스템을 말한다. 그래프에 있는 노드들은 operations이라고 불리우는데, 줄여서 ops라고 칭한다. op는 Tensor로 이루어져 있고, tensors간에 computaiton을 수행하게 된다. tensor는 multi-dimentional array형태로 되어있다. Tensorflow graph를 연산하기 위해서는 Session을 launch를 해야한다. Session은 Devices(CPUs, GPUs)위에서 연산을 실행한 후에 결과를 반환한다.

### 특징

   ML 모델을 개발학 학습시키는 데 도움이 되는 핵심 오픈소스 라이브러리를 제공한다.
즉각적인 모델 반복 및 손쉬운 디버깅을 가능하게 하는 즉시 실행 기능이 포함된 Keras와 같은 높은 수준의 직관적인 API를 사용하여 ML 모델을 쉽게 빌드하고 학습한다.

### 출처 및 참고

[https://ourcstory.tistory.com/236](https://ourcstory.tistory.com/236)

[https://joochang.tistory.com/102](https://joochang.tistory.com/102)

[https://github.com/tensorflow/tensorflow/blob/master/LICENSE](https://github.com/tensorflow/tensorflow/blob/master/LICENSE)

### 라이센스

● Apache license 2.0
복제, 배포, 수정의 권한 허용 : 가능
배포시 라이선스 사본 첨부 : 가능
저작권 고지사항 또는 Attribution 고지사항 유지 : 가능
배포시 소스코드 제공의무(Reciprocity)와 범위 : 명시되어있지않음
조합저작물(Lager Work) 작성 및 타 라이선스 배포 허용 : 가능
수정 시 수정내용 고지 : 명시되어있지않음
명시적 특허 라이선스의 허용 : 가능
라이선시가 특허소송 제기 시 라이선스 종료 : 명시되어있지않음
이름, 상표, 상호에 대한 사용제한 : 가능
보증의 부인 : 가능
책임의 제한 : 가능

### robotstxt

### 설명

robots.txt는 웹사이트에서 크롤링하며 정보를 수집하는 검색엔진 크롤러(또는 검색 로봇)가 액세스 하거나 정보수집을 해도 되는 페이지가 무엇인지, 해서는 안 되는 페이지가 무엇인지 알려주는 역할을 하는 .txt (텍스트) 파일이다. robots.txt 파일은 검색엔진 크롤러가 웹사이트에 접속하여 정보 수집을 하며 보내는 요청(request)으로 인해 사이트 과부하되는 것을 방지하기 위해 사용된다. robots.txt에서 액세스가 허용하지 않은 디렉토리를 발견하면 크롤링을 하지않는다

### 사용방법

<aside>
💡 User-agent: *
Disallow: /forbidden/


</aside>

1. **User-agent**: robots.txt 에서 지정하는 크롤링 규칙이 적용되어야 할 크롤러를 지정합니다.
2. **Allow**: 크롤링을 허용할 경로입니다 (/ 부터의 상대 경로).
3. **Disallow**: 크롤링을 제한할 경로입니다 (/ 부터의 상대 경로).
4. **Sitemap**: 웹사이트의 모든 리소스를 나열한 목록 파일입니다.

### 참고

Github : [https://github.com/google/robotstxt](https://github.com/google/robotstxt)

About Robots.txt : [https://developers.google.com/search/docs/crawling-indexing/robots/intro](https://developers.google.com/search/docs/crawling-indexing/robots/intro)

### 라이센스

Apache License
Version 2.0, January 2004
[https://www.apache.org/licenses/](https://www.apache.org/licenses/)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at [https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

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

### classify-images

### 설명
사용자가 키워드를 포함하는 파일을 업로드해서 알고리즘이 이미지 내용에 따라 각 이미지에 키워드를 할당하여 이미지를 분류한다.

### 특징
주어진 태그로 이미지를 분류하기 위한 웹 앱이다.
이 애플리케이션은 프론트엔드와 백엔드로 구성된다.
프런트엔드는 React 및 rsuite, axios 및 particle.js와 같은 패키지를 사용하여 구현된다.
백엔드는 OpenAi의 CLIP 모델을 배포하여 제로샷 파일 분류, 비디오 검색 및 이미지 검색을 수행한다.

### 참고
github : https://github.com/Cameramorphic/classify-images
OpenAi의 CLIP 모델 : https://github.com/openai/CLIP

### License

MIT License

Copyright (c) 2021 Höhing, Nils; Rittenschober, Johann; Schuschnig, Ricarda; Schwarzer, Tobias;

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