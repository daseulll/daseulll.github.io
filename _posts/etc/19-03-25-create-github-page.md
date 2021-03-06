---
layout: post
title: "windows 10에서 jekyll로 github-page 만들기"
date:   2019-03-25 23:27:32 +0900
categories: jekyll
---

드디어 jekyll로 github page를 만드는 데 성공했다.

window 환경에서 잘 안되는 것들이 꽤 있어서 힘들 때가 있다.

티스토리에 블로그를 기존에 운영했었지만, 코드블럭을 삽입하는 데 개인적으로 번거롭다고 느껴서 github page로 이전하고 싶었다. 마크다운이 훨씬 편리하다고 생각한다.



**참고
[마크다운문법](https://wikidocs.net/1678)
[마크다운 문법1](https://gist.github.com/ihoneymon/652be052a0727ad59601)
[마크다운 문법2](https://simhyejin.github.io/2016/06/30/Markdown-syntax/#code-blocks)**

<br>


강의를 들을 때는 MS의 onenote를 사용하는데, 여기에 쌓인 필기가 정말로 많다.. 이제라도 틈틈이 자주 정리하여 블로그에 업로드 하고 싶다.

평소에 [초보몽키의 개발공부로그](https://wayhome25.github.io/)를 자주 참고하는데, 해당 페이지가 간결하면서도 원하는 내용을 쉽게 한눈에 파악 할 수 있어서 해당 블로그에서 적용한 [codinfox-lanyon](http://jekyllthemes.org/themes/codinfox-lanyon/) jekyll theme를 적용했다.


---

### Window 10 home 환경에서 jekyll 테마 적용하기


처음 windows 10 home환경에서 github page를 생성하려고 했을 때, 많은 블로그 튜토리얼을 따라했지만 하루를 꼬박 쓰고도 성공하지 못했다. jekyll 공식문서와 여러 블로그들을 참고해서 계속 시도해서 나의 운영환경에는 가장 효과적이고 github page를 만드는데 도움이 되었던 두개의 글을 발견했다.

블로그 생성은 hurderella님이 정리하신 [windows에서 github page와 jekyll로 블로그 생성하기](https://hurderella.tistory.com/131)에 큰 도움을 받았다.


테마 적용은 junhobaik님의 [Jekyll 블로그 테마 적용하기](https://junhobaik.github.io/jekyll-apply-theme/)를 참고했다.


만약 codinfox-lanyon 테마를 적용하면 jekyll-paginate 에러가 발생하는 경우가 있는데,

```
  gem "jekyll", "~> 3.8.5" (삭제)
  gem "jekyll-paginate"
```

Gemfile의 `gem "jekyll"`를 삭제하고, 그 아래 줄에 `gem "jekyll-paginate"`를 추가한다.

그리고 `gem "github-pages", group: :jekyll_plugins`가 주석처리 돼있는 것을 해제한다.

`bundle update`후,

`_config.yml` 파일의 gems를 plugins로 바꿔준다.

이렇게 할 경우 잘 해결되었다.


<br>
마크다운 글꼴과 색상도 변경하고 싶은데, 차차 적용해 봐야 겠다.
