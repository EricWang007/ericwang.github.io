---
title: "SQL"
date: 2021-08-30T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: SQL
    identifier: SQL
    parent: Database
    weight: 10
---

# 3 SQL

---

## Data Definition

* create table

```sql
create table instructor(
	ID     char(5),
    name   varchar(20) not null,
    dept_name varchar(20),
    salary numeric(8,2),
    primary key(ID),
    foreign key(dept_name) references department,
    check(salary>0);
)
```

* insert

```sql
insert into instructor values(080040, 'Jack', 'Com.Sci', 8000)
```

* delete

```sql
delete from isntructor
```

* drop

```sql
drop table r
```

* alter table

```sql
alter table r add A D
```

```sql
alter table r drop A
```

## Select Query

```sql
select distinct dept_name from instructor # 去重
```

```sql
select all dept_name from instructor # 不去重
```

```sql
select T.name as instructor_name, course_id 
from isntructor as T, instructor as S
where T.salary > S.salary 
	and S.dept_name = 'Comp.Sci'
	and salary between 9000 and 10000
order by name desc # asc上升
```

```sql
select dept_name, avg(salary) as avg_salary
from instructor
group by dept_name
```

## Join

* natural join
* outer join