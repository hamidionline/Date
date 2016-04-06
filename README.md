# Date [in development]

Fix all needs to date in php

## Install

```
composer require m-jch/date:dev-master --prefer-dist
```

## Tutorial

This package contains 2 class, ```Jalali``` and ```Date```. ```Jalali``` class responsible for Jalali (shamsi) date time and ```Date``` class responsible for Gregorian date time.

All below examples should be run in ```Jalali``` or ```Date``` class.

All format listed in PHP [```date```](http://php.net/manual/en/function.date.php) function support.

We want to implements most of Carbon PHP class.

### Include Classes

```php
use Date\Date;
use Date\Jalali;
```

### Examples

#### Creators

```php
$date = new Jalali('1395/04/10 23:10:05');
$date->format('Y-m-d H:i:s');

echo new Jalali('1395-04-10');

echo Jalali::now();
echo Jalali::yesterday();
echo Jalali::tomorrow();

echo Jalali::create(1394, 05, 04, 12, 45, 23);
echo Jalali::createDate(1394, 05, 04);
echo Jalali::createTime(12, 45, 23);
```

#### Converters

```php
// Jalali to Gregorian
$date = new Jalali('1373/06/05 23:10:05');
echo $date->toGregorian();

$date = new Jalali('1373/06/05 23:10:05');
echo $date->tog(); // An aliases for toGregorian method

// Gregorian to Jalali
$date = new Date('2012-06-05 20:05:01');
echo $date->toJalali();

$date = new Date('2012-06-05 20:05:01');
echo $date->toj(); // An aliases for toJalali method
```

#### Modifiers

```php
echo Jalali::now()->startOfDay();
echo Jalali::now()->endOfDay();

echo Jalali::now()->addDays(1);
echo Jalali::now()->subDays(5);
```

#### Customize

```php
// echo as farsi numbers
echo Jalali::now()->fa()->subDays(4);
echo (new Jalali)->addDays(5)->fa('Y-m-d l'); // Can use just fa() instead of fa()->format()
```

### Comparisons

All comparisons based on Gregorian date, so you can compare two date with different type of class.

```php
$date1 = new Jalali('1395-07-12');
$date2 = new Jalali('1395-10-05');

$date1->equalTo($date2);
$date1->eq($date2);

$date1->notEqualTo($date2);
$date1->ne($date2);

$date1->greaterThan($date2);
$date1->gt($date2);

$date1->greaterThanOrEqualTo($date2);
$date1->gte($date2);

$date1->lessThan($date2);
$date1->lt($date2);

$date1->lessThanOrEqualTo($date2);
$date1->lte($date2);
```

## Road map

* Add diff methods such as ```diffInDay``` or ```greater```
* Add Laravel 4 and 5 providers
