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

