# Code Review for Xavier Poh

## Project Repo

[Xavier's Project Repo: Photozine](https://github.com/wdi-sg/wdi-project-2-random-9)

[Actual Web App](https://pacific-coast-30390.herokuapp.com/)

## Review

#### Project Purpose

This project is a full-stack web app that allows photographers to upload their photos online, and for users to build albums/curations of the photos that they like.

#### Project Organization

#### Features

* Image Upload via Cloudinary and Multer
* Three models (User, Photo, and Zine) with full CRUD functionality
* 'Zines' can form personalized collections of a user's favourite photos
* Bootstrap CSS Framework with a Boostrap Template
* Node.js, Express, Mongoose, MongoDB

#### Areas of Success (Code, Organization)

* Code is very well-structured according to the MVC framework. Routes contain directions, controller contains logic.
* Good client-side validation. I observed that the forms will not let you submit information if the fields are blank. This prevents it from even going to the server, so you don't waste time with server-side validation when you can already block it at the client level.
* Good use of `$push` and `$pull` to update Zines with Photos.

#### Areas for Improvement (Code, Organization)

* Remove `pre` code for the user profile when deploying to Heroku.
  * You can designate separate views for development environment vs. deployed product. So while in development, you can see the `pre` code to facilitate your coding process, but all these internal bits of data are hidden from the user when deployed.

## Additional Notes
* Good use of Bootstrap Template to give the web app a professional feel
* Consider randomizing the order of the photos displayed in 'View All'
* To optimize UX - Add 'back' buttons, provide more flow.
