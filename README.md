# Wercker Appengine Deploy
[Wercker Step](http://wrecker.com) that allows you to deploy your App Engine applications with continous integration.

[![wercker status](https://app.wercker.com/status/4a77807f88f6ca4d01322ad27cd32ca1/m "wercker status")](https://app.wercker.com/project/bykey/4a77807f88f6ca4d01322ad27cd32ca1)


## Basic usage
To use this tool simply create a wercker.yaml in your application root and insert:
```
box: wercker/default
  deploy:
      steps: 
        - stackmonkey/appengine-deploy:
            email: $EMAIL
            app_pwd: $APP_PWD
```

**EMAIL** and **APP_PWD** will be the name of the (private) variables you'll need to set up in your Wrecker settings page, under **Deploy Targets**. Configure this from the [Google App Password page](https://security.google.com/settings/security/apppasswords).

Finally, add the following lines at the of your *app.yaml* file:

```
skip_files:
- google_appengine/.*
```

This will prevent App Engine from uploading the SDK, which was locally downloaded by the Wrecker Step to deploy the app.
