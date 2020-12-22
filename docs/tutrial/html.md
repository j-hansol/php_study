# HTML에 포함된 스크립트

아래 코드와 같이 HTML 속에 PHP가 포함되어 있으면 웹 서버는 해당 코드를 실행하여 코드를 대체하여 브라우즈로 전송하게 됩니다.
```php
<!DOCTYPE html>
<html>
    <head>
        <title>PHP 예제</title>
    </html>
    <body>
        <?php
            echo "<p>안녕하세요. PHP</p>";
        ?>
    </body>
</html>
```

줄바꿈은 그렇게 중요하지는 않습니다. PHP는 C 또는 Java와 같이 명령의 끝을 나타내는 세미콜론(;)으로 구분하기 때문입니다.
그래서 위 코드를 아래와 같이 기록할 수도 잇습니다.
```phpregexp

```