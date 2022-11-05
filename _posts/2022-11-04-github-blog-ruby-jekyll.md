---
date: 2022-11-04 00:35:33 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 준비 단계](https://leejh95.github.io/posts/github-blog-prepare-to/)
2. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-ruby-jekyll/)
3. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기](https://leejh95.github.io/posts/github-blog-theme/)
4. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포](https://leejh95.github.io/posts/github-blog-build-deploy/)
5. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징](https://leejh95.github.io/posts/github-blog-customizing/)

## `macOS`에서 `Ruby` 설치는 어렵다?
---
> Ruby란?  
> Ruby는 1995년에 일본의 마츠모토 유키히로가 개발한 객체지향 스크립트 언어이다.

`Ruby`...

`Jekyll`을 설치하기 위해 반드시 깔아야 하는 스크립트 언어입니다.

Homebrew가 설치되어 있다면 몇번의 명령어만으로 간단하게 설치할 수 있습니다. 하지만... 이게 정말 쉽지 않았습니다.

macOS 업데이트를 하고 그 날 바로 `Ruby`를 설치했었는데, 설치가 정상적으로 되었지만 그 이후 작업은 정상적으로 진행되지 않았습니다. 할 수 없이 강제로 제거 후 또 다른 방식으로 설치를 시도했지만, 계속 오류가 발생했습니다. 그리고 이것의 반복...

결론부터 말하자면, 제가 macOS 13(Ventura)이 출시되자 마자 바로 업데이트를 했던게... 그래서 소프트웨어의 여러가지 지원이 덜 되어있던게 원인이었죠..😂😂

어찌저찌 해결해서 잘 설치가 되었습니다. 그런데 알고보니 이렇게 저처럼 macOS에서 `Ruby`를 설치하지 못하는 경우가 정말 많은 것 같았어요. 어느정도냐 하면 아예 macOS를 위한 `Ruby`를 한번에 설치할 수 있게 해주는 서비스가 따로 있더라구요.

> _[Ruby on Mac](https://www.rubyonmac.dev/?utm_campaign=install-ruby-guide)_  
> _Goodbye gem and Ruby installation issues. Hello Ruby on Mac._  
> _(안녕 gem과 Ruby 설치 문제. 안녕하세요 Ruby on Mac.)_  
> _**Before Ruby on Mac**: Spend days trying to get your Rails, Jekyll, iOS, React Native, or other Ruby project working._  
> _(**Ruby on Mac 이전**: Rails, Jekyll, iOS, React Native 또는 기타 Ruby 프로젝트 작업을 하기위해 하루를 보냅니다..)_  
> _**With Ruby on Mac**: Run a single command and you'll be up and running in 15 minutes or less._  
> _(**Ruby on Mac과 함께**: 단일 명령을 실행하면 15분 이내에 실행됩니다.)_

정말로 많은 사람들이 이런 문제를 겪고 계신 것 같아요. 이 정도면 설치가 어려운게 맞는 것 같습니다.😂

아쉽게도 Ruby on Mac은 유료입니다. 돈 내면서 할거면 애초에 이런짓 안하고 있겠죠? 그래서 밑에 macOS에서 `Ruby`를 설치하는 방법을 최대한 정리 해보겠습니다. 물론 끝까지 따라 오셔도 실패할 수도 있습니다.. 워낙 문제가 다양해서..ㅎㅎ

> _<https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>_  
> _⬆️ 이 글을 참고하였습니다._

## 전제 조건
---
> - 컴퓨터가 연결되어 있고 인터넷에 안정적으로 연결되어 있는지 확인하십시오.
> - `macOS`가 최신 버전인지 확인하십시오.
> - Homebrew가 `brew` 명령어를 실행할 수 있는 준비가 되어있는지 확인하십시오.
> - `RVM`, `rbenv` 또는 `asdf`가 설치되어 있지 않은지 확인하십시오.

위와 같은 전제 조건이 충족되어야 합니다.
<br>
<br>
> - 컴퓨터가 연결되어 있고 인터넷에 안정적으로 연결되어 있는지 확인하십시오.
> - `macOS`가 최신 버전인지 확인하십시오.

위 두개는 설명이 따로 필요 없겠죠??
<br>
<br>
> - Homebrew가 `brew` 명령어를 실행할 수 있는 준비가 되어있는지 확인하십시오.

Homebrew가 준비되어있는지는 아래와 같이 확인할 수 있습니다.

> Homebrew가 만족스러운지 확인하려면 터미널에서 다음 명령어를 실행하십시오.
> ```zsh
> brew doctor
> ```
> 그 다음 `Your system is ready to brew.`라는 메시지가 나오면 Homebrew가 준비되어 있다는 것입니다.  
> 만약 준비가 되지 않았다면 Homebrew의 설명을 읽고 스스로 문제를 해결할 수 있는지 확인하십시오. Homebrew는 일반적으로 문제 해결에 대한 자세한 지침을 제공합니다.

<br>

> - `RVM`, `rbenv` 또는 `asdf`가 설치되어 있지 않은지 확인하십시오.

`Ruby`는 다양한 버전이 있습니다. 하지만 원하는 버전을 설치해서 관리하기는 쉽지 않죠. 그래서 버전을 관리해주는 패키지를 설치해야 하는데요. `chruby`, `RVM`, `rbenv`, `asdf` 등 다양한 패키지가 있습니다.

정말 많은 블로그 글을 찾아봤는데 대부분 `rbenv`를 사용하고 있더라구요?? 사실 어떤것을 사용해도 상관 없을 것 같지만, `Jekyll` 공홈이나 최신글이 올라온 해외 사이트에서는 `chruby`를 추천하고 있습니다. 그래서 저도 `chruby`를 사용하겠습니다. 모든 `Ruby` 관리자 중 `chruby` 가 가장 안정적이고 사용 및 유지 관리가 쉽다고 하네요.

다만 `Ruby` 관리자는 서로 호환되지 않으므로 `RVM`, `rbenv` 또는 `asdf`가 있는 경우 제거하는 것이 좋습니다.

> 터미널에서 다음 명령을 실행합니다.
> ```zsh
> rvm help
> ```
> ```zsh
> rbenv help
> ```
> ```zsh
> asdf --help
> ```
> 해당 명령이 정보를 반환하면 해당 도구가 설치된 것입니다. `command not found`이라고 표시되면 설치되지 않은 것입니다. 설치한 경우 웹 사이트에서 각 도구에 대한 제거/비활성화 지침을 찾으십시오.

## `Ruby` 설치
---
\*\* 혹시 Apple Silicon Mac(M1/M2)을 사용하시는 분이라면 아래를 참고해주세요. \*\*

> Apple Silicon Mac(M1/M2)을 사용하는 경우에만 이 부분을 읽으십시오.  
> Apple Silicon Mac을 사용하는 경우 터미널이 Rosetta 모드에 있지 않은지 확인하십시오.
> 
> 터미널이 열리면 이 명령을 실행하여 확인할 수 있습니다.  
> `uname -m`
> 만약 Apple Silicon Mac을 사용 중이라면 `arm64` 를 말해야 합니다. `x86_4` 라고 표시 되면 터미널이 Rosetta 모드에 있음을 의미합니다. 이것이 발생할 수 있는 유일한 방법은 설정을 직접 변경한 경우이며, 아마도 올바르지 않거나 오래된 조언을 따른 후일 가능성이 큽니다. Rosetta를 끄려면 다음 지침을 따르십시오.
> 1. 터미널이 실행 중이면 종료
> 2. Finder로 이동
> 3. shift-command-U 를 눌러 유틸리티 폴더로 이동합니다 (또는 메뉴 모음에서 "이동"을 선택한 다음 유틸리티 선택).
> 4. 터미널을 선택하되 실행하지는 마십시오. 한 번만 클릭하면 선택됩니다.
> 5. 누르기 command-i(또는 메뉴 표시줄에서 "파일", "정보 가져오기")
> 6. "Rosetta를 사용하여 열기" 확인란의 선택을 취소합니다.
> 7. 터미널 정보 창 닫기
> 8. 터미널 실행
> 9. `uname -m` 실행. `arm64` 출력. 이제 가이드의 나머지 부분을 계속 진행할 수 있습니다.

\*\* 쉘에 대한 참고 사항 \*\*

> 이 튜토리얼에서는 `zsh`을 사용합니다. 자신의 쉘이 확실하지 않은 경우 [어떤 쉘을 사용하고 있습니까? 어떻게 전환할 수 있습니까?](https://www.moncefbelyamani.com/which-shell-am-i-using-how-can-i-switch/) 이 가이드를 참고해주세요.

### `ruby-install`을 사용하여 `chruby` 및 최신 `Ruby` 설치하기.

`chruby` 및 `ruby-install` 설치:
```zsh
brew install chruby ruby-install
```
다음으로 Apple Silicon Mac(M1 또는 M2)을 사용하는 경우 사용 중인 Apple 명령줄 도구(CLT) 또는 Xcode의 버전을 확인해야 합니다.
```zsh
brew config
```
`CLT:` 로 시작하는 줄을 찾으십시오 만약 `14` 로 시작한다면 다음과 같이 Ruby를 설치해야 합니다.
```zsh
ruby-install ruby -- --enable-shared
```
그렇지 않으면 추가 옵션을 사용하지 마십시오.
```zsh
ruby-install ruby
```
이 작업은 몇분 정도 걸릴 수 있습니다.

> 문제가 발생했나요?  
> `!!! Compiling Ruby 3.1.2 failed!`, or `!!! Installation of ruby 3.1.2 failed!`, or `!!! Configuration of ruby 3.1.2 failed!`, 아니면 다른 많은 에러가 발생할 수 있습니다.
>
> 이것은 다음 문제 중 하나 때문일 수 있습니다:
> - 개발 설정에 문제가 있습니다.
> - Apple Silicon Mac에 2.6.8 이전 버전의 Ruby를 설치하려고 합니다.
> - 지원되지 않는 macOS 버전에 Ruby를 설치하려고 합니다.
>
> 이 문제를 해결하는 확실한 방법은 개발 설정을 정리하고 처음부터 다시 시작하는 것입니다.
{: .prompt-warning }

### 쉘 설정 파일을 구성하기.

다음 명령어를 실행하여 `chruby`을 자동으로 로드하고 `~/.zshrc`에 추가합니다.
```zsh
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.1.2" >> ~/.zshrc
```
위 명령에서 `3.1.2`는 설치한 `Ruby`의 버전이라고 가정합니다.

> 만약에 잘못 입력했다면 `vim` 명령어로 `~/.zshrc` 파일을 열어서 수정하십시오.
> ```zsh
> vim ~/.zshrc
> ```
> `i`를 눌러서 `vim`의 편집 모드로 전환한 다음 원하는 부분을 수정하십시오. 그런 다음 `esc`를 눌러서 `vim`의 명령 모드로 전환한 다음 `:wq`를 입력하여 저장하고 종료하십시오.
> ```vim
> ...
> 112
> 113 source /opt/homebrew/opt/chruby/share/chruby/chruby.sh
> 114 source /opt/homebrew/opt/chruby/share/chruby/auto.sh
> 115 chruby ruby-3.1.2
> ```
{: .prompt-warning }

터미널을 종료하고 다시 시작한 다음 아래 명령어가 작동하는지 확인해주세요.
```zsh
ruby -v
```
`ruby 3.1.2`로 시작하는 줄이 출력될 것입니다. 최신 버전 루비가 설치되었습니다.😊

## 원하는 Gem 설치
---
이제 `Ruby`를 사용할 준비가 되었습니다. 이제 원하는 `Gem`을 설치할 수 있어요. `Gem`은 `Ruby`에서 사용할 수 있는 라이브러리입니다. `Gem`들을 설치하려면 `gem` 명령어를 사용하면 됩니다. `brew` 같은 패키지 관리 명령어 라고 할 수 있겠네요.

```zsh
gem install 패키지명1 패키지명2 ...
```

> `gem` 명령어는 `sudo`를 사용하지 않아도 됩니다. `sudo`를 사용하면 `gem`을 설치할 수 없습니다.
{: .prompt-warning }

이제 `bundler`와 `jekyll`을 설치해봅시다.
```zsh
gem install bundler jekyll
```

> Bundler는 Gemfile에 정의된 젬(Gem)들의 의존성을 파악해서 올바른 젬(Gem)을 사용할 수 있게끔 해주는 명령어입니다.
{: .prompt-info }

## 마무리
---

끝났습니다!! 여기까지 잘 오셨으면 이제 시스템에 설치된 `Ruby`대신 최신 버전의 `Ruby`와 `Jekyll`을 사용할 수 있습니다. 다음에는 `Jekyll`을 사용하여 블로그를 만들어보겠습니다.😊

## 다음 글
---
[Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기](https://leejh95.github.io/posts/github-blog-theme/)

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>