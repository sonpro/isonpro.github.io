---
layout : post
title : AMPERSAND나 특수 문자를 갖는 데이타를 INSERT하는 방법
---

<p>테스트 테이블 생성 </p>



<pre class="prettyprint"><code class="language-sql hljs ">SQL&gt; <span class="hljs-operator"><span class="hljs-keyword">CREATE</span> <span class="hljs-keyword">TABLE</span> test_str(
val varchar2(<span class="hljs-number">10</span>)
);</span></code></pre>

<p>– 테이블에 아래와 같이 특수문자를 인서트 할경우 </p>


```sql
sql> insert into test_str values('Q&A');
```

<p>a의 값을 입력하십시오:  <br>
– 이런 문장이 나옵니다..  <br>
– 특수문자를 갖는 데이터를 인서트 하기 위해서는  <br>
– 다음과 같은 세 가지 해결 방법이 있습니다.</p>



<pre class="prettyprint"><code class="language-sql hljs "><span class="hljs-operator"><span class="hljs-keyword">SET</span> DEFINE OFF
– <span class="hljs-keyword">SQL</span>*Plus에서 <span class="hljs-keyword">SET</span> DEFINE OFF나 <span class="hljs-keyword">SET</span> SCAN OFF를 실행하여
– Substitution Variable(&amp;)을 Turn Off시킨다.

<span class="hljs-keyword">SQL</span>&gt; <span class="hljs-keyword">SET</span> DEFINE OFF
<span class="hljs-keyword">SQL</span>&gt; <span class="hljs-keyword">INSERT</span> <span class="hljs-keyword">INTO</span> test_str <span class="hljs-keyword">VALUES</span>(‘Q&amp;A’);</span>

SQL&gt; <span class="hljs-operator"><span class="hljs-keyword">SELECT</span> * <span class="hljs-keyword">FROM</span> test_str;</span>
VAL
——
Q&amp;A

<span class="hljs-operator"><span class="hljs-keyword">SET</span> DEFINE %</span></code></pre>

<p>– SET DEFINE ON 상태로 유지 시키면서 Substitution Variable을  <br>
– 다른 Non-Alphanumeric 문자나 Non-White Space 문자(*, % 등등)로  <br>
– 대체시킨다.</p>



<pre class="prettyprint"><code class="language-sql hljs ">SQL&gt; <span class="hljs-operator"><span class="hljs-keyword">SET</span> DEFINE %
<span class="hljs-keyword">SQL</span>&gt; <span class="hljs-keyword">INSERT</span> <span class="hljs-keyword">INTO</span> test_str <span class="hljs-keyword">VALUES</span>(‘Q&amp;A’);</span></code></pre>

<hr>

<p>SET ESCAPE ON <br>
– SET ESCAPE ON 상태에서(DEFINE은 &amp;로, SCAN은 ON 상태로 유지)  <br>
– 특수 문자 앞에 ESCAPE 문자인 BACKSLASH(‘\’)를 붙인다.</p>



<pre class="prettyprint"><code class="language-sql hljs ">SQL&gt; <span class="hljs-operator"><span class="hljs-keyword">SET</span> <span class="hljs-keyword">ESCAPE</span> <span class="hljs-keyword">ON</span>
<span class="hljs-keyword">SQL</span>&gt; <span class="hljs-keyword">SHOW</span> <span class="hljs-keyword">ESCAPE</span>
<span class="hljs-keyword">ESCAPE</span> “\” (hex <span class="hljs-number">5</span>c)
<span class="hljs-keyword">SQL</span>&gt; <span class="hljs-keyword">INSERT</span> <span class="hljs-keyword">INTO</span> test_str <span class="hljs-keyword">VALUES</span> (‘Q\&amp;A’);</span></code></pre>

<blockquote>
  <p>문서에 대하여  <br>
  - 강좌 URL : <a href="http://www.gurubee.com/m/lecture/1148">http://www.gurubee.com/m/lecture/1148</a>  <br>
  - 구루비 강좌는 개인의 학습용으로만 사용 할 수 있으며, 다른 웹 페이지에 게재할 경우에는 출처를 꼭 밝혀 주시면 고맙겠습니다.~^^  <br>
  - 구루비 강좌는 서비스 제공을 위한 목적이나, 학원 홍보, 수익을 얻기 위한 용도로 사용 할 수 없습니다.</p>
</blockquote>
