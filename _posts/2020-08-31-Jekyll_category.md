---
layout: post
title: 지킬 블로그 카테고리 추가 - Jekyll category
excerpt: 지킬 블로그에 카테고리 기능을 추가하고, 카테고리 리스트와 글 헤더에 표시하기 기능 추가
categories: [jekyll]
tags: [jekyll, 카테고리]
last_modified_at: 2020-08-31
---

## 지킬 블로그 카테고리 추가

아직 글이 없긴 하지만, 한국사람들은 그룹핑 하는 것을 좋아한다고 하는데 나도 갑자기 그게 필요하다고 느껴졌다.

카테고리를 누르면 관련 글 리스트를 볼 수 있도록 간단하게나마 만들어 보자.
아래 그림처럼 결과물을 보면 글 헤더에 카테고리를 추가할 수 있었다.

![](https://paper-attachments.dropbox.com/s_40AE800B790B013089FC35A4CDB095E950E831337DD4DDAC9381D9D8CC92C6B6_1598855859081_image.png)


물론, 구글링을 통해서 했고, 당연히 많은 곳에서 도움을 받을 수 있다.

## 글 작성시에 카테고리 명시하기

지킬에 글을 쓰다보면, 글 맨 상단에 글에 대한 메타데이터를 넣도록 하고 있다.
타이틀, 저자, 생성일자 등등등 
여기에 이 글과 관련된 카테고리를 넣으면 착수 작업을 되었다고 볼 수 있다. 예제를 보면 아래와 같다.


    
    ---
    layout: post
    title: 지킬 블로그 총 게시글의 수는? - Jekyll blog total number of posts
    excerpt: 지킬 블로그 총 게시글의 수가 궁금하다면 이리저리 머리 굴릴 필요 없이 간단하게 구할 수 있다. Jekyll blog total number of posts
    categories: [jekyll]
    tags: [jekyll, blog, 꿀팁]
    last_modified_at: 2020-08-28
    ---
    


## 카테고리 목록 페이지 만들기

이제 카테고리가 쭉 나열되는 목록 페이지를 만들어야 한다. 
사실 여러가지 방법이 난무했지만, 제일 단순하게 한페이지에 모든 카테고리와 글을 보여주고 목차처럼 누르면 해당 영역으로 점프하도록 구현하였다. CSS를 적당히 이용하면 원하는 카테고리만 보였다 사라졌다 할 수 있지만 머 그럴 필요는 없어 보였다. 결과는 아래 그림과 같다.

![카테고리 리스트](https://paper-attachments.dropbox.com/s_40AE800B790B013089FC35A4CDB095E950E831337DD4DDAC9381D9D8CC92C6B6_1598856161804_image.png)


그럼 이런 결과를 보여주려면 어떻게 해야 하는가?
그냥 쉽게 가자. 

1. 루트 디렉토리에 category.html 을 만든다.
2. 아래 코드를 복사해 둔다.
3. 끝

<script src="https://gist.github.com/bjnhur/6d205239ba96552d16a50558958b77e8.js"></script>


- *permalink: /category/ 이부분이 실제 접근되는 주소가 된다. 즉 blog주소/category/ 이렇게 접속하면 분류 리스트가 나타난다.*
- 상단에 숫자(글의 개수)와 함께 있는 분류명을 누르면 해당 영역으로 점프하는 형태이다. #기능을 활용하고 있다.

## 글 헤더에 카테고리 표시하기

아까 그림에서 보이는 것 처럼 글 헤더에서 이 글이 어떤 카테고리에 해당 되는 글인지 알려 줄 필요가 있다.
어떻게 표시하는냐?
아래 코드를 참고하면 아주 쉽게 할 수 있다. 
핵심은 page.categories 라는 변수다. 복수 카테고리를 지정했다면 배열처럼 접근하면 된다. 한개씩

<script src="https://gist.github.com/bjnhur/714fbc8c925f102daa7bbba4b7281a56.js"></script>


- Font awesome 을 이용하여 앞에 폴더 모양의 아이콘이 추가되어 있다. ^-^

---

## 참고 글 목록
- [jekyll 블로그 tag 기능 추가](https://min9nim.github.io/2018/08/jekyll-tags/){:target="_blank"} 
- [Github Page Jekyll 에 카테고리 추가하기](https://blog.devari.kr/2019/jekyll/jekyll-category-setting){:target="_blank"} 
- [블로그 카테고리와 태그 목록 구성하기](https://devinlife.com/howto%20github%20pages/category-tag/){:target="_blank"} 

> 블로그 카테고리는 게시물을 제목이나 유형으로 분류할 때 사용되며, 블로그에 대한 일반적인 주제를 글 묶음을 위해 사용된다. 전문가들이 초보 블로거들에게 하는 충고 중의 하나가 블로그에서 다룰 주제를 몇가지로 한정해서 주제를 가진 블로그를 구성하라는 것이다. 이 때, 카테고리는 블로그가 다룰 주제들이 될 수 있다. 카테고리도 태그와 같이 여러개의 카테고리를 입력할 수도 있다. 이런 경우는 방문자들이 혼동을 느낄 수 있으니 카테고리 구성을 잘 해야 할 것이다.



