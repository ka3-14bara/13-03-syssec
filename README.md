# Домашнее задание к занятию "`SQL. Часть 2`" - `Латыпов Данияр`

   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1  

Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию:

    - фамилия и имя сотрудника из этого магазина;
    - город нахождения магазина;
    - количество пользователей, закреплённых в этом магазине.

---

### Ответ 1

```
select concat(s2.first_name, ' ', s2.last_name), c2.city, count(c.store_id) 
from store s 
left join staff s2 on s2.staff_id = s.manager_staff_id
left join customer c on c.store_id = s.store_id 
left join address a on a.address_id = s.address_id 
left join city c2 on c2.city_id = a.city_id 
group by s.store_id 
having count(c.store_id) > 300;
```

---

### Задание 2 

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

---
### Решение 2

```
select count(1)
from film f 
where f.length > (select avg(length) from film);
```

---

### Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

---

### Решение 3

```
select concat(month(p.payment_date), ' ', year(p.payment_date)) as dt, (sum(amount)) as sm
from payment p 
group by dt
order by sm desc 
limit 1;
```

---
