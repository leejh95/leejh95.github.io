---
date: 2022-11-11 15:32:43 +0900
title: Github 블로그에 Giscus로 댓글 기능 추가하기
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos, giscus] ## Only lowercase
---

## 시작
---
Github 블로그에 댓글 기능을 추가해보겠습니다.

## 어떤 서비스를 사용할까?
---
Github Pages는 DB를 지원하지 않기 때문에 따로 외부 서비스와 연동해서 사용해야 하는데요. 다음과 같이 여러가지 서비스가 있습니다.

- [discus](https://disqus.com/)
- [utterances](https://utteranc.es/)
- [giscus](https://giscus.app/ko)

각각 장단점이 있는데요, 이 중에서 저는 Giscus를 사용해보겠습니다.

## Giscus
---
> #### [__Giscus__](https://giscus.app/ko)
> ---
> [GitHub Discussions](https://docs.github.com/en/discussions)로 작동하는 댓글 시스템입니다. GitHub를 이용해 방문자가 댓글과 반응을 웹사이트에 남기게 해보세요! [utterances](https://github.com/utterance/utterances)에서 큰 영감을 받았습니다.

Github Discussions는 Github에서 제공하는 기능으로, Github 레포지토리에 대한 질문, 토론, 공지 등을 할 수 있는 기능입니다. giscus는 자신의 블로그 페이지에서 Github Discussions를 댓글처럼 사용할 수 있도록 해주는 서비스입니다.

마침 제 블로그는 제 Github 공개 저장소를 Github Pages로 호스팅하고 있기 때문에 딱 좋은 것 같아서 사용해보기로 했습니다.

## 설치 및 적용
---
다행히도 giscus는 [__공식 한국어 설명서__](https://giscus.app/ko)가 있습니다! 그냥 문서에 나온대로 따라하시면 쉽게 적용할 수 있습니다.

다만, 조금 헷갈리는 부분이 있을 수도 있으니 제가 적용한 방법을 설명드리겠습니다.

> #### giscus 앱 설치

당연하게도 giscus 설치가 필요합니다. [giscus app](https://github.com/apps/giscus)를 설치해주세요.

> #### 적용할 저장소에서 Discussions 활성화

giscus를 사용하려면 해당 저장소의 Discussions 기능을 활성화해야 합니다. [여기](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/enabling-or-disabling-github-discussions-for-a-repository)를 참고해주세요.

> #### 페이지 ↔️ Discussions 연결

giscus가 어떤 페이지에 어떤 Discussions를 연결할지 어떤 방식으로 연결할지 설정해야 합니다.  
저는 그냥 `Discussion 제목이 페이지 경로를 포함` 으로 선택했습니다.

> #### Discussion 카테고리

저는 추천해준대로 `Announcements` 로 설정했습니다.

> #### 기능

원하시는 기능을 설정해주세요.

> #### 테마

원하시는 테마를 설정해주세요.  
<br>

이제 `giscus 사용` 부분에 페이지에 적용해야할 `js` 코드가 나옵니다.

```html
<script src="https://giscus.app/client.js"
        data-repo="[ENTER REPO HERE]"
        data-repo-id="[ENTER REPO ID HERE]"
        data-category="[ENTER CATEGORY NAME HERE]"
        data-category-id="[ENTER CATEGORY ID HERE]"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="top"
        data-theme="preferred_color_scheme"
        data-lang="ko"
        crossorigin="anonymous"
        async>
</script>
```

원래는 이 스크립트 요소를 복사해서 원하는 html 페이지에 붙여넣기 하시고, 댓글이 나타나길 원하는 요소에 `giscus`라는 클래스를 넣으면 된다고 합니다.  
<br>

다만, 제가 쓰는 테마는 `_config.yml`에 `giscus`를 지원해주고 있어서 더 쉽게 할 수 있었습니다.

`_config.yml`에 `comments`에서 `giscus`부분을 입력해주세요.

```yml
...
comments:
  active: giscus        # The global switch for posts comments, e.g., 'disqus'.  Keep it empty means disable
  # The active options are as follows:
  disqus:
    shortname:    # fill with the Disqus shortname. › https://help.disqus.com/en/articles/1717111-what-s-a-shortname
  # utterances settings › https://utteranc.es/
  utterances:
    repo:         # <gh-username>/<repo>
    issue_term:   # < url | pathname | title | ...>
  # Giscus options › https://giscus.app
  giscus:
    repo: ENTER REPO HERE             # <gh-username>/<repo>
    repo_id: ENTER REPO ID HERE
    category: Announcements
    category_id: ENTER CATEGORY ID HERE
    mapping: pathname          # optional, default to 'pathname'
    strict: 0
    reactions_enabled: # optional, default to the value of `1`
    emit_metadata: 0
    input_position: top   # optional, default to 'bottom'
    theme: preferred_color_scheme          # optional, default to 'light'
    lang: ko             # optional, default to the value of `site.lang`
    loading: lazy        # optional, default to 'lazy'
...
```

`giscus`를 지원하지 않는 테마는 아마도 `_includes` 폴더에서 적용할 수 있는 페이지를 찾아서 `giscus` 클래스를 넣어주면 될 것 같습니다. 이 부분은 테마마다 다를 수 있으니 찾아보시면 될 것 같습니다.