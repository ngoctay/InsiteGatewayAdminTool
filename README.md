# Barton Admin Tool


## Dependencies
- nodejs https://nodejs.org/en/ (v6+)
- MongoDB https://www.mongodb.com/ (v3.2)
- Heroku Toolbelt https://toolbelt.heroku.com
- git


## Configuration
Back end configuration is at `config/default.js`, you may also set env variables.
You may need to update the MONGODB_URI parameter to point to a new database.

Front end configuration is at `public/js/config.js`, you needn't change it.


## Local deployment
- Start MongoDB server
- Install dependencies `npm i`
- Run code lint check `npm run lint`
- Run tests `npm run test`, note that running tests will clear all data
- Initialize data `npm run init-data`
- Start app `npm start`
- Access `http://localhost:3000`
- Login with `admin@test.com / abc123`


## Heroku deployment
- git init
- git add .
- git commit -m 'message'
- heroku login
- heroku create [application-name] // choose a name, or leave it empty to use generated one
- heroku addons:create mongolab // create Mongo Lab add-on
- git push heroku master // push code to Heroku
- to initialize data, run `heroku run bash`, in the bash, run `npm run init-data`, then `exit`;
  or simply run `heroku run npm run init-data`

## Application Demo
https://misha-bat.herokuapp.com/

Login with `admin@test.com / abc123`


## Notes
- This submission uses the suggested Angular 1.5.5, and I think this should be used. The reason is that:
  When I simply directly used Angular with the client components, there are problems rendering the page
  when route is changed, new routed page is blank, this is probably because Angular and client components
  have different handling for custom tags.
  Fortunately, client provided a component, i.e. bower_components\ng-polymer-elements, which solves the conflict,
  we should follow that client component, and that component uses Angular 1.5.5.
- For this initial development, I simply put back end and front end together; but it is easy to separate them if needed,
  the back end is CORS ready, and the front end can configure back end base URL, so it is just to deploy the front end
  `public` folder separately.
- This submission simply includes all client components, because it is probably more componennts are used in other pages,
  we may remove unused components later when in production.


## Devices

**Notes**

- the `src/add-users.js` is changed to `src/init-data.js`, because it now also inserts other data
- Postman tests, mocha tests are added for the new API
- the above Heroku app link is updated
- the IE view and Mobile view are checked, for mobile view check you may use Chrome developer tool,
  note that when for mobile view check, you will need to click the button near the site dropdown to collapse/expand the left panel

**Video for Device tags**

https://www.screencast.com/t/XUcAIxrwlfR (install/enable flash player)


**Enhancements**

- the mongoose promise is set to use global bluebird promise, the original outdated mongoose promise warning is gone now
- the original eslint code check doesn't check the test files, they are now checked
- when data got dirty (data are changed but not saved), user will get confirmation when:
  select other site;
  select other device;
  change page tab;
  create new device


**Video**

See: https://youtu.be/w6wXCUN2ESc


**Sample curl command**

Below is sample curl command to create a child device by using a parentId field, note that it is a command in Mac, other OS curl
command maybe a little different:

``
curl -H "Content-type: application/json" -X POST -d "{\"name\":\"device-name\",\"ingressPathId\":\"59141b285ba5750a738e8a9e\",\"activationCode\":\"code\",\"connectionString\":\"http://a.b.c\",\"model\":\"model\",\"firmware\":\"firmware\",\"createdBy\":\"user\",\"lastDataPoint\":\"2017-05-06T01:02:03.111Z\",\"parentId\":\"59141b285ba5750a738e8aa3\",\"siteId\":\"59141b285ba5750a738e8a9b\"}" http://localhost:3000/api/v1/device
``


## Device Profiles

**Notes**

- Postman tests, mocha tests are added for the new API
- the above Heroku app link in the `Heroku deployment` section is updated, it shows the latest app
- Chrome, IE, and Mobile view are checked, for mobile view check you may use Chrome developer tool,
  note that when for mobile view check, you will need to click the button near the site dropdown to collapse/expand the left panel
- when data got dirty (data are changed but not saved), user will get confirmation when:
  search profiles;
  select profile;
  change page tab;
  create new profile;
  download profile
- from the forum discussion, the `Add Selected` button will do channel synchronization, it may add or remove channels;
  if user searches some channels, only the searched channels will be synchronized, for example,
  if a profile has channel A, but A is not in right side searched channels, then when doing sychrnozation, channel A will not be changed
- add/remove channel will make the profile `dirty`, i.e. data changed but not saved


**Video**

See: https://youtu.be/MNFHLT4kHZY


## Operations & Roles

**Notes**

- Postman tests, mocha tests are added for the new API
- the above Heroku app link in the `Heroku deployment` section is updated, it shows the latest app
- menu for small width device e.g. iPhone 5 in chrome developer tool, is fixed so that last items is also shown

**Video**

See: https://youtu.be/tpPsjCcDbrA
