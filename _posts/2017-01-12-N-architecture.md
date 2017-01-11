---
layout : post
title : N계층 서버 아키텍처
---


Web Server & WAS(Web Application Server)
웹브라우저로 전송하는 컨텐츠 중에는 CSS(Cascading Style Sheet), Images, Javascript 등 정적인 요소도 존재하며, 이러한 컨텐츠를 전송하는 웹 서버가 전담한다

웹 기반의 환경에서 어플리케이션 서버 역할을 수행하는 서버를 WAS라고 하며, WAS는 Servlet 등의 자바 컴포넌트를 이용해 비즈니스 로직을 수행한다

클라이언트와 데이터베이스 사이에 2계층이 존재하므로 전체 4계층으로 구성한다

>browser - web server - was server - DB
