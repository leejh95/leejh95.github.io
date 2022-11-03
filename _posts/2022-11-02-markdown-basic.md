---
date: 2022-11-02 15:43:52 +0900
title: 마크다운(Markdown) 기본 정리🔥🔥🔥
categories: [Notes, Markdown]
tags: [markdown, github] ## Only lowercase
image:
  path: https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/markdown_logo.jpg?Web=1
  alt: Markdown
---

## 시작
---
> **마크다운(Markdown) 이란?**
>
> _마크다운(Markdown)은 일반 텍스트 문서에 서식 요소를 추가하는 데 사용할 수 있는 가벼운 마크업 언어입니다. 2004년 John Gruber 가 만든 마크다운(Markdown)은 현재 세계에서 가장 인기 있는 마크업 언어 중 하나입니다._
>
> **마크다운(Markdown)의 특징**
>
> _장점_
> - _문법이 쉽다._
> - _다양한 플랫폼에서 지원한다._
> - _HTML로 변환할 수 있다._
>
> _단점_
> - _표준이 없다. (많은 마크다운 표현방식이 존재한다.)_
> - _모든 HTML 마크업을 대체하지 못한다._

마크다운(Markdown)은 정말 많은 곳에서 사용중인 언어입니다. 깃헙 저장소(Repository)에 대한 정보를 기록하는 `README.md`파일도 마크다운(Markdown)문서죠. 나중에라도 배워두면 쓸모가 많으니 기본적인 문법을 한번 정리해보겠습니다.😄😄😄

## 글머리(Headers)
---
글머리를 표현할 때 사용합니다.

```markdown
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

> #### Result ⬇️
> ---
> # H1
> <h2 data-toc-skip>H2</h2>
> <h3 data-toc-skip>H3</h3>
> <h4>H4</h4>
> <h5>H5</h5>
> <h6>H6</h6>

## 줄바꿈(개행)
---
문장의 줄바꿈(개행)을 하고 싶으면 문장 끝에 띄어쓰기를 2번 하면 됩니다.

```markdown
마크다운(Markdown) 이란?  
마크다운(Markdown)은 일반 텍스트 문서에 서식 요소를  
추가하는 데 사용할 수 있는 가벼운 마크업 언어입니다.
```

> #### Result ⬇️
> ---
> 마크다운(Markdown) 이란?  
> 마크다운(Markdown)은 일반 텍스트 문서에 서식 요소를  
> 추가하는 데 사용할 수 있는 가벼운 마크업 언어입니다.

## 인용문(BlockQuote)
---
인용문을 표현할 때 사용합니다.

```markdown
> 가져온 인용문을 이런식으로 적으면...  
> This is a blockquote with two paragraphs.
```

> #### Result ⬇️
> ---
> > 가져온 인용문을 이런식으로 적으면...  
> > This is a blockquote with two paragraphs.

\+ 아래처럼 중첩할 수도 있습니다.

```markdown
> This is the first level of quoting.
> > consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> > > Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> > > > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse  
> > > > id sem consectetuer libero luctus adipiscing.
```

> #### Result ⬇️
> ---
> > This is the first level of quoting.
> > > consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> > > > Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> > > > > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse  
> > > > > id sem consectetuer libero luctus adipiscing.

## 목록(List)
---
### 순서가 있는 목록(Ordered List)

순서가 있는 목록을 표현할 때 사용합니다.

```markdown
1. 첫번째
2. 두번째
3. 세번째
```

> #### Result ⬇️
> ---
> 1. 첫번째
> 2. 두번째
> 3. 세번째

### 순서가 없는 목록(Unordered List)

순서가 없는 목록을 표현할 때 사용합니다. (`*`, `+`, `-`를 사용할 수 있습니다.)

```markdown
* 첫번째
+ 두번째
    - 111
- 세번째
    * 222
    * 333
        + 444

```

> #### Result ⬇️
> ---
> * 첫번째
> + 두번째
>     - 111
> - 세번째
>     * 222
>     * 333
>         + 444

### 정의가 있는 목록(Definition List)

정의가 있는 목록을 표현할 때 사용합니다.

```markdown
term
: definition
```

> #### Result ⬇️
> ---
> term
> : definition

## 코드(Code)
---
코드를 표현할 때 사용합니다.

### 인라인 코드(Inline Code)

원하는 부분을 인라인 코드로 표현할 때 사용합니다.

```markdown
`code`
```

> #### Result ⬇️
> ---
> `code`

### 블록 코드(Block Code)

코드 블록을 표현할 때 사용합니다.

```markdown
```code```
```

> #### Result ⬇️
> ---
> ```code```

### 블록 코드(Block Code) - Syntax Highlighting

코드 블록에 언어를 지정하여 Syntax Highlighting을 할 수 있습니다.

    ```javascript
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```

> #### Result ⬇️
> ---
> ```javascript
> var s = "JavaScript syntax highlighting";
> alert(s);
> ```

## 수평선(Horizontal Rule)
---
수평선을 표현할 때 사용합니다.

```markdown
---
* * *
***
*****
- - -
---------------------------------------
```

> #### Result ⬇️
> ---
> ---
> * * *
> ***
> *****
> - - -

전부 같은 수평선을 표현합니다.

## 링크(Link)
---
### 인라인 링크(Inline Link)

인라인 링크를 표현할 때 사용합니다.

```markdown
[내 깃헙 블로그가기](https://leejh95.github.io, "My blog")
```

> #### Result ⬇️
> ---
> [내 깃헙 블로그가기](https://leejh95.github.io, "My blog")

### 참조 링크(Reference Link)

참조 링크를 표현할 때 사용합니다.

```markdown
[내 깃헙 블로그가기][1]

[1]: https://leejh95.github.io "My blog"
```

> #### Result ⬇️
> ---
> [내 깃헙 블로그가기][1]

[1]: https://leejh95.github.io "My blog"

### 자동 연결(Automatic Link)

자동 연결을 표현할 때 사용합니다.

```markdown
<https://leejh95.github.io>
```

> #### Result ⬇️
> ---
> <https://leejh95.github.io>

## 이미지(Image)
---
### 인라인 이미지(Inline Image)

인라인 이미지를 표현할 때 사용합니다.

```markdown
![이미지](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1)
```

> #### Result ⬇️
> ---
> ![이미지](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1)

### 참조 이미지(Reference Image)

참조 이미지를 표현할 때 사용합니다.

```markdown
![이미지][1]

[1]: https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1
```

> #### Result ⬇️
> ---
> ![이미지][1]

[1]: https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1

### 이미지 링크(Image Link)

이미지 링크를 표현할 때 사용합니다.

```markdown
[![이미지](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1)](https://leejh95.github.io)
```

> #### Result ⬇️
> ---
> [![이미지](https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1)](https://leejh95.github.io)

### 이미지 사이즈(Image Size)

이미지 사이즈를 조절할 수 있습니다.

```markdown
<img src="https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="이미지"></img>
```

> #### Result ⬇️
> ---
> <img src="https://olphschool-my.sharepoint.com/personal/d16571_365v_me/Documents/githubblog/images/sample.png?Web=1" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="이미지"></img>

## 강조(Emphasis)
---
### 이탤릭(Italic)

이탤릭을 표현할 때 사용합니다.

```markdown
*이탤릭*
_이탤릭_
```

> #### Result ⬇️
> ---
> *이탤릭*
> _이탤릭_

### 볼드(Bold)

볼드를 표현할 때 사용합니다.

```markdown
**볼드**
__볼드__
```

> #### Result ⬇️
> ---
> **볼드**
> __볼드__

### 취소선(Strikethrough)

취소선을 표현할 때 사용합니다.

```markdown
~~취소선~~
```

> #### Result ⬇️
> ---
> ~~취소선~~

### 이탤릭 + 볼드 + 취소선(Italic + Bold + Strikethrough)

강조 표현식을 중첩해서 사용할 수도 있습니다.

```markdown
***이탤릭 + 볼드***  
___이탤릭 + 볼드___  
**_이탤릭 + 볼드_**  
__*이탤릭 + 볼드*__  
~~***이탤릭 + 볼드 + 취소선***~~  
~~___이탤릭 + 볼드 + 취소선___~~  
~~**_이탤릭 + 볼드 + 취소선_**~~  
~~__*이탤릭 + 볼드 + 취소선*__~~
```

> #### Result ⬇️
> ---
> ***이탤릭 + 볼드***  
> ___이탤릭 + 볼드___  
> **_이탤릭 + 볼드_**  
> __*이탤릭 + 볼드*__  
> ~~***이탤릭 + 볼드 + 취소선***~~  
> ~~___이탤릭 + 볼드 + 취소선___~~  
> ~~**_이탤릭 + 볼드 + 취소선_**~~  
> ~~__*이탤릭 + 볼드 + 취소선*__~~

## 참조
---
> * <https://www.markdownguide.org/>
> * <https://gist.github.com/ihoneymon/652be052a0727ad59601#12-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4%EC%9D%98-%EC%9E%A5-%EB%8B%A8%EC%A0%90>
