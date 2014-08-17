---
layout: post
title: Sass on Sails!
---

My wandering around the web has finally led me to SailsJS land. So far I love the concepts (Coming from Rails land and loving JS lately ;). Just before my exporations with Sails, I worked on a project using; 

* MongoDB
* Express
* Angular

This is also known as the MEAN stack. To get up and running quickly I kickstarted it with a very usefull boilerplate generator [Angular Fullstack Generator](https://github.com/DaftMonk/angular-fullstack.git)

Along the way I realised I needed some socket.io love and so I integrated it into it. Looking up a few issues and how to resolve them, I encountered the SailsJS project. So now I want to migrate my existing app to SailsJS. I checked out a few posts and ended up on [StackOverflow](http://stackoverflow.com/questions/21938850/angularjs-sailsjs)

Just before I could get to see a live page, I realised I needed Sass tasks. So this is how I got it running.

##Installing Sass Module
In my prevoius project sass was compiled with the help of grunt-contrib-compass module. I decided to use grunt-contrib-sass for this since I wasn't sure yet how its dealing with the other assets which I was using compass on.

  npm install grunt-contrib-sass

If you are using Sails >= 1.0, you should see a tasks folder with the various grunt tasks.
Copy the less.js content into a new sass.js file in the same folder.

Edit as follows;

    module.exports = function(grunt) {

        grunt.config.set('less', {
            dev: {
                files: [{
                    expand: true,
                    cwd: 'assets/styles/',
                    src: ['*.scss', '*.sass'],
                    dest: '.tmp/public/styles/',
                    ext: '.css'
                }]
            }
        });

        grunt.loadNpmTasks('grunt-contrib-sass');
    };

Now update your compileAssets.js file in **tasks/register/** directory and change the `less:dev` to `sass.dev`

Now Sails should stop whinning about our Sass files.

Hope you find this useful.

---


