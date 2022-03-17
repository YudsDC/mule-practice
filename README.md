# mule-practice

#### MySQL database
```
create table accounts(
    id int auto_increment,
    username varchar(255) unique not null,
    date_registered date,
    active integer,
    primary key (id)
);

create table account_details (
    id int auto_increment,
    account_id int,
    full_name varchar(255),
    birthday date,
    gender varchar(1),
    primary key (id),
    foreign key (account_id) references accounts(id)
);

insert into accounts (username, date_registered, active) values ('john123', '2014-01-22', 1);
insert into accounts (username, date_registered, active) values ('jackpeters', '2015-12-30', 1);
insert into accounts (username, date_registered, active) values ('jenniesummers', '2011-05-16', 1);

commit;

insert into account_details (account_id, full_name, birthday, gender)
values ((select id from accounts where username = 'john123'), 'John White Smith', '1990-01-01', 'M');

insert into account_details (account_id, full_name, birthday, gender)
values ((select id from accounts where username = 'jackpeters'), 'Jack Peters', '1988-02-02', 'M');

insert into account_details (account_id, full_name, birthday, gender)
values ((select id from accounts where username = 'jenniesummers'), 'Jennie Summers', '1994-04-04', 'F');

commit;
```

#### Docker
```
docker pull mysql
docker run -p 13306:3306  --name user-accounts-db -e MYSQL_ROOT_PASSWORD=passwd -d mysql:latest
```
