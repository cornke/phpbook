### Метод HTTP запроса
//1 и 2
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

$method = $_SERVER['REQUEST_METHOD'];
var_dump($method);
```

### HTTP заголовки запроса
//1, 2 и 3
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

echo $_SERVER['HTTP_ACCEPT'];
echo $_SERVER['HTTP_ACCEPT_LANGUAGE'];
var_dump($_SERVER);
```

### Массив заголовков HTTP запроса
//1
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

$arr = getallheaders();

foreach($arr as $elem) {
echo $elem . '<br>';
}
```

### Заголовки HTTP ответа
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

echo header('Content-Type: text/plain');
echo header('Content-Type: text/X-hey');
```

### Заголовки HTTP ответа
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

echo header('Content-Type: text/plain');
echo header('Content-Type: text/X-hey');
```

### Проблема с заголовками HTTP ответа
//1
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

	echo 'abc';
?>

<?php
	header('Content-Type: text/html');
?>
```

//2
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');
?>

<?php
header('Content-Type: text/html');
?>
<!DOCTYPE html>
<html>
	<head>

	</head>
	<body>
		text
	<body>
<html>
```

### Проблема с заголовками HTTP при include
//1
```php
<?php
	function func1() {
		echo '1';
	}
 
<?php
	function func2() {
		echo '2';
	}

<?php
	include 'file1.php';
	include 'file2.php';
	header('Content-Type: text/html');
```

//2
```php
<?php
	function func1() {
		echo '1';
	}
	function func2() {
		echo '2';
	}
 
<?php
	include 'file.php';
	header('Content-Type: text/html');
```

### Отдача стартовой строки HTTP ответа 
```php
<meta charset="utf-8">
<?php
/**
 * @var $link mysqli
 */

require_once('connect.php');

$arr = ['a', 'b', 'c'];
$key = $_GET['key'];

if (isset($arr[$key])) {
    echo $arr[$key];
} else {
    echo 'error';
}
```

### Отдача стартовой строки HTTP ответа
```php
<?php
 $arr = ['a', 'b', 'c'];
 $key = $_GET['key'];
 
 if (isset($arr[$key])) {
  echo $arr[$key];
 } else {
  http_response_code(404);
  echo 'error';
 }
?>
```

### Отдача статуса HTTP ответа
```php
<?php
 $arr = ['a', 'b', 'c'];
 
 if (isset($_GET['key'])) {
  $key = $_GET['key'];
  
  if (isset($arr[$key])) {
   echo $arr[$key];
  } else {
   http_response_code(404);
   echo 'Not Found';
  }
 } else {
  http_response_code(403);
  echo 'Forbidden';
 }
?>
```