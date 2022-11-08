---
date: 2022-11-07 10:27:56 +0900
title: Github 블로그 이미지 속도를 위한 CDN 적용과 클라우드 사용하기
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos, google drive, onedrive] ## Only lowercase
---

## CDN 이란?
---
Content Delivery Network의 약자인 CDN은 지리적 제약 없이 전 세계 사용자에게 빠르고 안전하게 콘텐츠를 전송할 수 있는 콘텐츠 전송 기술을 의미합니다. CDN은 각 지역에 캐시 서버를 분산 배치해서 원본 데이터를 미리 저장해놓고, 근접해있는 사용자에게 캐시 데이터를 빠르게 전송해줍니다.

Github 저장소에 이미지 등 파일을 업로드하면, 원본 데이터가 있는 서버와의 물리적인 거리 제한때문에 사용자가 이미지를 느리게 받아올 수 있습니다. 이를 해결하기 위해 CDN을 사용하면, 사용자가 이미지를 받아올 때 원본 데이터가 있는 서버가 아닌, 근접한 CDN 서버에서 빠르게 이미지를 받아올 수 있습니다.

## CDN 적용하기
---
여러가지 CDN 서비스가 있는데요. 다행히도 Github 블로그를 이용중이라면 `jsdelivr`이라는 서비스를 무료로 사용할 수 있습니다. 사용법도 매우 간단합니다!!

Github 저장소에 업로드한 file의 경로(file_path)를 아래와 같이 구성하여 원하는 이미지 url을 구성하면 됩니다.

e.g.) https://cdn.jsdelivr.net/gh/github_user_name/repo_url@branch_name/file_path

한 번 제 블로그 이미지로 적용해보겠습니다.

```markdown
![image](https://cdn.jsdelivr.net/gh/leejh95/leejh95.github.io@main/assets/img/rocket.png)
_프로젝트 assets/img에 있는 rocket.png 이미지를 CDN을 이용해 불러온 결과입니다._
```

> #### Result ⬇️
> ---
> ![image](/assets/img/rocket.png)
> _프로젝트 assets/img에 있는 rocket.png 이미지를 CDN을 이용해 불러온 결과입니다._

### +Chirpy Theme에서 CDN 사용하기
---
제가 사용중인 Chirpy Theme에서는 이미지를 CDN을 자동으로 붙여주는 기능을 제공합니다. `_config.yml` 파일에 아래와 같이 `img_cdn`에 주소를 설정해주면 됩니다.

```yaml
...
# e.g. 'https://cdn.com'
img_cdn: https://cdn.jsdelivr.net/gh/leejh95/leejh95.github.io@main # CDN 주소

# the avatar on sidebar, support local or CORS resources
...
```

이제 이미지 url을 `/assets/img/rocket.png`로 설정하면, 자동으로 `https://cdn.jsdelivr.net/gh/leejh95/leejh95.github.io@main/assets/img/rocket.png`로 변환되어 이미지가 불러와집니다.

```markdown
![image](/assets/img/rocket.png)
```

> #### Result ⬇️
> ---
> ![image](/assets/img/rocket.png)

## 이미지 용량 관리를 위해 클라우드 저장소를 사용하자
---
이미지 로딩속도는 어느정도 해결했습니다. 하지만 이제 용량 문제가 남아있죠...

Github 블로그를 운영하다 보면, 이미지를 포함한 자료들을 저장소에 올리게 됩니다. 하지만... 점점 저장소의 용량이 꽉차게 되겠죠. (Github는 1기가 까지만 무료입니다.)

이런 문제를 해결하기 위해, 이미지를 저장소에 직접 올리지 않고 클라우드에 업로드한 후, 블로그에서는 클라우드에 업로드된 이미지를 가져다 쓰는 방식을 사용해보겠습니다.

### 클라우드 저장소 선택
---
일단 클라우드 저장소를 골라야 합니다. 저는 Google Drive와 OneDrive를 추천합니다. 둘 다 무료로 사용할 수 있고, 용량도 많이 제공해줍니다. (Google Drive는 15기가, OneDrive는 5기가) 둘 다 무료니까 두개 다 쓰는 것도 나쁘진 않을 것 같네요.

저는 OneDrive를 사용하겠습니다. 기본 무료 용량이 5기가지만 학생 계정이 있다면 1TB까지 무료로 사용할 수 있다고 하네요!!😄 1TB면 충분하고도 남을 것 같습니다.

학생 계정은 다니시던 대학교 이메일이 있으면 바로 가입할 수 있습니다. Ms Office 365를 받으시면 되요.

### 클라우드 저장소에 이미지 업로드 및 사용방법
---
클라우드 저장소에 이미지를 업로드하겠습니다.

저는 OneDrive를 사용하니 OneDrive를 기준으로 설명하겠습니다.

#### OneDrive에 접속합니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-08%20%ec%98%a4%ed%9b%84%204.21.14.png?Web=1)
_macOS에서 OneDrive를 접속한 화면입니다._

#### OneDrive에 이미지를 업로드합니다.
저는 다음과 같이 `githubblog` 라는 폴더를 만들어서 그 안에 넣고싶은 이미지를 전부 업로드했습니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-08%20%ec%98%a4%ed%9b%84%204.24.58.png?Web=1)

#### 이미지를 온라인으로 열어줍니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-08%20%ec%98%a4%ed%9b%84%204.26.16.png?Web=1)

#### 주소창에 있는 주소를 복사합니다.

![image](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/ScreenShot%202022-11-08%20%ec%98%a4%ed%9b%84%204.28.31.png?Web=1)

이제 복사한 주소를 블로그에 사용하면 됩니다. 쉽죠???😊

### +Chirpy 테마에서 주어진 자동 CDN 설정을 했을 때 발생하는 문제
---

> <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>  
> ⬆️ 이 분의 글을 참고하였습니다.

아마 Chripy에서 주어진 자동 CDN 설정을 했을 때 클라우드 이미지가 불러와지지 않는 문제가 발생할 것입니다...😭

바로 구글링을 해봤고, 알아낸 이유는 다음과 같습니다.

프로젝트에서 `_includes/refactor-content.html` 파일에서 잘 둘러보시면 이미지 주소를 수정하는 코드가 있습니다.

그 중에서 주소 문자열에서 `=` 문자를 기준으로 앞뒤로 나누는 코드가 있는데요. OneDrive의 주소에서는 `=` 문자가 많이 포함되어 있어서 오류가 나는 것이라고 합니다.

{% raw %}
```liquid
71 ...
72    {% assign _pair = _attr | split: '=' %}
73    {% if _pair.size < 2 %}
74      {% continue %}
75    {% endif %}
76        
77    {% capture _key %}{{ _pair | first }}{% endcapture %}
78
79    <!-- 여기가 오류가 생기는 부분 -->
80    {% capture _value %}{{ _pair | last | replace: '"', '' }}{% endcapture %}
81 ...
```
{: .nolineno}
{% endraw %}

`refactor-content.html` 안쪽 코드가 `Liquid`라는 템플릿 언어로 작성되어 있는데요... `Jekyll`에서 템플릿 처리를 할 때 사용하는 언어입니다.

이제 저 부분을 고쳐주면 되는데요. 이렇게 고쳐주면 된다고 합니다.

{% raw %}
```liquid
71 ...
72    {% assign _pair = _attr | split: '=' %}
73    {% if _pair.size < 2 %}
74      {% continue %}
75    <!-- img_cdn 사용 시 원드라이브 src 오류 해결 코드 -->
76    {% elsif _pair.size == 2 %}
77      {% capture _key %}{{ _pair | first }}{% endcapture %}
78      {% capture _value %}{{ _pair | last | replace: '"', '' }}{% endcapture %}
79    {% elsif _pair.size > 2 %}
80      {% capture _key %}{{ _pair | first }}{% endcapture %}
81      {% capture _value %}{{ _pair | slice: 1, -1 | replace: '"', '' }}{% endcapture %}
82    {% endif %}
83 ...
```
{: .nolineno}
{% endraw %}

적용해보니... 정말로 잘 되네요!👏👏👏 다행입니다.


## 참고
---
> - <https://pioneergu.github.io/posts/github-blog-jsdelivr-cdn/>

