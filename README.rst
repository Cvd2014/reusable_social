=====Social Network Auth =====
Social-Auth is a reusable authorization app for Django
Detailed documentation is in the "docs" directory.
Quick start -----------
1. Add "reusable_auth" to your INSTALLED_APPS setting like this::
    INSTALLED_APPS = (         ...         'reusable_social_auth',     )


2. Add these  settings to your projects settings.py:
TEMPLATE_CONTEXT_PROCESSORS = (
   'django.contrib.auth.context_processors.auth',
   'django.core.context_processors.debug',
   'django.core.context_processors.i18n',
   'django.core.context_processors.media',
   'django.core.context_processors.static',
   'django.core.context_processors.tz',
   'django.contrib.messages.context_processors.messages',
   'social.apps.django_app.context_processors.backends',
   'social.apps.django_app.context_processors.login_redirect',
)

AUTHENTICATION_BACKENDS = (
   'social.backends.facebook.FacebookOAuth2',
   'social.backends.google.GoogleOAuth2',
   'social.backends.twitter.TwitterOAuth',
   'django.contrib.auth.backends.ModelBackend',
)




LOGIN_REDIRECT_URL='/'

SOCIAL_AUTH_FACEBOOK_KEY=<Your Key here>
SOCIAL_AUTH_FACEBOOK_SECRET=<Your Key here>

SOCIAL_AUTH_GOOGLE_OAUTH2_KEY=<Your Key here>
SOCIAL_AUTH_GOOGLE_OAUTH2_SECRET=<Your Key here>

SOCIAL_AUTH_TWITTER_KEY=<Your Key here>
SOCIAL_AUTH_TWITTER_SECRET=<Your Key here>


3. To get keys you will need to access the sites developer options
   Facebook: Go to https://developers.facebook.com/apps/?action=create and click the green “Create New App” button.
             In the settings of the newly-created application, click “Add Platform”. From the options provided, choose Web, and fill in the URL of the site (http://test1.com:8000 in our example).

   GOogle:Go to https://console.developers.google.com/ and create a new application.
          Make sure you add G+ API to allowed APIs
          Under APIs and Auth > Credentials, create a new Client ID.
          Make sure to specify the right callback URL: http://test1.com:8000/complete/google-oauth2/

   Twitter: Go to https://apps.twitter.com/app/new and create the new application
            The callback URL should be something like http://test1.com:8000/complete/twitter/


   I have added a map in my etc/hosts file mapping local directory to test1.com to allow for testing you can change this in the social apps setting when you go to production

4. Run `python manage.py migrate`.


5. Visit http://127.0.0.1:8000/blogs/ to view the blogs you create