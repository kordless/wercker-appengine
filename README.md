# Wercker Appengine Deploy
[Wercker Step](http://wrecker.com) that allows you to deploy your App Engine applications with Continuos Integration.

[![wercker status](https://app.wercker.com/status/4a77807f88f6ca4d01322ad27cd32ca1/m "wercker status")](https://app.wercker.com/project/bykey/4a77807f88f6ca4d01322ad27cd32ca1)


## Basic usage
To use this tool simply create a wercker.yaml in your application root and insert:
```
box: wercker/default
  deploy:
      steps: 
        - nicocanali/appengine-deploy:
            email: $EMAIL
            app_pwd: $APP_PWD
```

**EMAIL** and **APP_PWD** will be the name of the (private) variables you'll need to set up in your Wrecker settings page, under **Deploy Targets**. Even though these variables are private, it would be better to use an **App password**, which you can generate from you [Google Account Settings Page](https://www.google.com/settings)

Also, make sure you add the following lines at the of your *app.yaml* file:

```
skip_files:
- google_appengine/.*
```

This will prevent App Engine from uploading the SDK, which was locally downloaded by the Wrecker Step to deploy the app.
