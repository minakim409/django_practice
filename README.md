# django_practice

## Backend

#### Step 0.

確定電腦有安裝 `python3` 以及完成上述資料匯入資料庫的指令後打開終端機執行以下指令：

```shell
# for mac
cd backend
python3 -m venv django_env #建立虛擬環境 #-m: module-name
code . #確認有沒有建立了 django_env
source django_env/bin/activate #啟動虛擬環境 for mac
```

```shell
# for windows
cd backend
python3 -m venv venv #建立虛擬環境 #-m: module-name
venv\Scripts\activate.bat #啟動虛擬環境 for windows
```

#### Step 1.

成功的話，command prompt 前面應該會多出 `(django_env)` 的字樣，代表已經進入這個虛擬環境。如果未來你想退出這個虛擬環境，可以輸入 `deactivate`。
接著下載所需套件，需要的套件與版本已定義在 `requirements.txt`，下載完輸入`pip list`檢查所有用 `pip` 下載的套件。

```shell
python -m pip install --upgrade pip #pip更新至最新版本
pip install django
pip list
```

可以知道 django 的 version
```shell
python -m django --version
```

You can see what django subcommands you can use.
```shell
django-admin
```

You can start the project, and basic files will be set.
```shell
django-admin startproject django_project
```

Run server

```shell
python manage.py runserver
```

startApp (기능 분리)
```shell
python manage.py startapp blog
tree #to see the structure
```

After you start the blog app

blog.view.py (This format)
```shell
from django.shortcuts import render
from django.http import HttpResponse
def home(request):
    return HttpResponse('<h1>Blog Home</h1>')


def about(request):
    return HttpResponse('<h1>Blog About</h1>')
```

blog.urls.py (This format, you need to create by yourself)
```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='blog-home'),
    path('about/', views.about, name='blog-about'),
]
```

django_project.urls.py 
```shell
from django.contrib import admin
from django.urls import path, include #need to include blog

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', include('blog.urls')), #blog urls add
]
```
## PostgreSQL 연결 (미리 postgresql에 데이터 베이스를 만들어 놓는다.)
terminal command
```shell
pip install psycopg2
pip install psycopg2-binary #probably this is for macbook m1 이거때매 계속 에러 생겼었음.
```


django_project.urls.py 

```shell
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',  #PostgreSQL
        'NAME': 'Blog',  #資料庫名稱
        'USER': 'postgres',  #資料庫帳號
        'PASSWORD': '9999',  #資料庫密碼
        'HOST': 'localhost',  #Server(伺服器)位址
        'PORT': '5432'  #PostgreSQL Port號
    }
}
```
### blog.models.py에 모델을 만들고, admin page에 생기게 하고 싶으면 blog.admin.py 에 admin.site.register(modelname) 을 등록해야 한다.


