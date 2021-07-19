## [安装](https://www.django-rest-framework.org/#installation)

使用安装`pip`，包括所需的任何可选软件包...

```
pip install djangorestframework
pip install markdown       # Markdown support for the browsable API.
pip install django-filter  # Filtering support
```

...或从github克隆项目。

```
git clone https://github.com/encode/django-rest-framework
```

添加`'rest_framework'`到您的`INSTALLED_APPS`设置。

```
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```

如果您打算使用可浏览的API，则可能还需要添加REST框架的登录和注销视图。将以下内容添加到您的根`urls.py`文件中。



```
urlpatterns = [
    ...
    path('api-auth/', include('rest_framework.urls'))
]
```









