---
layout: post
title: "Dos Batch 1줄에서 2이상의 명령을 실행"
tagline: "This post demonstrates post content styles"
categories: til
image: /thumbnail-mobile.png
author: "Bart Simpson"
meta: "Springfield"
---

dos batch command 는 현재까지도 윈도우에서 쉽게 사용할 수 있는 스크립트다. 리눅스나 같은 계열의 맥에서만 이런 스크립트를 쓸수 있는 것은 아니다. 이전의  Dos 에서 부터 간단한 스크립트가 내장되어 있었고, 윈도우10 에서도 여전히 살아있다.

java Spring 을 사용하기 위해 eclipse 를 실행시키고, 그곳의 소스파일을 관리하기 위해 git 을 사용하고 있다.


<pre><code>cmd /k "git status & dir & copy za.bat d:\temp"</code></pre>
<br/>

위의 명령은 다음과 같은 작동을 한다.

1. cmd 로 커맨드 창을 열고,
2. git status 명령을 실행하고 (/k 옵션때문에 명령을 수행한 후 창을 닫지 않는다)
3. dir 명령을 실행해서 파일들을 화면에 보여주고,
4. 현 디렉토리에 있는 za.bat 파일을 D:\temp 디렉토리로 복사한다.

커맨드 창에서 커서가 깜박이며 입력상태를 나타낸다.

이 상태에서 내가 원하는 명령

<pre><code>git all --all .</code></pre>

을 사용할 커맨드창에서 키보드 입력을 통해 수행할 수 있다.

스프링 프로젝트의 디렉토리에 gitst.bat 이름으로 배치파일을 만들어두고 그 내부에

<pre><code>cmd /k git status & D:\sts-3.9.4.RELEASE\STS.exe</code></pre>

입력해 두면 gitst.bat 를 더블 클릭하면 커맨드창이 떠서 git 명령을 기다리고 있고, STS 의 eclipse 가 떠서 작업상태가 된다. 한번에 둘 이상의 프로그램을 실행시켜 둘때 cmd /k 과 & 옵션을 잘 사용하면 편하게 개발환경을 만들 수 있다.


![View the Light](https://user-images.githubusercontent.com/3831276/40552763-9e132ea0-607b-11e8-881c-8e29c24b8721.jpg "더 빠르게 개발환경 시작하기")


