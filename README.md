# PostreSQL

Профильный модуль. 2.5 Архитектура в разработке программного обеспечения и базы данных.

--1. SQL запрос для вывода всех категорий.

  select *
  from categories

--2. SQL запрос для вывода только названий всех категорий.
  
  select categoryname
  from categories
  

--3. Сколько всего категорий?

  16

--4. SQL запрос для вывода первых 100 строк из таблицы заказов с сортировкой по дате.
 
  select *
  from orders
  order by orderdate 
  limit 100

--5. SQL запрос для вывода первых 100 строк из таблицы заказов с сортировкой по сумме. От максимальной к минимальной.

  select *
  from orders
  order by totalamount desc 
  limit 100

--6. SQL запрос для вывода Имени, фамилии, имэйла покупателя с именем «XMFYXD».
     
  select firstname,lastname,email
  from customers
  where firstname='XMFYXD'

--7. Какое имя у покупателя?

  'XMFYXD'

--8.SQL запрос для вывода списка заказов (id, дата, id покупателя, сумма), совершённых с 2 февраля по 4 февраля.

  select orderid,orderdate,customerid,totalamount
  from orders 
  where orderdate between '2004-02-02' and '2004-02-04'

--9. Сколько было таких заказов?
  
  122

--10. SQL запрос для вывода списка актёров и кол-ва фильмов, в которых они снимались.

  select actor, count (1)
  from products 
  group by actor

--11. SQL запрос для вывода списка актёров, которые снимались в фильмах не менее 4 раз.

  select actor, count (1)
  from products 
  group by actor 
  having count (1)>=4

--12. Сколько таких актёров?
  
  2

--13. SQL запрос для вывода списка фильмов с актёром CHEVY FOSTER.

  select * from 
  products 
  where actor = 'CHEVY FOSTER'

--14. Сколько таких фильмов?
  
  4

--15. SQL запрос для вывода списка позиций заказами с фильмами, в которых снимался CHEVY FOSTER.

  select orderlineid from 
  orderlines inner join products on orderlines.prod_id=products.prod_id
  where actor = 'CHEVY FOSTER'

--16. Сколько таких позиций?
  
  23

--17. SQL запрос для вывода покупателей, купивших фильмы с CHEVY FOSTER.

select * from customers
where customerid in (
select customerid from orders
where orderid IN (
select orderid from
orderlines inner join products on orderlines.prod_id=products.prod_id
where actor = 'CHEVY FOSTER'))

--18. Сколько фанатов у CHEVY FOSTER?
  
  23       
