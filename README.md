
# PHP-VIXCAR-SDK

> PHP версия SDK для работы с API проекта VixCar.

## Содержание:

1. Установка
2. Базовые вызов 
3. Описание методов
     * Auth
          - login
          - logout
          - join
     * Services
          - get
          - count
          - price
     * Cars
          - get
          - create
          - delete
          - update
          - count
     *  Booking
         - get
         - create
         - delete
         - update
         - count
         - close
      * History
         - get
         - count
     * Account
         - get
         - delete
         - restore
         - name
         - surname
         - middleName
         - connections
 
## Установка

Необходимые зависимости:

1. PHP >= 7.1
2.  [php-curl-class/php-curl-class](https://packagist.org/packages/php-curl-class/php-curl-class): ^8.5

> composer require danil005/php-vixcar-sdk:dev-master

## Базовый вызов

```php
<?php  
  
require("vendor/autoload.php");  
  
use VixCarSdk\Client;  

$clientID = 2;
$token = "saffnapo";
$urlApi = "http://carplace.ru/api/v1";  

$client = new Client($clientId, $token, $urlApi);  

print_r($client->account()->get()); // is array
```

## Описание методов

> Все методы основаны на REST API проекта VixCar.Ru.

---

### Auth

---

#### Auth > login

Авторизация пользователя.

```php
$client->auth()->login($username, $password);
```

Описание аргументов:

|Название|Тип данных|Описание|По умолчанию
|--|--|--|--
|$username|string|Логин пользователя.|Обязательно указывать.
|$password|string|Пароль пользователя.|Обязательно указывать.

---

#### Auth > join

Создания нового пользователя.

```php
$client->auth()->join($username, $password, $email, $name, $surname, $middleName, $numberPhone)
```

Описание аргументов:

|Название|Тип данных|Описание|По умолчанию
|--|--|--|--
|$username|string|Логин пользователя.|Обязательно указывать.
|$password|string|Пароль пользователя.|Обязательно указывать.
|$email|string|E-mail пользователя.|Обязательно указывать.
|$name|string|Имя пользователя.|Обязательно указывать.
|$surname|string|Фамилия пользователя.|Обязательно указывать.
|$middleName|string|Отчество пользователя.|Обязательно указывать.
|$numberPhone|string|Номер телефона пользователя.|Обязательно указывать.

---

#### Auth > logout

Выйти из учетной записи (завершить сессию).

```php
$client->auth()->logout()
```

---

### Services

---

#### Services > get

Получить информацию о сервесах.

```php
$client->services()->get();
```

---

#### Services > count

Получить кол-во сервисов.

```php
$client->services()->count();
```

---

#### Services > price

Получить прейскурант сервиса.

```php
$client->services()->price($id);
```

Описание аргументов:

|Название|Тип данных|Описание|По умолчанию
|--|--|--|--
|$id|integer|ID сервиса.|Обязательно указывать.

---

### Cars

---

#### Cars > get

Получить информацию о всех автомобилях.

```php
$client->cars()->get();
```

---


---

#### Cars > create

Добавить новый автомобиль пользователю.

```php
$client->cars()->create($carName, $carNumber, $vin);
```

Описание аргументов:

|Название|Тип данных|Описание|По умолчанию
|--|--|--|--
|$carName|string|Название марки автомобиля.|Обязательно указывать.
|$carNumber|string|Государственный номер автомобиля.|Обязательно указывать.
|$vin|string|VIN автомобиля.|Обязательно указывать.

---

#### Cars > delete

Удалить автомобиль пользователю.

```php
$client->cars()->delete($id);
```

Описание аргументов:

|Название|Тип данных|Описание|По умолчанию
|--|--|--|--
|$id|integer|ID автомобиля.|Обязательно указывать.

---

#### Cars > update

Изменить информацию о автомобиле пользователю.

```php
$client->cars()->update($id, $carName, $carNumber, $vin);
```

Описание аргументов:

|Название|Тип данных|Описание|По умолчанию
|--|--|--|--
|$id|integer|ID автомобиля.|Обязательно указывать.
|$carName|string|Название марки автомобиля.|*
|$carNumber|string|Государственный номер автомобиля.|*
|$vin|string|VIN автомобиля.|*

> *Указать что-то одно из перечисленных.

---

#### Cars > count

Показать кол-во автомобилей у пользователя.

```php
$client->cars()->count();
```

---
