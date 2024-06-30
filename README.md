# Домашнее задание к занятию "`SQL. Часть 1`" - `Латыпов Данияр`

   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1  

Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

---

### Ответ 1

![alt text](image.png)

```
select distinct district from address a 
where district LIKE 'K%a' and 
	  district not like '% %';
```

---

### Задание 2 

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.

---
### Решение 2

![alt text](image-1.png)

```
select * from payment p 
where amount > 10.0 and 
	  cast(payment_date as date) between '2005-06-15' and '2005-06-18';
```

---

### Задание 3

Получите последние пять аренд фильмов.

---

### Решение 3

![alt text](image-2.png)

```
select * from rental r 
order by rental_date desc 
limit 5;
```

---

### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
замените буквы 'll' в именах на 'pp'.

---

### Решение 4

![alt text](image-3.png)

```
select customer_id, store_id, replace(lower(first_name), 'll', 'pp'), lower(last_name) from customer c 
where active like 1 and 
	  first_name in ('Kelly', 'Willie');
```

---