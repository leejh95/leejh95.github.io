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

## 커스터마이징
---
이제 블로그를 커스터마이징 해봅시다.

### 프로젝트 구성
---
가장 최상위에있는 파일들이 무엇인지 알아야 합니다. 전부 설명하기에는 너무 길어지니, 간단하게 몇가지만 설명하겠습니다.

- _data: 사이트에 사용되는 데이터를 저장하는 곳입니다. (e.g. 메뉴, 사이트 정보 등)
- _includes: 사이트에 사용되는 공통적인 부분을 저장하는 곳입니다. (e.g. 헤더, 푸터 등)
- _layouts: 사이트에 사용되는 레이아웃을 저장하는 곳입니다. (e.g. 메인 페이지, 포스트 페이지 등)
- _posts: 포스트를 저장하는 곳입니다. (e.g. 블로그 포스트)
- _sass: 사이트에 사용되는 스타일을 저장하는 곳입니다. (e.g. CSS)
- _tabs: 탭을 저장하는 곳입니다. (e.g. 카테고리, 태그 등)
- assets: 사이트에 사용되는 이미지, 파일 등을 저장하는 곳입니다.
- _config.yml: 사이트의 설정을 저장하는 곳입니다.
- Gemfile: 사용되는 Gem을 저장하는 곳입니다.

### 사이트 설정
---
사이트의 설정은 `_config.yml`에 저장됩니다. 이곳에서 사이트의 제목, 설명, 메뉴 등을 설정할 수 있습니다.

제 설정 파일을 참고하시면 됩니다.
```yaml
theme: jekyll-theme-chirpy                # 사용할 테마

baseurl: ''                               # 사용자 이름으로 Github Pages를 사용할 경우, 빈 문자열로 설정합니다. (e.g. https://username.github.io)

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
  email: wogns6857@gmail.com              # 소셜란에 사용할 이메일
  links:
    # - https://twitter.com/username      # 트위터가 없어서 주석처리했습니다.
    - https://github.com/leejh95          # 깃허브 주소
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username

google_site_verification: 코드             # 구글 웹마스터 도구에 등록한 사이트의 코드

google_analytics:
  id: G-XXXXXXXXXXX                       # 구글 애널리틱스에 등록한 사이트의 코드
  pv:
    proxy_endpoint:   # fill in the Google Analytics superProxy endpoint of Google App Engine
    cache_path:       # the local PV cache data, friendly to visitors from GFW region

theme_mode:                               # [light|dark] 테마 모드를 정할 수 있음

img_cdn: https://cdn.jsdelivr.net/gh/leejh95/leejh95.github.io@main # 이미지 CDN 주소

avatar: /assets/img/rocket.png            # 프로필 사진

toc: true                                 # 목차를 사용할지 여부

comments:
  active: disqus                          # 댓글을 사용할지 여부 (disqus를 사용하고 싶으면 disqus 입력)
  disqus:
    shortname: 숏네임                       # disqus에 등록한 사이트의 숏네임
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
  enabled: true   # the option for PWA feature

paginate: 10

## 이 아래로는 건드릴 부분이 없는 것 같네요.
```

### 


## 마무리
---
이제 Jekyll 블로그가 전부 설치되었습니다. 남은건 작업물을 빌드, 배포해주고 설정을 바꿔주고 포스트를 작성하시면 됩니다. 다음 글에서 git 다루기와 github actions, 블로그를 커스터마이징하는 방법을 알아보겠습니다.

## 다음 글
---
다음글 링크  

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>