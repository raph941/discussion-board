# install 
    gunicorn: pip install gunicorn
    whitnoise: pip install whitenoise

# Add requirements.txt
    this would be added to yur project root
    -get the requirement files with (pip freeze) command
# procfile in project root 
        web: gunicorn mysite.wsgi --log-file -

# configure your whitenoise to server static files
    in your settings.py add these
    from whitenoise.django import DjangoWhiteNoise

    STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
    STATIC_URL = '/static/'

    STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

    STATICFILES_DIRS = (
        os.path.join(BASE_DIR, 'static'),
    )

    add "'whitenoise.middleware.WhiteNoiseMiddleware',"
    as the first ement on your middleware list

# time to work on heroku
    -so from comand line, loginto your heroku account "heroku login" i.e you already have heroku cli installed on your system
    -create an app on your heroku account "heroku create name_of_app"
    -you can add pastgres db addon "heroku addons:create heroku-postgresql:hobby-dev" you dont have to do it        imidiately tho
    - use this to disable collect static "heroku config:set DISABLE_COLLECTSTATIC=1"

    
