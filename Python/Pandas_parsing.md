# 여러 딕셔너리 값을 담고 있는 리스트 탐색하기

**2020-07-10**

## 배경
앱 로그 데이터를 분석할 때, 여러 딕셔너리 값을 담고 있는 리스트를 하나의 값으로 갖는 컬럼에서 관심있는 대상을 파싱해야하는 경우가 있다. 


## DataFrame 예시

```python
import pandas as pd
import numpy as np
import json

df = pd.DataFrame()
df['Value'] = [[
    {"IDX": 1, "Name": "Apple"},
    {"IDX": 2, "Name": "Samsung"},
    {"IDX": 3, "Name": "LG"}
]]
```


## IDX 1 탐색

```python
IDX = 1
df['IDX'] = df['Value'].apply(lambda x: [i for i in x if i['IDX'] == IDX][0]['IDX']
                                 if (len([i for i in x if i['IDX'] == IDX]) >= 1)
                                 else np.nan
                                 )
```


## 없는 IDX 탐색

```python
IDX = 4
df['Name'] = df['Value'].apply(lambda x: [i for i in x if i['IDX'] == IDX][0]['Name']
                                 if (len([i for i in x if i['IDX'] == IDX]) >= 1)
                                 else np.nan
                                 )
```