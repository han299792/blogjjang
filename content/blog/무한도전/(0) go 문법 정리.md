---
title: 
date: 2025-04-29
tags:
  - golang
draft: false
---
>Struct + Constructor 

관례적으로 constructor 함수는 NewTypeName() 형식으로 짓고, struct 포인터를 반환한다. 
-> excelhandler 생성, excelservice를 주입해서 사용

> Method receiver

struct에 메소드 붙일 때, `func (리시버 이름 리시버 타입)`