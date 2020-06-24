# Azure App Service

**2020-06-24**

## 목적
**파이썬 애플리케이션**을 **RESTful API**로 사용하기 위한 **플라스크 웹 서버 구축**하기

- [Python Flask로 간단한 REST API 작성하기](https://medium.com/@feedbotstar/python-flask-%EB%A1%9C-%EA%B0%84%EB%8B%A8%ED%95%9C-rest-api-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0-60a29a9ebd8c)


## Flask App 환경 구축하기

- Github Repository 생성

- 가상환경 생성 및 활성화

```bash
python -m venv env
env\Scripts\activate
```

- 필수 라이브러리 설치 및 requirements.txt 생성

```bash
# 플라스크 및 플라스크 RESTful 라이브러리 설치
pip install flask
pip install flask-restful

# 라이브러리 목록 Freeze
pip freeze > requirements.txt
```


## Flask App 생성 - app.py

**app.py**
```python
from flask import Flask
from flask_restful import Resource, Api
from flask_restful import reqparse

app = Flask(__name__)
api = Api(app)

class GetInfo(Resource):

    def post(self):
        try:
            
            parser = reqparse.RequestParser()

            parser.add_argument('Name', type=int)
            parser.add_argument('Age', type=int)

            args = parser.parse_args()
            
            return {'Name': args['Name'],
                    'Age': args['Age']
                    }
        
        except Exception as e:
            
            return {'error': str(e)}

api.add_resource(GetInfo, '/test')

if __name__ == '__main__':
    app.run(debug=True)
```


## Flask App 실행하기
```bash
SET FLASK_APP=app.py
flask run
```


## POSTMAN으로 RESTful API 테스트하기

- [포스트맨 설치](https://www.postman.com/downloads/)
- 포스트맨 실행 후 POST Method 선택
- http://127.0.0.1:5000/test 설정
- Body 탭 - form-data 옵션 선택 - Key, Value 값에 각각 데이터 입력
- Send 버튼 클릭 후 Response 확인