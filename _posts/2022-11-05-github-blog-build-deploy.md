---
date: 2022-11-05 20:56:37 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos] ## Only lowercase
---

1. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 준비 단계](https://leejh95.github.io/posts/github-blog-prepare-to/)
2. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - Ruby, Jekyll 설치하기](https://leejh95.github.io/posts/github-blog-ruby-jekyll/)
3. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 테마 고르고 적용하기](https://leejh95.github.io/posts/github-blog-theme/)
4. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 빌드 및 배포](https://leejh95.github.io/posts/github-blog-build-deploy/)
5. [Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징](https://leejh95.github.io/posts/github-blog-customizing/)

## 빌드 및 배포
---
저번글에서는 로컬에서만 사이트를 접속해봤는데요. 인터넷에서 접속할 수 있는 블로그를 만들기 위해서는 정적 파일을 호스팅 서버에 배포해야 합니다. 정적 파일은 프로젝트에서 빌드해야 하죠.

뭔가 복잡하죠?? 하지만 괜찮습니다. Github Pages는 지정된 브랜치에 변경사항을 푸시해주면 모든 과정을 자동으로 해줍니다. 한번 살펴볼까요?

프로젝트 루트에 있는 .github 폴더에는 Github Actions에 대한 설정 파일이 있습니다. 그 안에있는 `pages-deploy.yml`파일을 보면 아래와 같이 빌드와 배포에 대한 설정이 있습니다.

```yaml
name: "Build and Deploy"
on:
  push:
    branches:
      - main
      - master
    paths-ignore:
      - .gitignore
      - README.md
      - LICENSE

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

# Allow one concurrent deployment
concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3
        with:
          fetch-depth: 0
          # submodules: true
          # If using the 'assets' git submodule from Chirpy Starter, uncomment above
          # (See: https://github.com/cotes2020/chirpy-starter/tree/main/assets)

      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v1

      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3 # reads from a '.ruby-version' or '.tools-version' file if 'ruby-version' is omitted
          bundler-cache: true

      - name: Build site
        run: bundle exec jekyll b -d "_site${{ steps.pages.outputs.base_path }}"
        env:
          JEKYLL_ENV: "production"

      - name: Test site
        run: |
          bundle exec htmlproofer _site --disable-external --check-html --allow_hash_href

      - name: Upload site artifact
        uses: actions/upload-pages-artifact@v1
        with:
          path: "_site${{ steps.pages.outputs.base_path }}"

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v1
```

복잡하니 모든것을 아실 필요는 없습니다. 중요한건 `build`와 `deploy`라는 두개의 job이 있고, `build`에서는 지정된 명령어를 통해 정적 파일을 빌드하고, `deploy`에서는 지정된 액션을 통해 빌드된 파일을 Github Pages에 배포한다는 것입니다.

### Git Push
---
지정된 브랜치에 변경사항이 푸시되면 자동으로 빌드 및 배포를 진행된다고 했는데요. 이를 위해서는 Git을 사용할 수 있어야 합니다.

그럼 Git으로 Push를 해보죠. 단계는 다음과 같습니다.

> 1. 프로젝트에서 변경사항이 생긴다.
> 2. 변경사항을 Staging Area에 올린다.
> 3. Staging Area에 올린 변경사항을 Commit한다.
> 4. Commit한 변경사항을 Github에 Push한다.

이렇게 진행해봅시다. 터미널을 열고 프로젝트 최상위 경로로 이동합니다. (VSCode 터미널을 사용해도 됩니다.)

> 1. 프로젝트에서 변경사항이 생긴다.

변경사항은 저번글에서 파일을 수정했으니 반드시 생겼을 것입니다.

> 2. 변경사항을 Staging Area에 올린다.

```zsh
git add .
```

스테이징 영역에 모든 변경사항을 올렸습니다.

> 3. Staging Area에 올린 변경사항을 Commit한다.

```zsh
git commit -m "첫 커밋"
```

커밋을 할때는 반드시 커밋 메시지를 작성해야 합니다. 처음이니까 일단 아무거나 작성하겠습니다.

> 4. Commit한 변경사항을 Github에 Push한다.

```zsh
git push
```

이렇게 하면 Github에 Push가 됩니다.

### VSCode에서 Git 사용하기
---
VSCode를 사용하면 Git도 매우 간단하게 사용할 수 있습니다. VSCode에서는 Git을 사용하기 위해 `Source Control` 탭을 사용합니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-05%20%ec%98%a4%ed%9b%84%2011.37.32.png?Web=1)  

`Source Control` 탭을 열고, `+` 버튼을 눌러서 변경사항을 Staging Area에 올립니다. 그리고 입력칸에  Commit 메시지를 작성하고, `Commit` 버튼을 눌러서 커밋을 합니다. 그리고 `Sync` 버튼을 눌러서 Push를 하면 됩니다.

### Github Actions
---
푸시가 되었다면 Github Actions가 자동으로 빌드 및 배포를 진행합니다. 무슨일이 벌어지는지 확인해봅시다.

자신의 저장소에서 `Actions` 탭을 열고, `Build and Deploy`를 클릭합니다.  
![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-05%20%ec%98%a4%ed%9b%84%2011.48.50.png?Web=1)  

이곳에 진행중인 워크플로우가 나타납니다. 각 워크플로우를 클릭해보면 현재 진행중인 작업을 실시간으로 확인할 수 있습니다.

빌드 및 배포가 전부 완료되었다면 한번 본인의 Github Pages를 확인해봅시다. `https://username.github.io`로 접속하면 됩니다. (e.g. <https://leejh95.github.io>)

## 마무리
---
다음 글에서는 블로그를 커스터마이징 해보겠습니다.😀

## 다음 글
---
[Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 커스터마이징](https://leejh95.github.io/posts/github-blog-customizing/)

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>