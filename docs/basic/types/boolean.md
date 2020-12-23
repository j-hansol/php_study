# 논리형

논려형은 참 또는 거짓 값을 가지는 매우 단순한 유형입니다.
주로 조건문, 반복문 등에서 이용합니다.

논리형은 아래와 같이 참, 거짓을 표협합니다.
```php
// 아래의 경우 첫 글자를 대문자로 사용했으나 PHP에서는 대소문자를 구분하지 않습니다.
$a = True;
$b = False;
```

외와 같이 논리형 값을 직접 지정할 수도 있지만 비교 연산자를 이용하여 참/거짓 여부를 계산할 수도 있습니다.
이 결과는 제어 및 반복문에서 이용할 것입니다.
```php
<?php
    $input_action = "출력";
    
    if( $input_action == "출력" ) {
        echo "콘텐츠 내용을 출력합니다.";
    }
    
    $displayed = $input_action == "출력";
    // 이렇게 사용할 필요는 없습니다.
    if( $displayed == TRUE ) {
        echo "다시 한 번 더 출력합니다.";
    }
    
    // 이렇게 사용하는 것이 좋습니다.
    if( $displayed ) {
        echo "다시 한 번 더 출력합니다.";
    }
?>
```

## 논리형으로의 변환
다른 자료를 논리형으로 명지적으로 변경할 경우 캐스트 연산자를 사용하세요. 사실 연산자, 함수, 제어문 등에서는 필요한 경우 자동으로 변환하기 때문에 명시적으로 변환할 필요가 없습니다.

논리형으로 변환 시 아래의 경우에는 거짓(False)로 변환됩니다.
* 정수형 자료 0
* 실수형 자료 0.0
* 공백 또는 "0" 문자열
* 요소가 없는 배열
* NULL
* 테그를 포함하지 않은 SimpleXML 객체

이해를 위해 아래의 예제를 입력하여 실행해보세요.
```php
<?php
    var_dump((bool) "");        // bool(false)
    var_dump((bool) 1);         // bool(true)
    var_dump((bool) -2);        // bool(true)
    var_dump((bool) "foo");     // bool(true)
    var_dump((bool) 2.3e5);     // bool(true)
    var_dump((bool) array(12)); // bool(true)
    var_dump((bool) array());   // bool(false)
    var_dump((bool) "false");   // bool(true)
?>
```