# SQLodev12
## sql sorguları patika odev 12 <br/>
**Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.**<br/>
1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?<br/><br/>
SELECT COUNT(*) FROM film WHERE length > (SELECT AVG(length) FROM film);<br/><br/><br/>
2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?<br/><br/>
SELECT COUNT(*) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);<br/><br/><br/>
3.film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.<br/><br/>
SELECT title, rental_rate, replacement_cost<br/>
FROM film<br/>
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film)<br/>
AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);<br/><br/><br/>
4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.<br/>
SELECT c.first_name, c.last_name, COUNT(p.payment_id) AS total_payments<br/>
FROM customer c<br/>
JOIN payment p ON c.customer_id = p.customer_id<br/>
GROUP BY c.customer_id, c.first_name, c.last_name<br/>
ORDER BY total_payments DESC;<br/><br/>

