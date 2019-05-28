### Design（设计说明书）

---
#### 2. Database design
```sql
CREATE TABLE `users` (
  `account` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `password` varchar(255) DEFAULT NULL,
  `email` varchar(255) DEFAULT NULL,
  `phone` varchar(255) DEFAULT NULL,
  `balance` double DEFAULT NULL,
  PRIMARY KEY (`account`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

```sql
CREATE TABLE `tasks` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `award` double DEFAULT NULL,
  `description` varchar(255) DEFAULT NULL,
  `ddl` varchar(255) DEFAULT NULL,
  `usernum` int(11) DEFAULT NULL,
  `agentaccount` varchar(255) DEFAULT NULL,
  `complete` tinyint(1) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

```sql
CREATE TABLE `TaskundoUsers` (
  `task_id` bigint(20) unsigned NOT NULL,
  `user_account` varchar(255) NOT NULL,
  PRIMARY KEY (`task_id`,`user_account`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

```sql
CREATE TABLE `TaskdoneUsers` (
  `task_id` bigint(20) unsigned NOT NULL,
  `user_account` varchar(255) NOT NULL,
  PRIMARY KEY (`task_id`,`user_account`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

```sql
CREATE TABLE `TaskUsers` (
  `task_id` bigint(20) unsigned NOT NULL,
  `user_account` varchar(255) NOT NULL,
  PRIMARY KEY (`task_id`,`user_account`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

---
#### 3. Interface API design 

**User**
- 数据结构

    ![](pics/API/Model1.png)
- API设计

    ![](pics/API/API1.png)
    ![](pics/API/API2.png)
    ![](pics/API/API3.png)
    ![](pics/API/API4.png)
    ![](pics/API/API5.png)

**Group**
- 数据结构

    ![](pics/API/Model2.png)
- API设计

    ![](pics/API/API6.png)
    ![](pics/API/API7.png)
    ![](pics/API/API8.png)

**Tasks**
- 数据结构

    ![](pics/API/Model3.png)
    ![](pics/API/Model4.png)
- API设计

    ![](pics/API/API9.png)
    ![](pics/API/API10.png)
    ![](pics/API/API11.png)
    ![](pics/API/API12.png)
    ![](pics/API/API13.png)
    ![](pics/API/API14.png)

**Questionnaires**
- 数据结构

    ![](pics/API/Model6.png)
- API设计

    ![](pics/API/API15.png)
    ![](pics/API/API16.png)
    ![](pics/API/API17.png)


**Error**
- 数据结构

    ![](pics/API/Model5.png)

---