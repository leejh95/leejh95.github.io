---
date: 2022-11-03 17:32:40 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 준비 단계
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 준비 단계](https://leejh95.github.io/posts/github-blog-prepare-to/)
2. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-ruby-jekyll/)
3. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기](https://leejh95.github.io/posts/github-blog-theme/)
4. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포](https://leejh95.github.io/posts/github-blog-build-deploy/)
5. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징](https://leejh95.github.io/posts/github-blog-customizing/)
6. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 첫 포스팅하기](https://leejh95.github.io/posts/github-blog-first-post/)

## 이야기
---
Github Pages라는 호스팅 서비스가 있습니다.

> [Github Pages](https://pages.github.com/)
> _당신과 당신의 프로젝트를 위한 웹사이트. GitHub 저장소 에서 직접 호스팅됩니다. 수정하고 푸시하면 변경 사항이 적용됩니다._

당연히 `Github`에서 제공하고 있습니다. `Github` 저장소에 정적 웹 작업물을 푸시 하면 자동으로 호스팅을 해주는 서비스인데요 그냥 단순히 저장소에 올리기만 하면 나머지는 설정은 거의 자동이니까 정말 좋죠, 심지어 무료입니다! 물론 일정 조건 안에서만 무료예요... (e.g. 업로드한 파일들의 용량이 1기가 이하)

이제 이곳에다 `Jekyll`이라는 정적 웹 파일을 만들어주는 서비스를 사용해서 나만의 블로그를 만들어보려고 합니다.

## 시작
---
바로 시작해 보겠습니다. 아무래도 일반적인 블로그 플랫폼과는 다르게 가벼운 느낌으로 짜잔 하고 시작할 수는 없습니다. `Jekyll` 프로젝트를 빌드하고 `Github`로 업로드 및 호스팅 하는 단계를 거쳐야 하기 때문이죠.

아무튼 이곳에 적혀있는 대로 잘 따라오시면 누구나 Github Pages로 블로그를 만들 수 있다고 생각합니다.

일단은 제가 작업한 환경과 사전 준비물을 적어놓겠습니다. 저는 `macOS`에서 작업을 진행했는데요 그래서 `macOS`기준으로 설명하게 되겠지만 아마 `Windows`도 크게 다르지 않을거라 생각됩니다.

다음 작업들은 전부 `2022-11-01` 기준으로 진행되었습니다.

## 준비물
---
### 최신 버전 `macOS`
---
_(또는 `Windows`... 저는 `macOS`에서 작업했습니다.)_

웹 프로젝트를 만들기 위해서는 `Jekyll`이 필요합니다. 하지만 `Jekyll`은 `Ruby`라는 언어가 필요한데요, 다음과 같은 조건이 있습니다.

> `Ruby`를 설치하기 위해 지원되는 macOS 버전:
>
> - 벤투라(macOS 13)  
> - 몬테레이(macOS 12)  
> - 빅서(macOS 11)  
>
> 이전 macOS 버전은 여전히 ​​작동할 수 있지만 보장할 수는 없습니다.

사실 `macOS`에는 이미 시스템에 `Ruby`가 설치되어 있습니다만... `Jekyll`을 설치하기 위해서는 시스템 버전을 사용하지 않는 것이 좋다고 하네요.

> _macOS에 Jekyll을 설치하려면 적절한 Ruby 개발 환경이 필요합니다. macOS에는 Ruby가 사전 설치되어 제공되지만 해당 버전을 사용하여 Jekyll을 설치하지 않는 것이 좋습니다. 이 외부 기사에서는 [시스템 Ruby를 사용하지 말아야 하는 다양한 이유](https://www.moncefbelyamani.com/why-you-shouldn-t-use-the-system-ruby-to-install-gems-on-a-mac/)에 대해 설명합니다._
{: .prompt-warning }

### 최신 버전 `Homebrew`
---
`Homebrew`는 `macOS`에서 패키지 관리를 쉽게 할 수 있도록 도와주는 패키지 관리자입니다. `Homebrew`가 설치되어있지 않다면 [여기](https://brew.sh/index_ko)를 참고하여 설치해주세요.

혹시 `Homebrew`가 설치되어 있는지 확인하고 싶다면 터미널에서 다음 명령어를 입력해주세요.

```zsh
$ brew -v
```

`Homebrew`가 설치되어 있다면 설치된 버전이 출력될 것입니다.

### Github 계정과 `Git`
---
Github 계정... 당연히 있어야겠죠?
<br>
<br>
그리고 `Git`  
`Git`은 필수입니다. `Git`이 설치되어 있지 않다면 [여기](https://git-scm.com/downloads)를 참고하여 설치해주세요.

혹시 `Git`이 설치되어 있는지 확인하고 싶다면 터미널에서 다음 명령어를 입력해주세요.

```zsh
$ git --version
```

`Git`이 설치되어 있다면 설치된 버전이 출력될 것입니다.

### Visual Studio Code 설치
---
VSCode는 다양한 언어를 지원하는 텍스트 에디터입니다.

`Jekyll`에서 포스팅 파일은 `Markdown`이라는 마크업 언어로 이루어져 있습니다. 그래서 전용 에디터를 사용해야 하는데요, 저는 VSCode를 추천드립니다. 굉장히 다양하고 편리한 기능들을 제공하거든요.

[여기](https://code.visualstudio.com/)에서 VSCode를 설치할 수 있습니다.

_(`Markdown`만 지원된다면 다른 에디터도 상관없습니다.)_

## 마무리
---
끝입니다!! 이 글을 보고 Github Pages와 Jekyll을 사용해서 블로그를 만들어보고 싶으신 분들은 위에 것들을 준비해서 따라오시면 됩니다.

## 다음 글
---
[Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-ruby-jekyll/)

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>