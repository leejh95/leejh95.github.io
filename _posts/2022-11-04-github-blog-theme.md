---
date: 2022-11-04 17:16:42 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀🚀🚀 - 테마 고르기
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀🚀🚀 - 준비 단계](https://leejh95.github.io/posts/github-blog-prepare-to/)
2. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀🚀🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-install-ruby-jekyll/)
3. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀🚀🚀 - 테마 고르기](https://leejh95.github.io/posts/github-blog-theme/)

## 테마 고르기
---
Jekyll에는 많은 테마들이 있습니다. 그 중에서 마음에 드는 무료 테마를 골라서 사용하면 됩니다. (유료도 있습니다.)

- <https://pages.github.com/themes/>
- <http://jekyllthemes.org/>
- <https://jekyllthemes.io/free>
- <http://themes.jekyllrc.org/>
- <https://github.com/topics/jekyll-theme>

저는 블로그를 만들 생각이었으니까... 블로그 테마를 골라야 겠죠??

여기저기 구글링을 하며 둘러보면서 결국 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) 라는 테마를 골랐습니다.([데모](https://chirpy.cotes.page/)) 꽤 인기있는 블로그 테마였고 지원하는 기능도 아주 좋더군요. 게다가 MIT 라이센스로 배포되고 있어서 누구나 무료로 사용할 수 있다고 합니다.

그래서 앞으로 이 테마를 기준으로 글을 써보려고 합니다. 다른 테마를 고르셔도 자유지만 테마에 따라서 설정 방법이 다를 수 있으니 참고해주세요.

## 테마 적용하기
---
테마를 골랐으니 이제 테마를 적용해보겠습니다.

대부분 고른 테마의 Github 저장소로 가시면 README.md 파일에 방법이 친절하게 적혀있습니다!

> Quick Start  
> Before starting, please follow the instructions in the Jekyll Docs to complete the installation of Ruby, RubyGems, Jekyll, and Bundler. In addition, Git is also required to be installed.
>
> Step 1. Creating a New Site  
> Create a new repository from the Chirpy Starter and name it <GH_USERNAME>.github.io, where GH_USERNAME represents your GitHub username.
>
> Step 2. Installing Dependencies  
> ...

아니면 다운받아서 로컬에서 내 저장소로 직접 올리는 방법도 있습니다만... 귀찮으니 이건 패스ㅎㅎ

제가 고른 테마는 [Chirpy Starter](https://github.com/cotes2020/chirpy-starter/generate)라는 빠른 시작 기능을 제공하고 있네요. 부수적인 기능을 전부 제거해서 가장 기본적인 테마만 남겨놓은 것 같습니다. 이걸로 시작하면 편하겠지만... 저는 추천드리지 않겠습니다. 받아서 둘러보니까 커스텀 가능한 부분들이 많이 빠져있더군요.

저는 그냥 테마를 fork해서 제 저장소로 직접 옮기겠습니다. 아니면 제가 고른 테마의 저장소 페이지에서 README.md




## 마무리
---
끝났습니다!! 여기까지 잘 오셨으면 이제 시스템에 설치된 `Ruby`대신 최신 버전의 `Ruby`와 `Jekyll`을 사용할 수 있습니다. 다음에는 `Jekyll`을 사용하여 블로그를 만들어보겠습니다.😊

## 다음 글
---
다음글 링크  

## 참조
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>