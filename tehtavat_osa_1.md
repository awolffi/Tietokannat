# Tietokannat
tietokannat vastaukset

tentti 1 Yhteen tauluun kohdistuvien kyselyiden harjoitukset

teht.1
select * from goal;
![image](https://github.com/user-attachments/assets/6ec13130-088d-4525-b338-e476ea789d88)

teht.2
select name, type from airport where iso_country = "FI";
![image](https://github.com/user-attachments/assets/062fc2fa-ac4e-4f49-92a0-d1760b4350c1)

teht.3
select name from airport where iso_country = "FI" order by name asc;
![image](https://github.com/user-attachments/assets/e637d1f2-5695-403d-8364-3caf0e6447c4)

teht.4
select name, type from airport where iso_country = "FI" order by type asc, name asc;
![image](https://github.com/user-attachments/assets/e357aca8-98c2-434b-ae1f-1026a0d47041)

teht. 5
select name from country where name like "F%";
![image](https://github.com/user-attachments/assets/65821dc3-71ac-454f-939d-840c1d501755)

teht. 6
select name from country where name like "%F%";
![image](https://github.com/user-attachments/assets/14cfff54-c13c-4265-a724-8cf064a2a410)

teht, 7
select location from game where screen_name = "Vesa";
![image](https://github.com/user-attachments/assets/5ca39890-55c5-414c-b6ee-05694980f3b8)

thet. 8
select co2_consumed from game where screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/624877e0-e8f0-4e98-9557-f967a2ab04ea)

teht. 9
select co2_budget from game limit 1;
![image](https://github.com/user-attachments/assets/1676997e-a3d1-4435-80c0-fc7c345d8397)

============================================================================================================================================================================================================================================================================================================================================================================================================

Where-osan liitosehto harjoitukset

teht. 1
select country.name AS "country name", airport.name AS "airport name" from airport, country where airport.iso_country = country.iso_country and country.iso_country = "IS";
![image](https://github.com/user-attachments/assets/48fbd756-d232-40d9-9632-2009379bc285)

teht. 2
select airport.name as "airport name" from airport, country where airport.iso_country = country.iso_country and country.name = "France" and type = "large_airport";
![image](https://github.com/user-attachments/assets/e55fd6e6-a262-4b6e-b7ee-edb90d674aec)

teht. 3
select country.name as "country_name", airport.name as "airport_name" from airport, country where airport.iso_country = country.iso_country and country.Continent = "AN";
![image](https://github.com/user-attachments/assets/a601d928-183c-4fed-aec8-1e273364a3e5)

teht. 4
select elevation_ft from game, airport where airport.ident = game.location and screen_name = "Heini";
![image](https://github.com/user-attachments/assets/9b28ad7a-52cb-4f14-a150-1371fe915554)

teht.5
select elevation_ft*0.3048 as "elevation_m" from game, airport where airport.ident = game.location and screen_name = "Heini";
![image](https://github.com/user-attachments/assets/c1392767-81de-4844-bd33-7cdfec183f81)

teht. 6
select airport.name from airport, game where airport.ident = game.location and screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/b3db69e1-836b-4c80-b9eb-8cefe6f81c36)

teht.7 
select country.name from airport, game, country where game.location = airport.ident and airport.iso_country = country.iso_country and screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/c8b675cb-49b2-4913-a312-3f9386ba5f84)

teht. 8
select goal.name from goal, goal_reached, game where goal_reached.game_id = game.id and goal_reached.goal_id = goal.id and screen_name = "Heini";
![image](https://github.com/user-attachments/assets/100bf409-007b-45de-bd55-d4773c0a1120)

thet. 9
select airport.name from goal, goal_reached, game, airport where goal_reached.game_id = game.id and goal_reached.goal_id = goal.id and airport.ident = game.location and screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/920c8cf6-4306-484c-8008-ba8b0817d545)

teht. 10
select country.name from goal, goal_reached, game, airport, country where airport.iso_country = country.iso_country and goal_reached.game_id = game.id and goal_reached.goal_id = goal.id and airport.ident = game.location and screen_name = "Ilkka" and goal.name = "CLOUDS";
![image](https://github.com/user-attachments/assets/d71cfbeb-542f-4998-bc4b-4369fb7bee70)

============================================================================================================================================================================================================================================================================================================================================================================================================


JOIN HARJOITUKSET

teht.1

select country.name as "country name", airport.name as "airport name"
from country
inner join airport on airport.iso_country = country.iso_country 
where country.name = "Finland"
and scheduled_service = "yes";
![image](https://github.com/user-attachments/assets/6adcd7b5-8e39-492c-869f-f56d7412fd7b)

teht.2 

select screen_name, name 
from game
inner join airport on airport.ident = game.location;
![image](https://github.com/user-attachments/assets/96d87255-33d9-461e-b252-3a53069f27fa)

teht. 3

select screen_name, country.name
from game
inner join airport on airport.ident = game.location
inner join country on airport.iso_country = country.iso_country;
![image](https://github.com/user-attachments/assets/d5b92107-85b0-4da0-9469-c458459c34cd)

teht. 4

select airport.name, screen_name
from airport 
left join game on ident = location
where name like '%Hels%';
![image](https://github.com/user-attachments/assets/52d11647-48d4-413b-8103-787b26ff55e9)

teht. 5

select name, screen_name 
from goal
left join goal_reached on goal.id = goal_reached.goal_id
left join game on game.id = goal_reached.game_id;
![image](https://github.com/user-attachments/assets/1f9dfb29-2439-4f04-8948-af987abd0a69)


==========================================================================================================================================================================================================================================================================================================================================================================================================

Sisäkysely harjoitukset

teht. 1

select name
from country
where iso_country in (
select iso_country 
from airport
where name like 'Satsuma%');
![image](https://github.com/user-attachments/assets/dbe6204e-d57d-47d6-a1cd-01318ecddee7)
