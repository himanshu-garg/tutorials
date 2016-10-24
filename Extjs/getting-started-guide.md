# Getting Started Guide to Extjs

Extjs is an javascript application framework to create cross platform applications.  Current version of Extjs is 6 at the time of writing this doc.

## Downloads
1. Download Extjs GPL version (https://www.sencha.com/legal/gpl/). With GPL license, you have to disclose your source code under GPL license.
2. Download Sencha command (https://www.sencha.com/products/extjs/cmd-download/).  It is used for complete application build and especially helps in code minification.

## Create a sample application
Here we will build a small application from scratch.
Suppose, the extracted extjs sdk is at ~/extjs-sdk/ and we will create an application under ~/sample-app/

1. Generate application using sencha cmd.
```
cd ~/sample-app/
sencha -sdk ~/extjs-sdk/ generate app -classic SampleApp ./
```
This will generate the complete application structure
```
app     app.json       bootstrap.js    build      ext         overrides  Readme.md  sass
app.js  bootstrap.css  bootstrap.json  build.xml  index.html  packages   resources  workspace.json
```

2. Run a localhost server using `sencha app watch`
```
sencha app watch
```
This will start a local sever on http://localhost:1841 and listen to changes done in code.  Access it and you will see a sample application running.

3. ~/sample/app/ is the main folder that contains all the main code that we will edit/add to create an application.

4. ```
    ~/sample-app/app:
    Application.js  model  Readme.md  store  view
    ```
    - Application.js is the start point that defines main Application
    - store contains the data for views.
    - model contains the definition for store.
    - view contains the main components to be displayed.

5. Since, we have to write from scratch, lets remove all the existing files.
```
rm -rf ~/sample-app/app/view/*
rm -rf ~/sample-app/app/store/*
rm -rf ~/sample-app/app/model/*
```

6. Lets create a table (called grid in extjs terms) with a row click event.
Create a file `~/sample-app/app/view/main/Main.js`
```
Ext.define('SampleApp.view.main.Main', {
    extend: 'Ext.grid.Panel',
    xtype: 'app-main',

    requires: [
        'Ext.plugin.Viewport',
        'SampleApp.store.main.Employees',
        'SampleApp.view.main.MainController'
    ],

    controller: 'main',
    store: {
        type: 'employees'
    },

    columns: [
        {text: 'First Name', dataIndex: 'firstName', flex: 1},
        {text: 'Last Name', dataIndex: 'lastName', flex: 1},
        {text: 'Position', dataIndex: 'position', flex: 1}
    ],

    listeners: {
        select: 'onSelect'
    }
});
```
Here, we have defined a view called "Main" with columns and store as "employees" along with "row select" event listener.

7. Lets define data in store "employees".  
Create a file `~/sample-app/app/store/main/Employees.js`
```
Ext.define('SampleApp.store.main.Employees', {
    extend: 'Ext.data.Store',
    alias: 'store.employees',

    fields: ['firstName', 'lastName', 'position'],
    data: [
        {firstName: 'Peter', lastName: 'Vill', position: 'Accountant'},
        {firstName: 'John', lastName: 'P.', position: 'Admin'},
        {firstName: 'Sarah', lastName: 'Williams', position: 'HR'},
        {firstName: 'Riki', lastName: 'John', position: 'Admin'},
        {firstName: 'Neil', lastName: 'Radar', position: 'Tech Lead'}
    ],

    proxy: {
        type: 'memory'
    }
});
```
Here, we have saved data in memory.  There are methods to fetch data from external urls using Ajax calls.

8. Now, define a controller that will take action based on the row click event.  Create a file `~/sample-app/app/view/main/MainController.js`
```
Ext.define('SampleApp.view.main.MainController', {
    extend: 'Ext.app.ViewController',

    alias: 'controller.main',

    onSelect: function (sender, record) {
        Ext.Msg.confirm('Confirm', 'Are you sure?', 'onConfirm', this);
    }
});
```
Here, on row click, it will show a confirmation dialog box.

9. Now, open http://localhost:1841/ and see a table.  Click on any row and you will see a confirmation dialog box.

---
So, this is just a small step towards understanding extjs for beginners.

## Resources
1. http://docs.sencha.com/extjs/6.0.1/guides/getting_started/getting_started.html
2. http://examples.sencha.com/extjs/6.0.1/examples/
