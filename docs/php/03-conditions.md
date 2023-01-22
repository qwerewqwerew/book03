---
layout: post
title: 03-조건문,반복문
date: 2023-01-10
parent: PHP
---
1. TOC
{:toc}
--

## 01 conditions.php

### 01-1 참과 거짓

1. C\xmapp\htdocs 폴더에 conditions.php 파일생성

```php
<?php
   $result = 1 < 3;
   echo $result;
?>
```

1. localhost:8080/conditions.php 의 결과를 확인한다.

```php
<?php
   $result = 1 > 3;
   echo $result;
?>
```

1. localhost:8080/condition.php 의 결과를 확인한다.
1. true는 1 이므로 이전의 결과는 1이 출력되었으나 false 는 화면에 아무것도 나오지 않는다.
1. ` echo $result;` 를 주석처리 후 조건문을 `echo $result2 == false;` 로 변경해본다
1. 화면에 1이 출력된다.

---

### 01-2 대소문자의 구분

```php
$first_name = 'mango';
$last_name = 'kim';

if($first_name == 'Mango'){
    echo '진실입니다';
} else{
    echo '거짓입니다';
}

```

1. `$first_name = 'mango';` 와 `$first_name == 'Mango'` 를 다르게 판단하여
   `거짓입니다';` 가 출력된다

2. `if($first_name == 'Mango' && $last_name='kim')` 으로 조건을 변경해본다.
3. 둘다 참이어야 참으로 판단되므로 거짓이 나온다.
4. `if($first_name == 'Mango' || $last_name='kim')` 으로 조건을 변경해본다.
5. 둘중 하나만 참이면 참으로 판단되므로 진실이 나온다
6. `if($first_name == 'Mango' and $last_name='kim')` 으로 조건을 변경해본다.
7. php 에서만 사용되는 조건식으로 둘다 참이어야 한다
8. `if($first_name == 'Mango' or $last_name='kim')` 으로 조건을 변경해본다.
8. php 에서만 사용되는 조건식으로 둘다 참이어야 한다
10. `if($first_name == 'Mango' xor $last_name='kim')` 으로 조건을 변경해본다.
11. php 에서만 사용되는 조건식으로 두개가 서로 다르면 참이다

---

## 02. array.php

1. array.php 생성
> 배열의 문법
> `$배열이름 = array();`
> 배열을 생성하고 값 넣기

### 02-1 배열의 생성

```php
<?php

$fruits=array();
$fruits[0]="사과";
$fruits[1]="바나나";
$fruits[2]="한라봉";

echo $fruits
?>

```

1. 아래와 같은 에러가 출력된다
   <img src='{{"/assets/img/error0.png" | relative_url }}'>
2. 자바스크립트와 마찬가지로 배열의 값은 원소 단위로 꺼내어야 한다.
  `echo $fruits[0]` 으로 작성하거나 반복문을 이용한다.
3. echo 를 주석처리한다.

### 02-2

1. isset 으로 확인해보자
   > #### isset
   >
   > isset( $var1, $var2, ... );
> 변수 설정 여부 확인 (준비되었는지)
> $var가 설정되었는지 확인하고, 설정되었으면 TRUE, 설정되지 않았으면 FALSE를 반환
   > {: .block-tip }

```php
...
//echo $fruits
if (isset($fruits[3])) {
  echo $fruits[3];
} else {
  echo '과일 배열에는 3번째 값이 없다';
}

```

<img src='{{"/assets/img/php-return.jpg" | relative_url }}'>

---


### 02-3 배열의 조작

> #### count()
>
> 배열의 개수를 반환
> count($test)
>
> {: .block-tip }

```php

<?php
  $fruits = array('apple', 'banana', 'orange');
    for($i=0;  $i<count($fruits); $i++){
        echo $fruits[$i].'<br/>';
    }
?>

```

## 연관배열 Associative Array

### 02-4 foreach

```php

<?php
    foreach($fruits as $item){
        echo $item.'<br/>';
    }
?>

```

```php

<?php
$prices = array();
$prices['apple'] = 1000;
$prices['banana'] = 2000;
$prices['orange'] = 1500;

foreach ($prices as $key => $price) {
  echo $key . "_" . $price . "</br>";
}
?>

```

$key는 배열의 요소를 의미하고 $price 는 값을 하나씩 의미한다

<img src='{{"/assets/img/php-30.jpg" | relative_url }}'>

### 02-5 

위의 배열을 줄여보기
아래처럼 한줄로 줄일수 있다.
```
// $array["apple"] = 1000;  // 연관 배열 요소 추가
// $array["banana"] = 2000; 
// $array["orange"] = 1500;

$array = array('apple' => 1000, 'banana' => 2000, 'orange' => 1500);

foreach ($array as $key => $price) {
  echo $key . "::" . $price . "</br>";
}
```
>
>#### 이전까지는 배열의 인덱스 번호를 활용하여 선언후 키에 할당하였으나 문자열에 직접 할당함


---

## 03 Loop

### 03-1 while

  {: .note }
  > while(조건식){
  >    실행문
  > }

```php
<h1>Loop</h1>
<h2>while</h2>
<?php
$i = 0;
while ($i < 5) {  //i가5미만일때 까지 실행
    echo ($i++) . "<br/>";  //i=i+1
}
?>
```
실행
![]({{'/assets/img/php55.jpg'| relative_url}} ) 

### 03-2 do/while
  {: .note }
  > while(조건식){
  >    실행문
  > }

```php
<h2>do/while</h2>
<?php
$j = 0;
do {
    echo ($j++) . "<br/>";
} while ($j < 5);
?>
```
실행
![]({{'/assets/img/php56.jpg'| relative_url}} )

### 03-3 for
{: .note }
>
>for(초기값;조건;증감식){실행문}

```php
<h2>for</h2>
<?php
for ($k = 0; $k < 5; $k++) {
    echo $k . '<br/>';
    echo "{$k}<br/>"; //쌍따옴표 작성시 변수명과 문자열을 묶어서 출력할수 있다
}
?>

```
실행
![]({{'/assets/img/php57.jpg'| relative_url}} )


### 03-4 foreach
{: .note }
>foreach(배열 as 변수){실행문}
>

```php
<?php
$results = array(0, 5, 6, 7, 8); //5개의 값이있는 배열 생성
foreach ($results as $result) {
    echo "변수 \$result의 값은 {$result} 입니다. <br/>";
}
?>
```
실행 - 배열의 요소들을 하나씩 출력함
![]({{'/assets/img/php58.jpg'| relative_url}} )


### 03-5 foreach(associative array)
{: .note-title }
> 키와 값이 있는 배열
>

```php
<?php
$scores = array(
    "국어" => 80,
    "영어" => 90,
    "수학" => 100,
    "과학" => 95,
);
foreach ($scores as $key => $score) {
    echo "배열 \$scores에서 키값 '{$key}'에 대한 값은 {$score}입니다.<br>";
}
?>

```
![]({{'/assets/img/php59.jpg'| relative_url}} )
출력
![]({{'/assets/img/php60.jpg'| relative_url}} )
---

### 문제

1. 배열을 이용해 과목성적의 합계와 평균 구하기

```php

<?php
//배열을 이용하여 합계, 평균 구하기 ,원소는 0부터 시작
//과목별 점수
$eng=99;
$computer=80;
$program=85;
//과목별 점수를 배열에 할당
$score[0]=90;
$score[1]=80;
$score[2]=85;

$sum =0 ;
for($a=0; $a<=2; $a++){
    $sum+=$score[$a];
}
$avg=$sum/3;

echo "과목점수: $score[0],$score[1],$score[2], <br>";
echo "합계: $sum,평균:$avg <br>";
?>

```
1. 출력
![]({{'/assets/img/php46.jpg'| relative_url}} )

---
