## sql group by を用いた計算方法
```
select 
  tsd.user.cd
  ,mu.user.name
  ,sum(tsd.amt)as sum_amt             // 集計関数を用いて計算
from
 t-sales-detail tsd
 join m-user my                      // joinはinnerjoinの省略
   on tsd.user_cd = mu.user_cd       // onでどこをくっつけるか
group by                             // group by はselectと同じになる
  tsd.user_cd
  ,mu.user_name
order by                            // sort
  sum_amt desc;
```
