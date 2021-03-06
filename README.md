# sailscast-activityOverlord

a [Sails](http://sailsjs.org) application

code walkthrough tutorial of: [Building Sails app](https://www.youtube.com/playlist?list=PLOG4lw1-sUaHgpn3TKz1Q8CTzezHVDZZu)

To checkout code at specific snapshots use git tags

    git tag 1-setup
    
## 1-setup

    npm install -g sails
    sails new project_name
    sails lift
    
## 2-bootstrap

We'll user bower to manage some of the common packages

    npm install -g bower
    bower init

Create `.bowerrc` file with:

    {
      "directory": "assets/bower_components"
    }
    
Then install bootstrap to our asset directory. 

    bower install bootstrap
    
Sails injects code from asset directory to build your templates. In `tasks/pipeline.js` modify file to include the
bootstrap path `'bower_components/bootstrap/dist/css/**/bootstrap.min.css'` to have bootstrap linked to your `layout.ejs`
file.

Create `static` dir in `views` folder and create `index.ejs` in state folder`
In `config/routes.js` modify the default root route to:

    '/': {
        view: 'static/index'
      }

Now `sails lift` and you should see the index page styled by bootstrap.

Head over to `views/layout.ejs` and add a navbar and footer to your base template.

## 2b-styling

Additional styling. 
* `bower install jquery` . 
* Modify `tasks/pipeline.js` to load `jquery.js`
* Create a new `styles/custom.less` file to modify things to your liking 
* Add a reference to your custom.less file to `assets/styles/importer.less`

## 3-user

* `sails generate api user`
* fill out `api/models/User.js` with the fields you want
* create new folder `views/user/new.js` and put form markup there
* create new `new` function in `api/controllers/UserController.js` to register blueprint route
* add form css to `assets/styles/custom.less`



    

