# install PostgreSQL12 on Centos7
```
/usr/pgsql-9.6/bin/postgresql96-setup initdb
```

PostgreSQL 관리자 암호 설정
```
$ sudo su postgres
$ psql -c " 'StrongDBPassword'암호로 사용자 postgres 변경" ALTER ROLE
```

```
$ psql -U <dbuser> -h <serverip> -p 5432 <dbname> 
```

원격 데이터베이스 연결 활성화 (선택 사항)
```
vi /var/lib/pgsql/13/data/pg_hba.conf
```
reference: 
- https://browndwarf.tistory.com/1
- https://quiz12.tistory.com/99


# remote connection
https://docs.bitnami.com/virtual-machine/infrastructure/postgresql/administration/connect-remotely/
```
```

# 21. Database Roles
PostgreSQL manages database access permissions using the concept of roles. A role can be thought of
as either a database user, or a group of database users, depending on how the role is set up. Roles can
own database objects (for example, tables and functions) and can assign privileges on those objects to
other roles to control who has access to which objects. Furthermore, it is possible to grant membership
in a role to another role, thus allowing the member role to use privileges assigned to another role.
The concept of roles subsumes the concepts of “users” and “groups”. In PostgreSQL versions before
8.1, users and groups were distinct kinds of entities, but now there are only roles. Any role can act
as a user, a group, or both.  
This chapter describes how to create and manage roles. More information about the effects of role
privileges on various database objects can be found in Section 5.7.  

## 21.1. Database Roles
Database roles are conceptually completely separate from operating system users. In practice it might
be convenient to maintain a correspondence, but this is not required. Database roles are global across
a database cluster installation (and not per individual database). To create a role use the CREATE
ROLE SQL command:

```
CREATE ROLE name;
DROP ROLE name;
```
> name follows the rules for SQL identifiers: either unadorned without special characters, or double-quoted. (In practice, you will usually want to add additional options, such as LOGIN, to the command. More details appear below.)


```
SELECT rolname FROM pg_roles;
```