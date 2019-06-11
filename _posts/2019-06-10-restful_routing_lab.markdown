---
layout: post
title:      "RESTful Routing Lab"
date:       2019-06-10 23:50:52 -0400
permalink:  restful_routing_lab
---


Today we will be walking through the RESTful Index Action Lab which is part of the Rails Intro to REST section.  To begin, you will need to fork and clone the lab and run bundle install.  Once all the dependencies have loaded.  You will then run "rake db:create && rake db:migrate && rake db:seed".  Once that is done, run the test suite and there will be two failures.

![screenshot1](https://i.imgur.com/jSI9tFp.png.jpg)

We will start with the first failing test.  We have a Student model but there is no route for a student index page and there is no Student controller.  The first thing we need to do is add the route.  Routes are in the config folder in the routes.rb file.

![](https://i.imgur.com/Wyhkk6e.png)

We could use resourceful routing here but for the sake of simplicity, we will just add the singular route the tests are looking for.

![](https://i.imgur.com/FEXNMkW.png)

What this route means is that if somebody visits the "/students" url of our application, the rails app will match it to the student controller index action.  We don't have students controller so we will need to add that.  Controllers go into the app directory under the controller file.  

![](https://i.imgur.com/PBlvJNH.png)

![](https://i.imgur.com/Dv4PzZ9.png)

We then need to add an index action to the students controller.

![](https://i.imgur.com/RyaIBLV.png)

Now if we run the tests, the error has changed.

![](https://i.imgur.com/7LqYJ0H.png)

We are getting this error because there is no student/index template in our views folder so we will need to add that.

![](https://i.imgur.com/v0nOA3Y.png)

Now when we run our tests, the first one is passing.  The remaining error is because multiple students are not showing up on the page.  We have a database of students that can be accessed through the student model.  We will want to access that data in our controller and pass it to our view using an instance variable.  We will then iterate over the data and display it in our view.  When we fire up the rails server we can go to the /students url and see that it is working and all tests are now passing.

![](https://i.imgur.com/DuigTXY.png)

![](https://i.imgur.com/QRHShst.png)

![](https://i.imgur.com/wDO6tQH.png)

![](https://i.imgur.com/q7nXQhf.png)
