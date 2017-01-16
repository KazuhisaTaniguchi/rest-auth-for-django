# ReduxSimpleStarter

Interested in learning [Redux](https://www.udemy.com/react-redux/)?

###Getting Started###

There are two methods for getting started with this repo.

####Familiar with Git?#####
Checkout this repo, install dependencies, then start the gulp process with the following:

```
	> git clone git@github.com:StephenGrider/ReduxSimpleStarter.git
	> cd ReduxSimpleStarter
	> npm install
	> npm start
```

####Not Familiar with Git?#####
Click [here](https://github.com/StephenGrider/ReactStarter/releases) then download the .zip file.  Extract the contents of the zip file, then open your terminal, change to the project directory, and:

```
	> npm install
	> npm start
```

####プラスで追加#####
backendでDjangoを使う場合(LoginとLogoutのみ)
[django-rest-auth](http://django-rest-auth.readthedocs.io/en/latest/index.html)
[django-cors-headers](https://github.com/ottoyiu/django-cors-headers)

```
	> pip install django-rest-auth
	> pip django-cors-headers

  settings.py

  INSTALLED_APPS = (
      ...,
      'rest_framework',
      'rest_framework.authtoken',
      ...,
      'rest_auth'
  )

  REST_USE_JWT = True

  CORS_ORIGIN_ALLOW_ALL = True
  ACCOUNT_LOGOUT_ON_GET = True
  # ↑の2つは、CROSSサイトの登録とLOGOUT時をGETでも出来るようにする設定だから
  開発時のみTrueにしてもよい


  urls.py

  urlpatterns = patterns('',
      ...,
      url(r'^rest-auth/', include('rest_auth.urls'))
  )
```

backendでDjangoを使う場合(Registration)

```
	> pip install django-allauth

  settings.py

  INSTALLED_APPS = (
      ...,
      'rest_framework',
      'rest_framework.authtoken',
      ...,
      'rest_auth'
      'django.contrib.sites',
      'allauth',
      'allauth.account',
      'rest_auth.registration',
  )

  SITE_ID = 1

  REST_USE_JWT = True

  EMAIL_HOST = 'smtp.gmail.com'
  EMAIL_USE_TLS = 1
  EMAIL_PORT = 587
  EMAIL_HOST_USER = 'youremail@gmail.com'
  EMAIL_HOST_PASSWORD = 'youremailpass'
  or
  ACCOUNT_EMAIL_VERIFICATION = "none"
  # ↑の項目はメールでの認証コードの送信をやめるもの


  urls.py

  urlpatterns = patterns('',
      ...,
      url(r'^rest-auth/', include('rest_auth.urls')),
      url(r'^rest-auth/registration/', include('rest_auth.registration.urls'))
  )
```
