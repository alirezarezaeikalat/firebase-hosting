1. To use hosting, first you have to make firebase hosting,
then go to hosting tab, first you need to install firebase-tools

  npm install -g firebase-tools

then go to your project folder and sign in to google and
  initialize the project locally:
    
    a. firebase login
    b. firebase init

first you need to select the firebase service that you want to use,
      select hosting

Then you have to select your firebase project that you made on
  firebase console.
and select the folder to deploy on server, the default is public

2. the firebase makes some folder and files for you:

    a. firebase.json: some configuration for your project
    b. .firebaseserc: define the project in server side
    c. public folder: the folder that is going to be deploy

3. Then you have to move your files to the public folder, to 
  be deployed on the server.

4. With firebase tools, there is local server, you can test your
  projects, with this develpment server:

      firebase serve

if this command is not working use this:

      firebase serve -p 5000 -o 127.0.0.1

5. Then you have to deploy your app:

    firebase deploy

6. You can specify the number of version that a firebase will 
  save in hosting panel in firebase console, and you can role back
  to the older version if you want to.

7. deploying Vue app as a single page application in firebase
   hosting:

    7.1 first you need to initialize locally:
      a. firebase login
      b. firebase init

    7.2 then we have to select a dist folder for deployment:
      [ATTENTION]
      select (dist) as deploy folder because when we build our
      Vue application it is going to build in this folder

      after that we don't have 404 page in dist folder.

    7.3 Then you have to build your vue app:
        npm run build

    7.4 Then test it in firebase server:

          firebase serve
            Or
          firebase serve -p 5000 -o 127.0.0.1
    
    7.5 Then deploy the project:

          firebase deploy

8. To redirect in your website you need to add redirects field
 in firebase.json file: 

      {
        "hosting": {
          "redirects": [
            {
              "source": "/about",
              "destination": "/",
              "type": 301
            },
            {
              "source": "/contact",
              "destination": "/",
              "type": 302
            }
          ],
          "public": "public",
          "ignore": [
            "firebase.json",
            "**/.*",
            "**/node_modules/**"
          ]
        }
      }
    
