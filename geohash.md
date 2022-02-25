## Select Zabbix

SELECT h.name as 'host', inv.location as 'geohash',  
  CASE   
    WHEN IFNULL(problems.count, 0)=0 AND IFNULL(status.value, 0)>0 THEN 0 -- Green status  
    WHEN IFNULL(problems.count, 0)>0 AND IFNULL(status.value, 0)>0 THEN 1 -- Yellow status  
    ELSE 2 -- Red status  
  END as 'metric'  
FROM hosts h LEFT JOIN host_inventory inv USING(hostid)  
LEFT JOIN (  
  SELECT h.hostid, COUNT(t.triggerid) as count  
  FROM triggers t, functions f, items i, hosts h  
  WHERE t.triggerid=f.triggerid AND i.itemid=f.itemid AND h.hostid=i.hostid   
    AND h.status=0 AND t.status=0 AND t.value=1  
  GROUP BY h.hostid  
) as problems  
USING(hostid)  
LEFT JOIN (  
  SELECT hostid, MAX(h.value) as value  
  FROM items LEFT JOIN history h USING(itemid)  
  -- Replace key_ by item you want to check  
  -- key_='icmpping[your params here]' or key_ like 'icmpping%'  
  WHERE key_ like 'icmpping%'  
  GROUP BY hostid  
) status USING(hostid)  
-- status could be 0 (monitored host) or 1 (unmonitored)  
WHERE h.status=0   
  AND inv.location!=''  
-- It's possible also exclude discovered hosts by adding h.flags=0  
  AND h.flags=0  
GROUP BY h.name, inv.location, problems.count, status.value;  
