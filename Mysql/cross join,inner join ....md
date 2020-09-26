# cross join  (笛卡尔连接查询)
```sql
SELECT 
  a.`store_name`,
  b.`product_name`,
  IFNULL(c.revenue, 0) AS revenue 
FROM
  stores a 
   CROSS JOIN  products b 
  LEFT JOIN 
    (SELECT 
      sto.`id` AS store_id,
      pro.`id` AS product_id,
      sto.`store_name`,
      pro.`product_name`,
      SUM(quantity * price) AS revenue 
    FROM
      sales sal
      INNER JOIN stores sto 
        ON sto.`id` = sal.`store_id` 
      INNER JOIN products pro 
        ON sal.`product_id` = pro.`id` 
    GROUP BY sto.`store_name`,
      pro.`product_name`) c 
  ON a.id = c.store_id 
  AND b.id = c.product_id 
ORDER BY a.store_name ;
```