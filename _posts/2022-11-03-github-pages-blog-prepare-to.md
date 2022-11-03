---
date: 2022-11-03 17:32:40 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀🚀🚀 - 준비 단계
categories: [Tutorial, Github Pages]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀🚀🚀 - 준비 단계](https://leejh95.github.io/posts/github-pages-blog-prepare-to/)

## 시작
---
바로 시작해보겠습니다. 아무래도 일반적인 블로그 플랫폼과는 다르게 가벼운 느낌으로 짜잔하고 시작할 수는 없습니다. `Jekyll` 프로젝트를 빌드하고 `Github`에 호스팅하는 단계를 거쳐야 하기 때문이죠 저도 꽤 고생했던 것 같네요. 아무튼 이곳에 적혀있는 대로 잘 따라오시면 누구나 Github Pages로 블로그를 만들 수 있다고 생각합니다. 일단은 제가 작업한 환경과 사전 준비물을 적어놓겠습니다. 저는 `macOS`에서 작업을 진행했는데요 그래서 `macOS`기준으로 설명하게 되겠지만 아마 `Windows`도 크게 다르지 않을거라 생각됩니다.

## 준비물
---
### 최신 버전 `macOS`
---
_(또는 `Windows`... 저는 `macOS`에서 작업했습니다.)_

다음 단계에서 `Jekyll`을 설치하기 위해서는 반드시 `Ruby`라는 언어를 설치해야 하는데요 하지만 조건이 있습니다.

> `Ruby`를 설치하기 위해 지원되는 macOS 버전:
>
> - 벤투라(macOS 13)  
> - 몬테레이(macOS 12)  
> - 빅서(macOS 11)  
>
> 이전 macOS 버전은 여전히 ​​작동할 수 있지만 보장할 수는 없습니다.

사실 `macOS`에는 이미 시스템에 `Ruby`가 설치되어 있습니다만... `Jekyll`을 설치하기 위해서는 해당 버전을 사용하지 않는 것이 좋다고 하네요.

> _macOS에 Jekyll을 설치하려면 적절한 Ruby 개발 환경이 필요합니다. macOS에는 Ruby가 사전 설치되어 제공되지만 해당 버전을 사용하여 Jekyll을 설치하지 않는 것이 좋습니다. 이 외부 기사에서는 [시스템 Ruby를 사용하지 말아야 하는 다양한 이유](https://www.moncefbelyamani.com/why-you-shouldn-t-use-the-system-ruby-to-install-gems-on-a-mac/)에 대해 설명합니다._

### 최신 버전 `Homebrew`
---
`Homebrew`는 `macOS`에서 패키지 관리를 쉽게 할 수 있도록 도와주는 패키지 관리자입니다. `Homebrew`가 설치되어있지 않다면 [여기](https://brew.sh/index_ko)를 참고하여 설치해주세요.

혹시 `Homebrew`가 설치되어 있는지 확인하고 싶다면 터미널에서 다음 명령어를 입력해주세요.

```zsh
$ brew -v
```

`Homebrew`가 설치되어 있다면 다음과 같이 버전이 출력됩니다.

```zsh
Homebrew 3.2.6
Homebrew/homebrew-core (git revision 1b2c; last commit 2021-05-05)
```


### `Git` 설치와 `Github` 계정
---
당연히 있어야겠죠?
- Google 계정 (Google의 서비스를 사용하기 위해 필요합니다.)
- Visual Studio Code (다른 에디터를 사용해도 상관없습니다.)

끝입니다!! 위에 것들은 따로 설명하지 않고 넘어갈게요. 이 글을 보고 Github Pages와 Jekyll을 사용해서 블로그를 만들어보고 싶으신 분들은 이렇게 준비하시면 됩니다.

## Github 계정
---
Github Pages와 Jekyll을 사용해서 나만의 블로그를 만들기 위해서는 Github 계정이 필요합니다.

## 참조
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>