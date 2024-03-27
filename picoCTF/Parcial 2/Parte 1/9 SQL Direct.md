## Objetivo
Connect to this PostgreSQL server and find the flag!
Additional details will be available after launching your challenge instance.

## Pistas
What does a SQL database contain?

## Solución
En este reto hay que conectarse a una base de datos PostgreSQL, la pista nos pide investigar que es lo que hay dentro de esa base de datos.

```bash
mgarcia@nightmare ~/mgarcia/Desktop/saturn.picoctf.net:64727
 % psql -h saturn.picoctf.net -p 64912 -U postgres pico
Password for user postgres:
psql (15.6 (Debian 15.6-0+deb12u1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico=# select * from flags;
 id | firstname | lastname  |                address
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)

pico=# exit
```

## Notas adicionales
Hay que instalar el cliente de postgres en caso de no tenerlo instalado
> sudo apt install postgresql-client

## Referencias