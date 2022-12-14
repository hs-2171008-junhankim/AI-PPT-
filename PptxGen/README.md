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