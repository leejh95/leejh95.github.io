---
date: 2022-11-04 17:16:42 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 준비 단계](https://leejh95.github.io/posts/github-blog-prepare-to/)
2. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-ruby-jekyll/)
3. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기](https://leejh95.github.io/posts/github-blog-theme/)
4. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포](https://leejh95.github.io/posts/github-blog-build-deploy/)
5. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징](https://leejh95.github.io/posts/github-blog-customizing/)
6. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 첫 포스팅하기](https://leejh95.github.io/posts/github-blog-first-post/)

## 테마 고르고 적용하기
---
Jekyll에는 많은 웹 사이트 테마들이 있습니다. 그 중에서 마음에 드는 무료 테마를 골라서 사용하면 됩니다. (유료도 있습니다.)

- <https://pages.github.com/themes/>
- <http://jekyllthemes.org/>
- <https://jekyllthemes.io/free>
- <http://themes.jekyllrc.org/>
- <https://github.com/topics/jekyll-theme>

저는 블로그를 만들 생각이었으니까... 블로그 테마를 골라야 겠죠??

여기저기 구글링을 하며 둘러보면서 결국 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) 라는 테마를 골랐습니다.([데모](https://chirpy.cotes.page/))

![Chirpy](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/devices-mockup.png?Web=1)
_Chirpy Theme_

꽤 인기있는 블로그 테마였고 지원하는 기능도 아주 좋더군요. 게다가 MIT 라이센스로 배포되고 있어서 누구나 무료로 사용할 수 있다고 합니다.

그래서 앞으로 이 테마를 기준으로 글을 써보려고 합니다. 다른 테마를 고르셔도 자유지만 테마에 따라서 설정 방법이 다를 수 있으니 참고해주세요.

## 테마 적용하기
---
테마를 골랐으니 이제 테마를 제 저장소에 적용해보겠습니다.

대부분의 경우에는 정한 테마의 Github 저장소로 가시면 README.md 파일에 방법이 친절하게 적혀있습니다!

> Quick Start  
> Before starting, please follow the instructions in the Jekyll Docs to complete the installation of Ruby, RubyGems, Jekyll, and Bundler. In addition, Git is also required to be installed.
>
> Step 1. Creating a New Site  
> Create a new repository from the Chirpy Starter and name it <GH_USERNAME>.github.io, where GH_USERNAME represents your GitHub username.
>
> Step 2. Installing Dependencies  
> ...

보통 적혀있는대로 따라 하시면 될 것 같구요.

아니면 다운받아서 로컬에서 내 저장소로 직접 올리는 방법도 있습니다만... 귀찮으니 이건 패스ㅎㅎ

제가 고른 테마는 [Chirpy Starter](https://github.com/cotes2020/chirpy-starter/generate)라는 빠른 시작 기능을 제공하고 있네요. 이걸 사용하면 뼈대만 있는 테마로 빠르게 시작할 수 있도록 해놓은 것 같습니다.  
이걸로 시작하면 편하겠지만... 저는 추천드리지 않겠습니다. 받아서 둘러보니까 커스텀 가능한 부분들이 많이 빠져있더군요.

저는 그냥 테마 저장소에서 fork를 해서 제 저장소로 직접 옮기겠습니다.😀 fork를 하게되면 별다른 작업 없이 간단하게 바로 제 저장소가 생성되면서 그 곳에 프로젝트를 복사해서 가져올 수 있습니다.  
<br>

### Fork 하기

오른쪽에 Fork버튼을 눌러줍니다. 이제 보니 3천번이나 Fork되었네요.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%209.33.38.png?Web=1)  
<br>

**여기가 중요합니다.** Repository name을 `<GH_USERNAME>.github.io` 이 형식으로 바꿔줍니다. 여기서 `GH_USERNAME`은 GitHub 유저네임을 나타냅니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%209.36.20.png?Web=1)  
이름을 저렇게 짓는 이유는 저희는 Github Pages를 사용할 것이기 때문입니다. Github Pages는 `<GH_USERNAME>.github.io` 형식의 저장소를 만들면 자동으로 호스팅 서비스를 만들어줍니다. 유저네임으로 지어야 하기 때문에 계정당 한개씩만 가능하죠.  
<br>

이제 저장소가 생성되었습니다. (저는 이미 만들어져 있었습니다.🙂)  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.07.06.png?Web=1)  
<br>

이렇게 fork를 하게되면 좋은점은 나중에 원본 저장소 에서 업데이트가 이루어지면 제가 복사해온 저장소에 동기화 작업을 할 수 있다는 것입니다! git을 통해서 릴리즈된 업데이트를 간단하게 적용할 수 있는거죠.

물론 동기화 할 때 병합 작업은 진행해야 합니다만, 이건 나중에 다루도록 하겠습니다.  
<br>

### GitHub Pages 설정하기

그리고 이건 해도 안해도 상관없는데 더 진행하기 전에 저는 `master`브랜치를 `main`으로 바꿔줬습니다.  
`Github`의 기본 브랜치명인 `master`가 노예제를 연상시킨다는 이유로 `main` 으로 변경되었는데요; 이게 바뀐지가 좀 되었거든요... 그래서 저는 `main`이 더 익숙해서 바꿔줬습니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.08.49.png?Web=1)  
<br>

Settings에서 Pages를 들어가면 Github Pages에 대한 설정을 할 수 있습니다. 활성화된 상태도 볼 수 있고, 브랜치를 바꿀 수도 있습니다. 만약 현재 브랜치가 `main`이 아니라면 `main`으로 바꿔줍니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.11.39.png?Web=1)  

## 로컬에서 작업하기
---
아직 끝이 아닙니다. 이제 받은 프로젝트 내부를 깔끔하게 정리 해줘야 하는데요. 웹에서 할 수도 있겠지만 저는 VSCode로 로컬에서 작업을 진행하겠습니다.

다음과 같이 표시된 버튼을 누르면 저장소 주소를 복사할 수 있습니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.17.09.png?Web=1)  
<br>

터미널로 원하는 작업 폴더에 들어가서 `git clone`을 통해 저장소를 복사해줍니다.

```zsh
git clone 복사한주소
```

> `git clone`을 하는 방법은 전부 아실거라고 믿겠습니다... 혹시나 모르시는 분들을 위해 추후에 블로그에 올리도록 하겠습니다.

### VSCode로 작업하기

VSCode를 실행합니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.23.09.png?Web=1)  
<br>

> VSCode에는 작업을 더 편하게 할 수 있는 여러가지 기능과 정말 다양한 확장 플러그인이 있습니다. 여기서는 일단 기본적인 것만 설명하겠습니다. 기회가 된다면 추후에 확장 플러그인에 대해서도 설명하도록 하겠습니다.  

<br>

`Open Folder`를 눌러서 저장소를 열어줍니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.24.33.png?Web=1)  

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.26.57.png?Web=1)  
<br>

터미널 프로그램으로 작업 폴더를 열거나, 아니면 VSCode에서 터미널을 열어도 상관없습니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-04%20%ec%98%a4%ed%9b%84%2010.29.18.png?Web=1)  
<br>

이제 작업 폴더를 초기화해줘야 합니다만, 이 부분은 테마 마다 구성이 조금씩 다르기 때문에 제가 설명드릴 수 있는 부분은 아니네요. 각 테마가 설명해주는 지침을 따라야 할 것 같습니다. 아마 `README.md`파일에 자세히 적혀있을 겁니다.

다행히 `Chirpy` 테마는 초기화 작업을 도와주는 스크립트가 준비되어 있어서 터미널에서 실행하면 끝입니다!  
다음의 안내를 따르면 됩니다.

> 터미널로 작업 폴더 최상위 루트에서 다음 명령어를 실행합니다.
> ```zsh
> bash tools/init.sh
> ```
> > GitHub Pages에 사이트를 배포하지 않으려면 --no-gh위 명령 끝에 옵션을 추가하세요.
> {: .prompt-info}  
>
> 위의 명령은 다음을 수행합니다.
> 
> 1. 저장소에서 일부 파일 또는 디렉토리를 제거합니다.
>    - .travis.yml
>    - 아래의 파일_posts
> 2. `--no-gh` 옵션이 제공되면 `.github` 디렉토리가 삭제됩니다. 그렇지 않으면 `.github/workflows/pages-deploy.yml.hook`의 확장자 `.hook`을 제거하여 GitHub Action 워크플로를 설정한 다음 `.github` 폴더에서 다른 파일과 디렉터리를 제거합니다.
> 3. .gitignore 에서 Gemfile.lock 항목을 제거합니다.
> 4. 변경 사항을 자동으로 저장하기 위해 새 커밋을 만듭니다.

`[INFO] Initialization successful!`라는 메시지가 나오면 성공입니다.

#### 로컬에서 Jekyll 서버 실행하기

우선 Github에 올리기 전에 로컬에서 Jekyll 서버를 실행해보겠습니다.

미리 받았던 `Gem`인 `bundler`를 이용하면 되는데요.

그 전에 우선 `Ruby`버전을 바꿔주도록 하겠습니다. `Chirpy` 테마가 최신 버전의 `Ruby`로 하니까 잘 안되더라구요... 그래서 다른 버전을 받아야 하는데 다행히 이미 준비 되어있죠? 미리 받아둔 `chruby`와 `ruby-install`을 사용하면 쉽게 받을 수 있습니다.

> 지원하는 버전에 대한 부분은 테마에 따라 다를 수 있습니다. 필요하신 분만 따라하시면 됩니다.
{: .prompt-warning}  

일단 2.x.x 버전중에 하나를 받아야 하는데 저는 2.7.6 버전을 받았습니다.

먼저 Apple Silicon Mac(M1 또는 M2)을 사용하는 경우 사용 중인 Apple 명령줄 도구(CLT) 또는 Xcode의 버전을 확인해야 합니다.
```zsh
brew config
```
`CLT:` 로 시작하는 줄을 찾으십시오 만약 `14` 로 시작한다면 다음과 같이 Ruby를 설치해야 합니다.
```zsh
ruby-install 2.7.6 -- --enable-shared
```
그렇지 않으면 추가 옵션을 사용하지 마십시오.
```zsh
ruby-install 2.7.6
```
이 작업은 몇분 정도 걸릴 수 있습니다.

설치가 완료되고 `ruby -v`을 입력하면 여전히 기존 버전이 나올 수 있습니다. 원하는 버전으로 자동 전환하는 방법은 다음과 같습니다.

> 1. 일단 작업 폴더 최상위 루트에서 `.ruby-version` 파일이 존재하는지 확인해주세요.
> ```zsh
> cat .ruby-version
> ```
> 2. 만약 없다면 다음과 같이 입력해주세요.
> ```zsh
> echo 'ruby-2.7.6' >> .ruby-version
> ```
> 3. 그리고 `ruby -v`를 입력해주세요. 원하는 버전이 나올 것입니다.

이렇게 `.ruby-version`이 적용된 폴더가 아니면 원래 설치된 최신버전이, 적용된 폴더에선 본인이 원하는 버전으로 자동 전환되서 나옵니다.  
<br>

이제 `Jekyll`을 실행해보겠습니다. `Bundler`를 이용해서 실행하면 됩니다.

서버를 처음 실행하기 전에 반드시 디펜던시(의존성)를 설치해야 합니다. 처음 한번만 해주면 됩니다.

```zsh
bundle
```

그리고 다음과 같이 실행합니다.

```zsh
bundle exec jekyll serve
```

> Ruby 버전 3.0.0 이상을 사용하는 경우 위에 명령어가 실패할 수 있습니다. webrick을 의존성에 추가하여 문제를 해결할 수 있습니다. `bundle add webrick`
{: .prompt-warning}  

> 소스 파일을 변경할 때마다 페이지를 자동으로 새로 고치는 --livereload 옵션을 적용할 수 있습니다. `bundle exec jekyll serve --livereload`
{: .prompt-tip}  

다음과 같이 실행되면 성공입니다.

```zsh
Configuration file: /Users/username/Projects/username.github.io/_config.yml
            Source: /Users/username/Projects/username.github.io
       Destination: /Users/username/Projects/username.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.202 seconds.
 Auto-regeneration: enabled for '/Users/username/Projects/username.github.io'
    Server address: http://localhost:4000
    Server running... press ctrl-c to stop.
```

이제 `http://localhost:4000`으로 접속하면 로컬에서 블로그를 확인할 수 있습니다. 아무것도 없지만요ㅎㅎ

## 마무리
---
이제 Jekyll 블로그가 전부 설치되었습니다. 남은건 작업물을 빌드, 배포해주고 자신에게 맞는 설정을 적용해서 포스트를 작성하시면 됩니다. 다음 글에서 빌드 및 배포를 위한 git 동기화와 github actions를 알아보겠습니다.

## 다음 글
---
[Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포](https://leejh95.github.io/posts/github-blog-build-deploy/)

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>