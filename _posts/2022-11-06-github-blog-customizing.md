---
date: 2022-11-06 02:07:01 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 준비 단계](https://leejh95.github.io/posts/github-blog-prepare-to/)
2. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-ruby-jekyll/)
3. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기](https://leejh95.github.io/posts/github-blog-theme/)
4. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포](https://leejh95.github.io/posts/github-blog-build-deploy/)
5. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징](https://leejh95.github.io/posts/github-blog-customizing/)
6. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 첫 포스팅하기](https://leejh95.github.io/posts/github-blog-first-post/)

## 시작
---
이제 블로그를 커스터마이징 해봅시다.

## 프로젝트 구성
---
프로젝트를 구성하는 파일들이 무엇인지 알아야 합니다. 전부 설명하기에는 너무 길어지니, 간단하게 몇가지만 설명하겠습니다.

- _data: 사이트에 사용되는 데이터를 저장하는 곳입니다. (e.g. 메뉴, 사이트 정보 등)
- _includes: 사이트에 사용되는 공통적인 부분을 저장하는 곳입니다. (e.g. 헤더, 푸터 등)
- _layouts: 사이트에 사용되는 레이아웃을 저장하는 곳입니다. (e.g. 메인 페이지, 포스트 페이지 등)
- _posts: 포스트를 저장하는 곳입니다. (e.g. 블로그 포스트)
- _sass: 사이트에 사용되는 스타일을 저장하는 곳입니다. (e.g. CSS)
- _tabs: 탭을 저장하는 곳입니다. (e.g. 카테고리, 태그 등)
- assets: 사이트에 사용되는 이미지, 파일 등을 저장하는 곳입니다.
- _config.yml: 사이트의 설정을 저장하는 곳입니다.
- Gemfile: 사용되는 Gem을 저장하는 곳입니다.

## 사이트 설정
---
사이트의 설정은 `_config.yml`에 저장됩니다. 이곳에서 사이트의 제목, 설명, 메뉴 등을 설정할 수 있습니다.

제 설정 파일을 참고하시면 됩니다.
```yaml
theme: jekyll-theme-chirpy                # 사용할 테마

baseurl: ''                               # 사용자 이름으로 Github Pages를 사용할 경우, 빈 문자열로 설정합니다.

lang: ko-KR                               # 사용할 언어, _data/locales 폴더에 있는 파일을 사용합니다.

timezone: Asia/Seoul                      # 사용할 시간대, (e.g. Asia/Seoul)

title: Leejh                              # 사이트 제목

tagline: 이것 저것 메모용 블로그                # 사이트 부제목

description: >-                           # 사이트 설명
  알아낸 것, 공부한 것, 적어놓을 것 메모하기...

url: 'https://leejh95.github.io'          # 사이트 주소 본인의 Github Pages 주소로 설정합니다.

github:
  username: leejh95                       # Github 사용자 이름

# twitter:                                # 트위터가 없어서 주석처리했습니다.
  # username: twitter_username

social:
  name: leejh95                           # 소셜란에 사용할 이름
  email: 아이디@email.com                   # 소셜란에 사용할 이메일
  links:
    # - https://twitter.com/username      # 트위터가 없어서 주석처리했습니다.
    - https://github.com/leejh95          # 깃허브 주소
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username

google_site_verification: 코드             # 구글 웹마스터 도구에 등록한 사이트의 코드 (일단 비워놓기)

google_analytics:
  id: G-XXXXXXXXXXX                       # 구글 애널리틱스에 등록한 사이트의 코드 (일단 비워놓기)
  pv:
    proxy_endpoint:   # fill in the Google Analytics superProxy endpoint of Google App Engine
    cache_path:       # the local PV cache data, friendly to visitors from GFW region

theme_mode:                               # [light|dark] 테마 모드를 정할 수 있음 비워두면 시스템 설정에 따라 결정됨

img_cdn: https://cdn.jsdelivr.net/gh/leejh95/leejh95.github.io@main # 이미지 CDN 주소 (일단 비워놓기)

avatar: /assets/img/rocket.png            # 프로필 사진

toc: true                                 # 목차를 사용할지 여부

comments:                                 # 댓글 기능 관련 설정
  active: disqus                          # 댓글을 사용할지 여부 (disqus를 사용하고 싶으면 disqus 입력) (일단 비워놓기)
  disqus:
    shortname: 숏네임                       # disqus에 등록한 사이트의 숏네임 (일단 비워놓기)
  utterances:
    repo:         # <gh-username>/<repo>
    issue_term:   # < url | pathname | title | ...>
  giscus:
    repo:              # <gh-username>/<repo>
    repo_id:
    category:
    category_id:
    mapping:           # optional, default to 'pathname'
    input_position:    # optional, default to 'bottom'
    lang:              # optional, default to the value of `site.lang`
    reactions_enabled: # optional, default to the value of `1`

assets:
  self_host:
    enabled:      # boolean, keep empty means false
    # specify the Jekyll environment, empty means both
    # only works if `assets.self_host.enabled` is 'true'
    env:          # [development|production]

pwa:
  enabled: true   # pwa 기능 사용할지 여부

paginate: 10

## 이 아래로는 건드릴 부분이 없는 것 같네요.
```

> `_config.yml`파일의 수정사항을 로컬에서 확인하려면 반드시 서버를 재구동해 줘야 합니다.  
> `Ctrl + C` 그리고 `bundle exec jekyll serve`
{: .prompt-info}

\+추가 설명할 부분이 꽤 있습니다.

- 구글 웹마스터
- 구글 애널리틱스
- 이미지 CDN 주소
- 댓글 기능
- pwa 기능

이것들에 대한 설명은 너무 길어지니 일단 넘어갈게요. 기회가 된다면 추후에 포스팅 하겠습니다.🙂

## 사이트 스타일 수정
---
`_config.yml`에선 기본적인 것만 수정할 수 있습니다만, 추가적으로 프로젝트에 있는 파일들을 수정하면 좀 더 여러가지 스타일적인 부분을 바꿀 수 있습니다. (물론 원하는 사람만)

### 사이드바 배경 변경
---
`_sass/addon/commons.scss`파일을 열어서 아래 부분을 수정해 줍니다.

```scss
...
#sidebar {
  @include pl-pr(0);

  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  overflow-y: auto;
  width: $sidebar-width;
  z-index: 99;
  // background: var(--sidebar-bg); // 기존 코드
  background-image: url('/assets/img/background.jpg'); // 변경할 이미지 주소
  background-size: cover; // 배경크기가 알아서 조절됨
...
```
### 사이드바 아래 메뉴 변경
---
저는 트위터를 사용하지 않아서 트위터 아이콘을 지워주겠습니다.

`_includes/sidebar.html`파일을 열어서 아래 부분을 수정해 줍니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-06%20%ec%98%a4%ed%9b%84%203.59.43.png?Web=1)

### Footer 변경
---
저는 따로 수정하지 않았지만, 바꾸고 싶다면 `_includes/footer.html`파일을 열어서 수정하면 됩니다.

### about 페이지 변경
---
`_tabs/about.md`파일을 열어서 수정하면 됩니다.

```markdown
---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---

## About
---
This is about page.
```

### favicon 변경
---
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-06%20%ec%98%a4%ed%9b%84%204.13.27.png?Web=1)  

웹사이트 탭에 보이는 아이콘(favicon)을 바꿔보겠습니다.

> <https://chirpy.cotes.page/posts/customize-the-favicon/>  
> ⬆️ 이 글을 참고하였습니다.

[Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/)의 favicon은 `assets/img/favicons/`디렉토리에 있습니다. 자신의 것으로 교체하고 싶을 수도 있습니다. 다음 섹션에서는 기본 파비콘을 만들고 바꾸는 방법을 안내합니다.

#### 파비콘 생성

크기가 512x512 이상인 정사각형 이미지(PNG, JPG 또는 SVG)를 준비한 다음 온라인 도구인 [Real Favicon Generator](https://realfavicongenerator.net/) 로 이동하여 `Select your Favicon image` 버튼을 클릭 하여 이미지 파일을 업로드합니다.

다음 단계에서는 웹 페이지에 모든 사용 시나리오가 표시됩니다. 기본 옵션을 유지하고 페이지 하단으로 스크롤한 다음 `Generate your Favicons and HTML code` 버튼을 클릭 하여 favicon을 생성할 수 있습니다.

#### 다운로드 및 교체

생성된 패키지를 다운로드하고 압축을 푼 다음 추출된 파일에서 다음 두 개를 삭제합니다.

- browserconfig.xml
- site.webmanifest

그런 다음 나머지 이미지 파일( .PNG 등 )을 복사 하여 assets/img/favicons 디렉토리에 있는 원본 파일을 덮어쓰기 합니다. 아직 이 디렉토리가 없으면 새로 만드십시오.

이제 서버를 다시 실행하여 favicon이 표시되는지 확인하십시오. 만약 favicon이 표시되지 않는다면, 브라우저 캐시를 비우고 다시 시도해 보십시오.

## 마무리
---
이제 정말 마무리 단계입니다. 다음 글에서는 처음으로 글을 포스팅 해보겠습니다. 

## 다음 글
---
[Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 첫 포스팅하기](https://leejh95.github.io/posts/github-blog-first-post/)

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>