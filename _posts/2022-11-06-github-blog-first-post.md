---
date: 2022-11-06 16:43:04 +0900
title: Github Pages와 Jekyll을 사용해서 나만의 블로그 만들어보기🚀 - 첫 포스팅하기
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
이제 블로그를 만들었으니 첫 포스팅을 해봐야겠죠. 적용한 테마는 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy)입니다. 사용할 에디터는 VSCode입니다.

> <https://chirpy.cotes.page/posts/write-a-new-post/>  
> ⬆️ 이 글을 참고했습니다.

## 파일 생성 및 이름 지정
---

- 블로그 포스팅은 `_posts` 폴더에 마크다운 파일로 생성합니다.
- 파일 이름은 반드시 `yyyy-mm-dd-파일이름.마크다운` 형식으로 지정합니다.
- 날짜를 제외한 파일이름은 영어로 작성하고, 공백은 `-`로 대체합니다.
- 마크다운 파일은 `.md` 혹은 `.markdown` 확장자를 사용합니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-06%20%ec%98%a4%ed%9b%84%205.40.58.png?Web=1)  

> 날짜를 제외한 파일 이름을 작성할때는 되도록 영어로만 작성하는 것이 좋은 것 같습니다. (숫자x) 제 테마 저장소의 이슈를 둘러보니 관련 이슈가 좀 있는 것 같더군요. 이 부분은 확실하진 않습니다.🤔

## 서문(Front Matter) 작성
---
만들어진 파일 안쪽을 작성해보죠.

기본적으로 포스트 상단에 아래와 같이 Front Matter를 작성해야 합니다.

```markdown
---
title: First Post
date: 2022-11-06 12:00:00 +0900
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [tag1, tag2]     # 태그는 항상 소문자여야 합니다.
---
```

- `title` : 포스트 제목
- `date` : 포스트 작성 날짜 및 시간
    - 포스트의 게시 날짜를 정확하게 기록하려면 반드시 timezone을 지정해야 합니다.(한국시간 기준 +0900)
    - _config.yml 파일에서도 timezone을 설정해야 합니다.
- `categories` : 포스트 카테고리
    - 이곳에 카테고리를 지정하면 카테고리 페이지가 자동으로 생성됩니다.
    - 최상위 카테고리와 하위 카테고리를 지정할 수 있습니다.
    - 하위 카테고리는 선택사항입니다.
- `tags` : 포스트 태그
    - 이곳에 태그를 지정하면 태그가 자동으로 생성됩니다.
    - 태그는 항상 소문자여야 합니다.

> 포스트의 `layout`은 기본적으로 설정되어 있으므로 Front Matter에 `post`를 추가할 필요가 없습니다.
{: .prompt-tip}

기본적으로 Front Matter에는 위와 같은 항목들이 있습니다.

이후 나머지는 추가사항 입니다.

### 글쓴이 정보
---
글쓴이 정보는 일반적으로 Front Matter에 입력할 필요가 없으며 기본적으로 `_config.yml` 파일의 `social` 첫 번째 항목 `name`에서 가져옵니다.

### 목차(Table of Contents, TOC)
---
기본적으로 목차 ( TOC ) 는 게시물의 오른쪽 패널에 표시됩니다. 마크다운의 헤더(`##`, `###`) 을 인식해서 자동으로 생성됩니다. 전역적으로 끄려면 `_config.yml`로 이동하여 `toc`변수 값을 `false`로 설정 합니다. 특정 게시물에 대한 TOC를 해제하려면 게시물의 Front Matter에 다음을 추가하세요.

```markdown
toc: false
```

### 댓글(Comments)
---
댓글 기능의 전역 스위치는 `_config.yml` 파일의 `comments.active` 변수에 의해 정의됩니다. 이 변수에 대한 댓글 시스템을 선택하면 모든 게시물에 대한 댓글이 켜집니다.

특정 게시물에 대한 댓글을 닫으려면 게시물의 Front Matter 에 다음을 추가하세요.

```markdown
comments: false
```

### 수학 수식(Mathematical Expressions)
---
웹사이트 성능상의 이유로 수학 기능은 기본적으로 로드되지 않습니다. 그러나 다음을 통해 활성화할 수 있습니다.

```markdown
math: true
```

### Mermaid
---
Mermaid 는 훌륭한 다이어그램 생성 도구입니다. 게시물에서 활성화하려면 Front Matter 블록에 다음을 추가하세요.

```markdown
mermaid: true
```

### 미리보기 이미지(Preview Image)
---
게시물 콘텐츠 상단에 미리보기 이미지를 추가하려면 이미지에 대해 `path`, `width`, `height` 및 `alt`속성을 지정합니다.

```markdown
image:
  path: /assets/images/preview.jpg
  width: 1000
  height: 500
  alt: Preview Image
```

### 고정된 게시물(Pinning Posts)
---
하나 이상의 게시물을 홈페이지 상단에 고정할 수 있으며, 고정된 게시물은 출시일에 따라 역순으로 정렬됩니다.

```markdown
pin: true
```

## 내용(Content) 작성하기
---
이제 Front Matter를 작성했으니, 내용을 작성해봅시다.

기본적으로 Markdown 문법을 사용하면 끝입니다!! 또 추가적으로 Chirpy 테마의 글자 표현식이 따로 있습니다. 이러한 것들은 제가 쓴 글을 참고해주세요!😄😄  

- [마크다운(Markdown) 기본 정리🔥🔥🔥](https://leejh95.github.io/posts/markdown-basic/)
- [Chirpy 테마의 Text and Typography 정리🔥🔥🔥](https://leejh95.github.io/posts/chirpy-theme-basic)

한번 간단하게 작성해볼게요.

```markdown
---
title: First Post
date: 2022-11-06 12:00:00 +0900
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [tag1, tag2]     # 태그는 항상 소문자여야 합니다.
---

## Hello World!
---
만나서 반갑습니다. 첫 포스팅입니다.

## Markdown 문법...
---
...
```

> 내용에서 헤더는 `##`이 가장 큰 헤더로 시작하는 것이 좋습니다. `#`은 가장위에 글제목으로 사용되기 때문입니다. `#`을 사용하면 목차가 제대로 생성되지 않을 수 있습니다.
{: .prompt-warning}  
> 헤더의 첫 부분은 숫자로 시작하면 안됩니다. 예를 들어 `## 1. Hello World!`는 하위 목차가 제대로 생성되지 않는 버그가 있습니다. (`2022-11-06` 기준)
{: .prompt-warning}

이제 내용을 작성했으니 저장 후, 변경사항을 푸시하고 확인 하면됩니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-06%20%ec%98%a4%ed%9b%84%207.31.19.png?Web=1)
_첫 포스트!_

> VSCode의 여러 기능으로 더욱 편하게 작성할 수도 있습니다! 기회가 된다면 추후에 포스팅하겠습니다.
{: .prompt-tip}

## 마무리
---
Github Pages와 Jekyll로 블로그 만들기 튜토리얼 끝!!😄😄  
기본적인 것은 전부 마무리된 것 같습니다...  
이제 마크다운으로 자유롭게 포스트를 작성해갈 수 있습니다!! 읽어주셔서 감사합니다.

## 참고
---
> - <https://jekyllrb.com/>
> - <https://www.irgroup.org/posts/jekyll-chirpy/>
> - <https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/>
> - <https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#how-to-install-different-versions-of-ruby-and-switch-between-them>
> - <https://github.com/cotes2020/jekyll-theme-chirpy>
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>
> - <https://kim-eun-ji.github.io/etc/2021-05-18-ga/>