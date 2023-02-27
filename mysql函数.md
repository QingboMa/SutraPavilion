## 查询INVOICE_IDS字段中包含99232的记录

```sql
select *
from moa_fnd_submit_material  where find_in_set('99232', INVOICE_IDS);
```

## **使用MySQL提供的字符串函数locate()函数。**

MySQL还提供一个字符串函数locate(substr,str)函数，用于返回str中substr所在的位置索引，如果找到了，则返回一个大于0的数，否则返回0。

```
select * from user where locate('yanggb', hobby ) > 0;
```

适用的场景和find_in_set()函数差不多，两个函数的区别大概只有返回值上的不同。