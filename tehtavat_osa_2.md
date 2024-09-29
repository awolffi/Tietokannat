Sisäkysely harjoitukset

teht.2 

select name 
from airport
where iso_country in(
select iso_country
from country
where name = "Monaco");
![image](https://github.com/user-attachments/assets/db18b5fa-1568-4904-84aa-bc55a839ff25)

teht. 3

select screen_name 
from game 
where id in(
select game_id
from goal_reached
where goal_id in (
select id 
from goal 
where name = "CLOUDS"));
![image](https://github.com/user-attachments/assets/fee79e6d-7d40-4573-a9b8-21f1551a4113)

teht.4

select name
from country
where iso_country not in(
select iso_country
from airport
);
![image](https://github.com/user-attachments/assets/f3169d29-5129-4f82-842e-a304042f373d)

teht. 5

select name 
from goal
where id not in(
select goal_id
from goal_reached
where game_id in(
select id
from game 
where screen_name = "Heini")); 
![image](https://github.com/user-attachments/assets/1fc62ee8-c1ec-4a62-8d25-f0e2addc5503)

============================================================================================================================================================================================================================================================================================================

Koostetieto kyselyt harjoitukset

teht. 1

select elevation_ft as "max(elevation_ft)"
from airport
where elevation_ft in(
select max(elevation_ft)
from airport);
![image](https://github.com/user-attachments/assets/2444183d-53bb-4155-92bb-f8742fd04662)

teht.2 

select continent, count(*)
from country
group by continent;
![image](https://github.com/user-attachments/assets/f5110b87-6f09-4f86-9043-318f10b32249)

teht.3

select screen_name, count(*) 
from game 
inner join goal_reached on goal_reached.game_id = game.id 
inner join goal on goal.id = goal_reached.goal_id 
group by screen_name;
![image](https://github.com/user-attachments/assets/22a259b9-6a65-490e-a0af-81f7ea84bc22)

teht.4 

select screen_name 
from game
where co2_consumed in(
select min(co2_consumed)
from game);
![image](https://github.com/user-attachments/assets/538d12fe-f381-4e81-beb4-699fce5e93de)

teht. 5

select country.name, count(*)
from country, airport
where airport.iso_country = country.iso_country
group by country.iso_country
order by count(*) desc
limit 50;
![image](https://github.com/user-attachments/assets/9a306bb7-bd10-4f21-a12e-f081a935994d)

teht. 6

select country.name 
from country, airport
where country.iso_country = airport.iso_country
group by country.iso_country
having count(*) >= 1000;
![image](https://github.com/user-attachments/assets/396c2f52-be4e-4849-b113-1f65abc64ad8)

teht. 7

select name 
from airport	
where elevation_ft in(
select max(elevation_ft)
from airport);
![image](https://github.com/user-attachments/assets/3481ea72-6f7c-48f3-8882-8644919b784f)

teht. 8

select name
from country
where iso_country in(
select iso_country
from airport
where elevation_ft in(
select max(elevation_ft) 
from airport));
![image](https://github.com/user-attachments/assets/606d09af-3edb-46d6-a9e1-0d34a11d1550)

teht. 9

select count(*)
from game, goal_reached
where id = game_id
and screen_name = "Vesa";
![image](https://github.com/user-attachments/assets/146a75ac-b006-463f-9a7d-95c3ab358231)

teht. 10

select name 
from airport 
where latitude_deg in(
select min(latitude_deg)
from airport);
![image](https://github.com/user-attachments/assets/f9208ef2-e951-4b61-94ae-c587cfe663e0)

==========================================================================================================================================================================================================================================================================================================

Päivityskyselyt harjoitukset

teht. 1

update game 
set location =( 
select ident from airport 
where name like "Nottingham airport") 
where screen_name = "Vesa";

update game
set co2_consumed = co2_consumed + 500 
where screen_name = "Vesa";

![image](https://github.com/user-attachments/assets/bdb125a3-c46a-4b26-a2cc-e0a0d5ea0dc3)

teht. 2

![image](https://github.com/user-attachments/assets/10c02e9b-e71a-4e82-b8df-1cc8ad6da9ae)

teht. 3

delete from goal_reached;
![image](https://github.com/user-attachments/assets/389dd345-b746-45bd-a306-12095ae66ed7)

teht. 4

delete from game;
![image](https://github.com/user-attachments/assets/bb4697ba-ab06-4463-bc0f-8b13daee991d)


lopputulos:

![image](https://github.com/user-attachments/assets/b0eac84a-0ea0-4337-98bb-f1cc16b37ab4)


