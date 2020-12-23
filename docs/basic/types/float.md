# 실수형

실수형(Floating point)은 숫수 이하 자리를 가진 숫자로 정수형에 비해 넓은 범위의 숫자 표현이 가능합니다. 숫자의 표현은 아래와 같습니다.
```php
<?php
    $a = 1.234; 
    $b = 1.2e3; 
    $c = 7E-10;
    $d = 1_234.567; // 천단위 구분, 7.4.0 이상에서 지원함
?>
```
## 실수형의 정밀도 문제
일반적으로 CPU는 실수형보다 정수를 처리하기 쉽도록 설계되었습니다. 그래서 실수를 표현할 때 정밀도와 관련하여 여러 오류가 발생할 수 있습니다.
정밀도관련 오류는 연산의 복잡도에 따라 증가할 수 있습니다. 프로그램 개발 시 이런 오류의 증가부분을 고려하여 작성해야 합니다.

또한 0.1과 0.7 등 2진수로 소수를 정확하게 표현하기 어려운 숫자의 경우 정밀도 문제가 발생할 수 있습니다. 이로 인해 아래와 같은 연산의 수행 시 우리가 기대하지 않았던 결과가 나올 수 있습니다. (이 부분은 정수 부분에서도 언급되었습니다.)
"(0.1+0.7) * 10"의 결과를 8로 기대했을 것입니다. 그러나 정밀도 문제로 7.99999.... 형태로 계산됩니다. 이런 이유로 정수로 변환 시 ㅕ7로 계산된 것입니다.
```php
<?php
echo (int) ( (0.1+0.7) * 10 ); // 7이 출력됨
?>
```

따라서 실수형의 마지막(끝자리) 숫자는 신뢰하지 소숫점 아래의 숫자를 직접 비교하지 않도록 하십시오.

## 다른 자료형을 실수로 변환
다른 자료를 실수로 명시적으로 변환하르면 캐스트 연산자((floatr))를 사용하세요. 이 역시 정수와 마찬가질초 연산과정, 함수, 제어 및 반복문에서 필요한 경우 자동 변환됩니다.

### 문자열로부터 변환
이 부분도 정수와 동일한 방식으로 변환됩니다.
```php
<?php
    echo (int)"1234.56"        // 결과 : 1234.56
    echo (int)"01234.56"       // 결과 : 1234.56
    echo (int)"0x1234.56"      // 결과 : 0
    echo (int)"0b1234.56"      // 결과 : 0
    echo (int)"12a34.56"       // 결과 : 12
    echo (int)"a1234.56"       // 결과 : 0
    
    $a = "12345.67";
    echo $a + 0             // 결과 : 12345.67
?>
```

### 다른 자료형으로부터의 변환
다른 형태의 자료형은 먼저 정수로 변환한 다음 실수로 변환합니다.