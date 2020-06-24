# Python Flask Web App 배포하기

**2020-06-24**

## 목적
- **Python Flask App**을 **Azure App Service**에 배포하기


## 레퍼런스
- [파이썬 앱 만들기](https://docs.microsoft.com/ko-kr/azure/app-service/containers/quickstart-python?tabs=cmd)


## Flask App Sample 다운

```bash
# 플라스크 앱 샘플 다운
git clone https://github.com/Azure-Samples/python-docs-hello-world

# 다운받은 디렉토리로 이동
cd python-docs-hello-world
```

## 가상환경 생성 / 필수 라이브러리 설치 / 플라스크 웹 서버 구동

```bash
# 파이썬 가상환경 'env' 생성
py -3 -m venv env
# 가상환경 'env' 활성화
env\scripts\activate
# 가상환경 'env'에 필수 라이브러리 일괄 설치
pip install -r requirements.txt
# 파이썬 플라스크 앱 설정
SET FLASK_APP=application.py
# 플라스크 웹 서버 구동
flask run
```


## 로컬에서 플라스크 앱 동작 확인
http://localhost:5000/


## Azure CLI 설치

- [Azure CLI 설치 페이지](https://docs.microsoft.com/ko-kr/cli/azure/install-azure-cli?view=azure-cli-latest)

OS에 맞는 Azure CLI 설치 진행


## Azure 로그인

```bash
az login
```


## Azure App Service에 신규 앱 만들기

```bash
az webapp up --sku <tier> -l <location name> -g <resource group name> -n <flask app name>
```


### `az webapp up --help` 명령을 통해 자세한 파라미터 정보 확인 가능

- `<tier>` : F1 무료, B1 베이직(유료) 등
- `<location name>` : southeastasia 등
- `<resource group name>` : Azure Portal에서 확인
- `<flask app name>` : 플라스크 앱 이름

완료 시 `http://<flask app name>.azurewebsites.net` 로 접속 후 확인

