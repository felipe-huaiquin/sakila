# Sakila

1. Consulta para obtener todos los clientes pertenecientes a la ciudad con el id 312.
```
SELECT customer.first_name, customer.last_name, customer.email, address.address
FROM customer
JOIN address ON customer.customer_id = address.address_id
JOIN city ON address.city_id = city.city_id
WHERE city.city_id = 132
```

2. Consulta para obtener el título de la película, la descripción, el año de estreno, la calificación, las características especiales y el la categoría.
```
SELECT film.title, film.description, film.release_year, film.rating, film.special_features, category.name AS category_name
FROM film
JOIN film_category ON film.film_id = film_category.film_id
JOIN category ON film_category.category_id = category.category_id
```
3. Consulta para obtener la identificación del actor, el nombre del actor, el título de la película, la descripción y el año de lanzamiento, del actor con id 5.
```
SELECT actor.first_name, actor.last_name, film.title, film.description, film.release_year
FROM actor
JOIN film_actor ON actor.actor_id = film_actor.actor_id
JOIN film ON film_actor.film_id = film.film_id 
WHERE actor.actor_id = 5
```
4. Consulta para obtener el nombre, apellido, correo electrónico y dirección de los clientes que realizaron una orden en la tienda 1 y que viven en las siguientes ciudades: 1, 42, 312 y 459.
```
SELECT customer.first_name, customer.last_name, customer.email, address.address
FROM customer
JOIN address ON customer.address_id = address.address_id
JOIN city ON address.city_id = city.city_id
WHERE customer.store_id = 1
AND (city.city_id = 1 OR city.city_id = 42 OR city.city_id = 312 OR city.city_id = 459)
```
5.  Consulta que devuelve el título de la película, la descripción, el año de lanzamiento, la calificacion y las características especiales de todos los filmes en las que actúa el actor 15 y además poseen una calificación de G y la característica especial del detrás de escena.
```
SELECT film.title, film.description, film.release_year, film.rating, film.special_features
FROM film
JOIN film_category ON film.film_id = film_category.film_id
JOIN category ON film_category.category_id = category.category_id
JOIN film_actor ON film.film_id =  film_actor.film_id
JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE film.special_features LIKE '%Behind the Scenes%'
AND actor.actor_id = 15 AND film.rating = 'G'
```
6. Consulta para obtener todos los actores que trabajaron en la película 369. Esta consulta devuelve el id de la película, su título junto con el id de los actores y su nombre completo.
```
SELECT film.film_id, film.title, actor.actor_id, CONCAT(actor.first_name,' ',actor.last_name) AS actor_name
FROM film
JOIN film_actor ON film.film_id = film_actor.film_id
JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE film.film_id = 369
```
7. Consulta para obtener todas las películas del género "Drama" y que poseen una tarifa de alquiler de 2.99. Esta consulta devuelve el título de la película, la descripción, el año de estreno, la calificación, las características especiales y la categoría.
```
SELECT film.title, film.description, film.release_year, film.special_features, category.name AS category_name
FROM film
JOIN film_category ON film.film_id = film_category.film_id
JOIN category ON film_category.category_id = category.category_id
WHERE film.rental_rate = 2.99 AND category.name = 'Drama'
```
8. Consulta para obtener todas las películas de acción donde actúa Sandra Kilmer. Esta consulta devuelve el título de la película, la descripción, el año de estreno, la calificación, las características especiales, el género (categoría) y el nombre completo del actor.
```
SELECT film.title, film.description, film.release_year, film.rating, film.special_features, category.name AS category_name, CONCAT(actor.first_name,' ',actor.last_name) AS actor_name
FROM film
JOIN film_category ON film.film_id = film_category.film_id
JOIN category ON film_category.category_id = category.category_id
JOIN film_actor ON film.film_id = film_actor.film_id
JOIN actor ON film_actor.actor_id = actor.actor_id 
WHERE actor.first_name = 'SANDRA' AND actor.last_name ='KILMER' AND category.name = 'Action'
```