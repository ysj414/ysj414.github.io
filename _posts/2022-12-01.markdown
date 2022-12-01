---
layout: post
titile: C 언어 연산자 우선순위
date: 2022-12-01 15:02:30 +0900
category: sample
---

# post-sample
>  C 언어 연산자 우선순위

다음 코드에서 line 37~39에 있는 문장의 처리 결과는 어떻게 될까?
```c
 32 /* Parse and check an LLC header */
 33
 34 int
 35 l2_llcParse (unsigned char * frame, struct LLC_Frame_s * llc)
 36 {
 37   llc->dsap = *frame++;
 38   llc->ssap = *frame++;
 39   llc->ctrl = *frame++;
 40
 41   return (((llc->dsap == LLC_DEFAULT_ADDR)
 42     && (llc->ssap == LLC_DEFAULT_ADDR)
 43     && (llc->ctrl == LLC_DEFAULT_CTRL)) ||
 44        ((llc->dsap == LLC_DSAP_ADDR)
 45     && (llc->ssap == LLC_SSAP_ADDR)
 46     && (llc->ctrl == LLC_DEFAULT_CTRL)));
 47 }
```
정답은 후위연산자 -> 참조연산자 순으로 진행되어 먼저 frame의 주소 값을 1 증가시킨뒤 frame의 값을 참조한다.

C언어 연산자우선순위 참고자료: 
https://coding-factory.tistory.com/635
