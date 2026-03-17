### Введение в работу с куками
```php
<?php
setcookie('test', 'abcde');
?>
<?php
echo $_COOKIE['test'];
?>
```

### Проблема установки кук
```php
<?php
setcookie('str', 'eee');
var_dump($_COOKIE['str']);
?>
```

### Мгновенная установка кук
```php
<?php
if (!isset($_COOKIE['str'])) { 
    setcookie('str', 'eee');
    $_COOKIE['str'] = 'eee';
}

echo $_COOKIE['str']; 
?>
```

### Счетчик обновления страницы на куках
```php
<?php
if (!isset($_COOKIE['start-time'])) {
    setcookie('start-time', time());
} else {
    echo $_COOKIE['start-time'] = time() - $_COOKIE['start-time'];
}
?>
```

### Время жизни куки
```php
<?php
setcookie('meow', 'meow-meow', time() + 60 * 60 * 24 * 30);
?>

<?php
setcookie('meow', 'meow-meow', time() + 60 * 60 * 24 * 30 * 12);
?>

<?php
setcookie('meow', 'meow-meow', time() + 60 * 60 * 24 * 30 * 12 * 10);
?>
```

### Время жизни куки
```php
<?php
setcookie('meow', 'meow-meow', time());
print_r($_COOKIE['meow']);
?>
```

### Мгновенное удаление кук
```php
<?php
if (isset($_COOKIE['meow'])) {
    setcookie('meow', '', time());
    unset($_COOKIE['meow']);
}
var_dump($_COOKIE['meow']);
?>
```   
