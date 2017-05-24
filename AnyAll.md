## Get the functionality of `any` and `all`(from R) in SAS

One way of doing this within `PROC SQL` is to use the `min` and `max` functions:

```sas
PROC SQL;
  SELECT    sex, min(age < 18) as allMinors
  FROM      sashelp.classes
  GROUP BY  sex;
  
  SELECT    sex, max(height >= 6*12) as someBBallHope
  FROM      sashelp.classes
  GROUP BY  sex;
QUIT;
```

would correspond to 

```R
library(tidyverse)
classes %>% group_by(sex) %>% summarise(allMinors = all(age < 18))
classes %>% group_by(sex) %>% summarise(someBBallHope = any(height >= 6*12)
```
