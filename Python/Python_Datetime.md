# 날짜 및 시간 데이터 핸들링하기

**2020-07-10**

## 배경
날짜 및 시간 데이터를 분석할 때 데이터 타입 관련 이슈가 종종 발생해 신속한 데이터 분석을 방해하는 경우가 있다. 날짜 및 시간 데이터 타입에 대한 이해를 높히고, 핸들링 능력을 향상시키는 것을 목적으로 이 글을 작성한다.


## 타입

```python
import pandas as pd
import numpy as np
import datetime

# Datetime 타입
today_datetime = datetime.datetime.today()

# Str 타입
today_string = datetime.datetime.strftime(today_datetime, "%Y-%m-%d %H:%M:%S")

# Timestamp 타입
today_timestamp = pd.to_datetime(today_string)

print(">> today_datetime\n{}".format(today_datetime), type(today_datetime),'\n')
print(">> today_string\n{}".format(today_string), type(today_string),'\n')
print(">> today_timestamp\n{}".format(today_timestamp), type(today_timestamp),'\n')
```


```
>> today_datetime
2020-07-10 17:54:24.262052 <class 'datetime.datetime'> 

>> today_string
2020-07-10 17:54:24 <class 'str'> 

>> today_timestamp
2020-07-10 17:54:24 <class 'pandas._libs.tslibs.timestamps.Timestamp'> 
```

### 1) Datetime 타입 핸들링





### 2) Str 타입 핸들링





### 3) Timestamp 타입 핸들링




