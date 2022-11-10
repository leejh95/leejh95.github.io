---
date: 2022-11-09 11:03:07 +0900
title: VSCode로 기능을 활용하여 Github 블로그 포스트를 작성해보기 + 웹에서도 작성해보기
categories: [Tutorial, Github Blog]
tags: [git, ruby, jekyll, github pages, github blog, chirpy theme, macos, vscode] ## Only lowercase
---

## 시작
---
VSCode의 다양한 기능을 활용하면 더 쉽고 편하게 Github 블로그 포스트를 작성할 수 있습니다.

## 스니펫으로 자동완성
---
스니펫(코드 조각)은 루프나 조건문과 같이 반복되는 코드 패턴을 더 쉽게 입력할 수 있게 해주는 템플릿입니다. 스니펫을 사용하면 포스트를 작성할 때 반복되는 코드를 더 쉽게 입력할 수 있습니다.

![image](https://code.visualstudio.com/assets/docs/editor/userdefinedsnippets/ajax-snippet.gif)
_Snipet을 사용하여 반복되는 코드를 더 쉽게 입력할 수 있습니다._

### Front Matter 자동완성
---
Front Matter를 작성할 때마다 매번 수동으로 써 넣어야 하는 불편함을 해소할 수 있습니다. 특히 날짜를 구하는게 정말 귀찮죠...

하지만 스니펫을 쓰면 정말 간단하게 Front Matter를 작성할 수 있습니다.😀

한번 자동으로 패턴을 만들고 날짜가 알아서 입력되게 해보도록 하죠.

#### Markdown 파일을 열고 스니펫을 만들어보자

일단 원하는 언어의 스니펫을 커스텀 해야합니다. 아무 Markdown 파일을 열고 `Cmd + Shift + P` 또는 `Ctrl + Shift + P` 를 눌러서 `snippets`을 입력하고 `Snippets: Configure User Snippets`를 선택합니다.
![image](https://dsm01pap003files.storage.live.com/y4malyLsL1Jy6wJjtuQF6WMIkWCeO4A-XWV8mRbREJXTrugwIyNcJvsqt_HNPj0G8_HH8W9vchocwfFpDRaSnL-NrMGj29vjdshsiTPFRwnZis_FhoqJfcRpMSIrTRbcGe5vf9TfWjm4xDNI-lhdiMNV3-GJHuhL9OYBOzLW7Z8zwyGVXPdDbse6Bhaz1JNPsmc?width=733&height=174&cropmode=none)  
<br>

이때 이미 만들어진 파일을 선택할 수도 있습니다. `markdown.json`을 선택하면 됩니다.
![image](https://dsm01pap003files.storage.live.com/y4mL-Hc__8lb6P8LOiFAQct8Q4-8d7KNdUTXf1bkQyLAmmVbtm4lhQNHvYaycp_L7CWguqcg7ZV2LMQu894vVui10uxl8l3JiUpxC0fkWY09mp2c3L5pQ7D71f8eXLp25BHubUM6Tcr8tTz0cnXRBjt_8dllH18NxNQMkwZS-QR2vPjQna_0PGznR2u6pt5Yzw1?width=735&height=142&cropmode=none)  
<br>

`markdown.json` 파일이 열렸다면 다음과 같이 스니펫을 만들어 보겠습니다.

```json
{
    "Frontmatter": {
		"prefix": ["frontmatter", "fm", "front-matter"],
		"body": [
			"---",
			"date: ${CURRENT_YEAR}-${CURRENT_MONTH}-${CURRENT_DATE} ${CURRENT_HOUR}:${CURRENT_MINUTE}:${CURRENT_SECOND} +0900",
			"title: $1",
			"categories: [$2]",
			"tags: [$3] ## Only lowercase",
			"---"
		],
		"description": "Frontmatter"
	}
}
```

- `prefix`는 스니펫을 사용할 때 입력할 단어입니다. `.md` 파일에서 `frontmatter`, `fm`, `front-matter`를 입력하면 스니펫이 자동으로 입력됩니다.
- `body`는 스니펫을 입력했을 때 입력될 내용입니다. date를 `${CURRENT_YEAR}-${CURRENT_MONTH}-${CURRENT_DATE} ${CURRENT_HOUR}:${CURRENT_MINUTE}:${CURRENT_SECOND} +0900` 이렇게 구성해놓으면 현재 날짜를 자동으로 입력해줍니다.
- `$`와 숫자로 구성된 변수는 스니펫을 사용한 후 추가로 입력해야할 부분을 알려줍니다. `tab`키를 누르면 다음 변수로 이동합니다.
- `description`은 스니펫의 설명입니다.

#### 한 번 사용해보자

이제 스니펫을 사용해보겠습니다.

`.md` 파일에서 `fm` 또는 `frontmatter` 를 입력하고 `Ctrl` \+ `Space` 키를 눌러보세요.  
![image](https://dsm01pap003files.storage.live.com/y4m9RyUo1-4cymBLiukS4kwP4tK-YohZRq3p0T3W7iVIOJIcPVOJ-OUikncMB9ocTaIzLrcvo42YsQs5PcGAr82DV9TVIPkBoHsc94qx4R3DStYda-9Mps0KuqoRCNs6Fd_jnNQKtaVRvGtsu56cFVFjcPLWZhq3Ti5BtUtBNfyFM7aj9FdoHUZNiKfyWeyNw9X?width=600&height=252&cropmode=none)
_예시 이미지입니다._

나머지 부분을 입력하고 `tab`키를 눌러서 다음 변수로 이동하면서 입력하면 됩니다.

> 참고로 커스텀 스니펫 외에도 기본으로 준비된 스니펫을 사용할 수 있습니다. `Ctrl` \+ `Space` 키를 눌러서 한 번 사용해보세요.
{: .prompt-tip}

> 스니펫에 대한 더 자세한 설명은 공식문서를 참고해주세요.  
> <https://code.visualstudio.com/docs/editor/userdefinedsnippets>
{: .prompt-info}

## Markdown 미리 보기 기능
---
포스트를 작성할 때 Jekyll로 서버를 실행시켜서 실제 화면을 보면서 작업할 수 있습니다. 하지만 서버를 실행시켜야 한다는게 조금 번거롭죠. 심지어 다른 PC로 작업을 할때는 다시 Jekyll 환경을 잡아줘야 하고요. 그래서 다른 방법을 찾아보았습니다.

VSCode에서는 Markdown 파일을 미리 보기할 수 있는 기능을 제공합니다. 블로그 전체를 확인할 수는 없지만, 포스트 내용에 집중할 때는 괜찮은 기능입니다.

#### 미리 보기 기능 사용하기

`.md` 파일을 열고 `Ctrl` \+ `Shift` \+ `V` 또는 `Cmd` \+ `Shift` \+ `V` 키를 눌러서 `markdown`을 입력하고 `Markdown: Open Preview to the Side`를 선택하면 됩니다.

![image](https://dsm01pap003files.storage.live.com/y4mOyKnNxie6MPdupOL4yyhcZjE5KlXx2PR6ocI1b07iOthimRT9XcwIIc0OpmwgsR61tOKglE-Gk7Mig1Wg3ZcgLkll31bEVMXjWKEOUvlGO955fA-Wq37_zRWIq3dYKMkHSLXw0mNgjb1T0G8shgZGLI0WbMR27Xhef4NzYSgcqO3WHKJXVdQ9rpk-9US1Rxm?width=998&height=312&cropmode=none)  

![image](https://dsm01pap003files.storage.live.com/y4mg1squOrreAeyPv8LwiX5TieGHF3mVgKS52JUF5wJQKKL0gwixiXqDAZhoSQw_yri64a16ODGvvHnqKdYtwm1fIpU3znSD7j0bfJnHlfv81QiTg6-x4fb1mAHDSfjls9sLC_uu2l8IzaX5AAfDbThCd6s8oQ_nMmx9PS-fusxGlc-nGAiZ5AO26hsAmqfJ-Go?width=1634&height=703&cropmode=none)
_예시 이미지입니다._

끝입니다!! 간단하죠?😀 이제 서버를 실행하지 않고 실시간으로 미리 보기를 보면서 글을 작성할 수 있습니다. 물론 기본 기능이라 테마 자체의 표현식은 적용되지 않지만, 가볍게 작업할 때는 괜찮은 기능입니다.

## 웹에서 VSCode 사용하기
---
VSCode는 웹에서도 사용할 수 있도록 지원해주고 있습니다. 웹에서 사용하면 다른 PC에서도 그대로 VSCode를 사용할 수 있고, VSCode를 설치하지 않아도 됩니다. 또 가볍게 브라우저에서 작업을 할 수 있어서 정말 괜찮은 서비스죠.

#### 웹에서 VSCode를 사용해보자

<https://vscode.dev/>에 접속하면 VSCode를 웹에서 사용할 수 있습니다. 처음 접속하면 로그인을 해야하는데, GitHub 계정으로 로그인하면 됩니다. 로그인을 하면 VSCode를 사용할 수 있습니다.

> 다른 곳에서 VSCode를 사용하기 전에 원래 쓰던 VSCode의 설정을 동기화 해놓으면 좋습니다. 설정을 동기화하면 VSCode를 사용하는 어느곳에서나 동일한 설정을 사용할 수 있습니다. (동기화하려면 'Github' 또는 'Microsoft' 계정이 필요합니다.)  
> ![image](https://dsm01pap003files.storage.live.com/y4mQxkGdoW2mpax8fmoI8NmGCzGhlDPux9WonjQRfFsnzZvFGRRvo0iBEtNMipm8V7zEtQulw3LEmNyDjHaJJCpycE0aaUizsB10mMarJllC5tBmNCEUHyYg01hgr1iS2mxzjygw5g6-aObRVmIzLlgO038kS6QjdzfQU95tN2VeCJq_kbL0CuOGXww-xK8XmM9?width=388&height=308&cropmode=none)
{: .prompt-tip}

![image](https://dsm01pap003files.storage.live.com/y4meSeiOF8kTuUBsE3nd89oat3Ix3-Jn9ysMHEoU4CWEuK49xjMLTuKTEVFfkHBXae0URbsRaLMtKYQomJgX7kWqSimv_MOFulWM62mAmHA39rrGwuizhHvonCq5ldN5hRecLGfPnzV5onWYK2Q3BgRDLiuSKI8_LqDygoYTomDawSCewmACSp-FtGlHlcRYXNH?width=2612&height=1842&cropmode=none)
_웹 버전 VSCode입니다._  
<br>

설정을 동기화해주면 좋습니다.
![image](https://dsm01pap003files.storage.live.com/y4m_XQ0Db-LO7yfriz1AvPxAJDV6MSvvfQxhcc9l5fx0BICkC3sBDg3cL4eiBSMByxfFQEviC0F0e8n_iQ0PGcNfD0aQF2oXT3Uvr_RjGbrtt6q3cqFaeF-BsYUUSz4cEAez3Ace9tRRQrTmxl--7AhNTRLMSBwucGTz_tNIta3nYDO-7e2jZX6A7OtDYmE_gTE?width=680&height=428&cropmode=none)  
<br>

#### 웹에서 포스트를 작성해보자.

제 블로그의 원격 저장소를 열고 글을 써보겠습니다.

![image](https://dsm01pap003files.storage.live.com/y4mnQUxJLIm3bclWtaocYamuSAxOUoBqs3uEOglGHWzIu_D-zRArnHK0vL8ArHa2ZZZYiTIWzK_ENXm9eHHToe1JFlLcfzFb9L5MeqVTJNdr4ehc7_Zs0MYk5lY2LRs0p9oCzkY7SfYbyn1ir5dacNPq9SY3a05OIJW4Vkc8X_kKWyljkzoKTBWeU9XvSqXYEXa?width=2066&height=718&cropmode=none)
_저장소를 가져오는 기능을 지원하고 있습니다._  

![image](https://dsm01pap003files.storage.live.com/y4mh5lZ1bs2yrZPvrOOy3FWEqiWdf623KndeGjWXJzJJ1SBa-WJVZmCiy6YMNUtrvbNIuoIaVlqC8DYXTErvqB3sqXY7z2CieL05D9dujDAcXUpiGHrpouZUG3cn3WyDXYJfsMW2Aitp-9VxOMqAk2S4Npy-TBCaYyzfgzeH4ZYZcgczpWa6vqzr0MEJM4FpnFX?width=1910&height=1066&cropmode=none)
_Github에서 원격 저장소를 가져왔습니다!_  

![image](https://dsm01pap003files.storage.live.com/y4mvZi9bMcO0OXaYv7aetfe4d0Hzii2vkPIivFgU0-FVQf1BhiB8uUyawVZBfvvbQra3oSAblykT0QkCH2t5wldPC0fOLaquJsgLR5AUjJPBpjd6Zdi4_PZAJq67WPYKB_zNrqHRqfmOnYP1vvQHJf5cXFOReqmn5tG-L-w-cVILgN3cRDC7u0KsjojzQ5E7gc4?width=2876&height=1468&cropmode=none)
_이제 글을 작성할 수 있습니다._  
<br>

이제 어디서든 인터넷과 브라우저만 있으면 포스트를 작성할 수 있게 되었습니다. 👏👏👏

## 참고
---
> - <https://code.visualstudio.com/>
