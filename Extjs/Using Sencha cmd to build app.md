# Using Sencha Cmd to build app

1. Download sencha cmd http://www.sencha.com/products/sencha-cmd/download/

2. Extract and chmod +x Sencha*.run

3. ./Sencha*.run

4. $ sencha

5. Ruby is required to build app, so install ruby, otherwise following error occurred

    ```
    [himanshu@localhost myapp]$ sencha app watch
Sencha Cmd v5.1.3.61
[INF] Processing Build Descriptor : default
[INF] Loading app json manifest...
[INF] Appending content to /home/himanshu/one.com/myapp/bootstrap.js
[INF] Writing content to /home/himanshu/one.com/myapp/bootstrap.json
[INF] merging 219 input resources into /home/himanshu/one.com/myapp/build/development/MyApp/resources
[INF] merged 219 resources into /home/himanshu/one.com/myapp/build/development/MyApp/resources
[INF] merging 0 input resources into /home/himanshu/one.com/myapp/build/development/MyApp
[INF] merged 0 resources into /home/himanshu/one.com/myapp/build/development/MyApp
[INF] writing sass content to /home/himanshu/one.com/myapp/build/temp/development/MyApp/sass/MyApp-all.scss.tmp
[INF] appending sass content to /home/himanshu/one.com/myapp/build/temp/development/MyApp/sass/MyApp-all.scss.tmp
[INF] appending sass content to /home/himanshu/one.com/myapp/build/temp/development/MyApp/sass/MyApp-all.scss.tmp
[INF] writing sass content to /home/himanshu/one.com/myapp/build/temp/development/MyApp/sass/config.rb
[INF] executing compass using system installed ruby runtime
[ERR]
[ERR] BUILD FAILED
[ERR] com.sencha.exceptions.ExProcess: Failed creating background process
[ERR] 	at org.apache.
[ERR] tools.ant.UnknownElement.execute(UnknownElement.java:291)
[ERR]
[ERR] Total time: 3 seconds
[ERR] The following error occurred while executing this line:
/home/himanshu/one.com/myapp/.sencha/app/build-impl.xml:246: The following error occurred while executing this line:
/home/himanshu/one.com/myapp/.sencha/app/watch-impl.xml:59: The following error occurred while executing this line:
/home/himanshu/one.com/myapp/.sencha/app/build-impl.xml:284: The following error occurred while executing this line:
/home/himanshu/one.com/myapp/.sencha/app/sass-impl.xml:155: The following error occurred while executing this line:
/home/himanshu/one.com/myapp/.sencha/app/sass-impl.xml:176: com.sencha.exceptions.ExProcess: Failed creating background process
[himanshu@localhost myapp]$
```

6. Generate a app
```
sencha generate app MyApp myapp
```

MyApp is name of application and myapp is the location

7. cd myapp

8. sencha app watch

visit http://localhost:1841/
