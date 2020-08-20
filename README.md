# ETH-6777
# Steps to enable Debug toolbar.
1. $ pip install django-debug-toolbar

2. Add 'debug_toolbar' in INSTALLED_APPS In settings.py

3. Import the below two packages and the If block in urls.py
```
   from django.conf import settings
   from django.urls import include, path
```
```
if settings.DEBUG:
    import debug_toolbar
    urlpatterns = [
        path('__debug__/', include(debug_toolbar.urls)),
    ] + urlpatterns
```

4. Add 'debug_toolbar.middleware.DebugToolbarMiddleware' in MIDDLEWARE In settings.py

5. Add the following in settings.py
 ```
 INTERNAL_IPS = [ '127.0.0.1', ]
```

6. This will enable debug toolbar.

# Steps to write django logs in a file.
1. Add the following code in settings.py

```
import os
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'handlers': {
        'file': {
            'level': 'DEBUG',
            'class': 'logging.FileHandler',
            'filename': '/path/to/django/debug.log',
        },
    },
    'loggers': {
        'django': {
            'handlers': ['file'],
            'level': 'DEBUG',
            'propagate': True,
        },
    },
}
```

2. Make sure DEBUG = True
