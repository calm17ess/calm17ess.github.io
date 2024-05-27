---
layout: post
title: Nautilus에서 'New document' 탭 만들기
author: calm17ess
subtitle: How to create a new document in Nautilus
categories: Linux
banner:
  image: /assets/images/banners/posts_banners/linux.jpg
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  subheading_style: "color: gold"
tags: [gnome, nautilus, new document, document, new file, linux]
---

## 미리보기

기본적으로 노틸러스(파일 편집기)에서 우클릭을 해보면 아래와 같은 메뉴가 나오게 된다. '새 문서' 같은 탭은 보이지 않는다.
![image](https://github.com/calm17ess/calm17ess.github.io/assets/168082113/d4178dfd-f707-4475-8cb9-3d13ef75558b)

하지만 아주 간단한 설정을 하면 아래와 같은 화면을 띄울 수 있다.
![image](https://github.com/calm17ess/calm17ess.github.io/assets/168082113/c3462a1b-2bbf-4915-a711-8eb3302e6d2c)

## 해결 방법

1. Home/Templates 폴더로 이동한다.
   ![image](https://github.com/calm17ess/calm17ess.github.io/assets/168082113/d5ffa18f-ade3-4a1a-987b-b86ae9eae447)

2. Templates 폴더에 원하는 파일을 만들어준다(.md, .txt 등)
   a. 만드는 방법은 간단하게 콘솔을 연 후
   `cd Templates` => `touch 원하는 파일.확장자`
   ![image](https://github.com/calm17ess/calm17ess.github.io/assets/168082113/baf85e31-f11f-471c-9d06-2234c67788e0)

3. 다른 폴더로 이동 후 우클릭을 해서 확인을 해보면 정상적으로 작동함을 확인할 수 있다.
   ![image](https://github.com/calm17ess/calm17ess.github.io/assets/168082113/1b243507-9718-48ab-92d3-565d881505c0)
