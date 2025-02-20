# tours-database

create table tours (
    tour_id number(7, 0) generated as identity constraint pk_tour_id primary key,
    country varchar(50) not null,
    city varchar(50) not null,
    description clob,
    price number(10, 2),
    duration_days varchar(30) not null
);

drop table tours;

insert into tours (country, city, price, duration_days)
values ('poland', 'krakow', 500, '3 days');

insert into tours (country, city, price, duration_days)
values ('france', 'paris', 800, '1 week');

insert into tours (country, city, price, duration_days)
values ('italy', 'milan', 960, '2 weeks');

select * from tours;

create table customers (
    customer_id number(7, 0) generated as identity primary key,
    customer_name varchar2(100) not null,
    email varchar2(100),
    phone_number varchar2(20)
);
drop table customers;

create table bookings (
    booking_id number(7, 0) generated as identity primary key,
    tour_id number(7, 0) references tours(tour_id),
    customer_id number(7, 0) references customers(customer_id),
    booking_date date
);

drop table bookings;

insert into bookings (customer_id, booking_date)
values (1, null);

insert into bookings (customer_id, booking_date)
values (2, null);

insert into bookings (customer_id, booking_date)
values (3, null);

insert into bookings (customer_id, booking_date)
values (4, null);

select * from bookings;

create table customer_infos (
    info_id number(8, 0) generated as identity primary key,
    customer_id number(7, 0) references customers(customer_id),
    info_type char check (info_type in ('a', 'h', 'm')),
    email varchar2(200),
    phone varchar2(18) not null
);


insert into customers (customer_name, email, phone_number)
values ('nicat', 'nicat@example.com', '1234567890');

insert into customers (customer_name, email, phone_number)
values ('arifa', 'arifa@example.com', '0987654321');

insert into customers (customer_name, email, phone_number)
values ('fidan', 'fidan@example.com', '1122334455');

insert into customers (customer_name, email, phone_number)
values ('shahin', 'shahin@example.com', '5566778899');
