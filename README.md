# Домашнее задание к занятию "SQL. Часть 1" - Дорофеев Максим

## Задание 1

Уникальные районы: начинаются на K, заканчиваются на a, без пробелов.

    SELECT DISTINCT district
    FROM address
    WHERE district LIKE 'K%a'
      AND district NOT LIKE '% %';

Результат: Kanagawa, Kalmykia, Kaduna, Karnataka, Kutahya, Kerala, Kitaa

## Задание 2

Платежи с 15.06.2005 по 18.06.2005 включительно, сумма > 10.00.

    SELECT *
    FROM payment
    WHERE payment_date >= '2005-06-15'
      AND payment_date <  '2005-06-19'
      AND amount > 10.00;

Результат: 7 строк (payment_id 908, 7017, 8272, 12888, 13892, 14620, 15313)

## Задание 3

Последние пять аренд фильмов.

    SELECT *
    FROM rental
    ORDER BY rental_date DESC
    LIMIT 5;

Результат (rental_id): 11739, 14616, 11676, 15966, 13486
(дата 2006-02-14 15:16:03)

## Задание 4

Активные покупатели с именем Kelly или Willie.
Фамилия и имя в нижний регистр, в именах ll заменить на pp.

    SELECT
      REPLACE(LOWER(last_name), 'll', 'pp') AS last_name,
      REPLACE(LOWER(first_name), 'll', 'pp') AS first_name
    FROM customer
    WHERE active = 1
      AND first_name IN ('Kelly', 'Willie');

Результат:
torres - keppy
howepp - wippie
markham - wippie
knott - keppy
