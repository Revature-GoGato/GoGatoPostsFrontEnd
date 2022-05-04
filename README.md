# GoGato


#### _A Social Media Application_


## What is GoGato?

GoGato is a social media site where users can share stories that interest them.

Users can comment on posts and discover new trending topics.

Read something cool? Leave a like to give the author GoGato points!


## What is the GoGato application composed of?

The GoGato backend was built using Java Spring Boot.

The Posts and Users API currently function independently. However, there is

potential for the application to transition to a microservices architecture in the future.

GoGato's frontend was built with the React.js library.


## Site Design and Functionality

Live demo (requires Posts and Users API to be running locally): 

[https://gogatotest.vercel.app/](https://gogatotest.vercel.app/)

Visitors to the GoGato site can do the following:



* Register
* Login
* View and update their profile
* Create and delete posts
* Comment on posts and reply to comments
* View the amount of likes on a post
* View their timeline
* View trends

When users log into the application, their userId is saved as a Local Storage entry. This information is kept until the user logs out. The Navigation.js component checks the currentUser to ensure that logged out users are unable to view pages other than login or registration.

When a user checks the timeline, the program retrieves a list of posts that will be looped through to create a list of renderable posts. During this loop a recursive function is called on every post to find comments correlated to that post. Using a combination of looping and recursion we create the timeline seen on the site. This allows users to comment on comments and posts alike.   

Profile pages are generated by sending a GET request for the userId matching the ID in the URL (e.g. …/profiles/1). If the profile userId matches the currentUser, edit options will be available.


## Posts API

The GoGato Posts API provides the following functionalities:



* Create/Update/Delete Posts
* Retrieve a Post by userId
* Retrieve all Posts
* Create a Like
* Retrieve a Like by userId
* Retrieve all Likes
* Update/Delete Like by userId

The Posts API is used to update, create, and retrieve Posts and Likes. Its methods, classes, and interfaces are documented via JavaDocs. Post and Likes data is persisted to a PostgreSQL database hosted on AWS. The tables for the RDMS were created manually using SQL. Lombok was used to cut down on getter, setter, and constructor boilerplate code.


## Users API

The GoGato Users API provides the following functionalities:



* Create/Register a User
* Login/Validate a User
* Find a User by userId or username
* Update a User's firstName, lastName and aboutMe
* Update a User's points

The Users API is used to update, create, and retrieve Users. Its methods, classes, and interfaces are documented via Swagger OpenAPI and JavaDocs. For encryption, the Users API utilizes a static BCrypt hash. User data is persisted to a PostgreSQL database hosted on AWS. The tables for the RDMS are created programmatically via Spring JPA with Hibernate. Lombok was also used to cut down on getter, setter, and constructor boilerplate code.

Although the Users API does include the Eureka client dependency, the application as a whole does not support a microservices architecture at this time.

—


### Users API Endpoints

Please see Swagger documentation for a full description of requests.


<table>
  <tr>
   <td>USERS
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>/users
   </td>
   <td>POST: Create a new User
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>GET: All Users
   </td>
  </tr>
  <tr>
   <td>/users/{identifier}/
   </td>
   <td>GET: User by userId or Username
   </td>
  </tr>
  <tr>
   <td>/users/{identifier}/
   </td>
   <td>PUT: Update a User's points
   </td>
  </tr>
</table>



<table>
  <tr>
   <td>LOGIN
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>/login
   </td>
   <td>POST: Verify a User's credentials
   </td>
  </tr>
</table>



<table>
  <tr>
   <td>PROFILES
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>/profiles/{identifier}/about
   </td>
   <td>PUT: Update a User's points
   </td>
  </tr>
  <tr>
   <td>/profiles/{identifier}/name
   </td>
   <td>PUT: Update a User's name
   </td>
  </tr>
</table>



### Posts API Endpoints


<table>
  <tr>
   <td>POSTS
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>/post
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>/post/userid/:userid
   </td>
   <td>GET: Post by userid
   </td>
  </tr>
  <tr>
   <td>/post/userid/:parentid
   </td>
   <td>GET: Post by parentid
   </td>
  </tr>
  <tr>
   <td>/post/create
   </td>
   <td>POST: Create a new post
   </td>
  </tr>
</table>



<table>
  <tr>
   <td>LIKES
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>/likes
   </td>
   <td>GET: Return list of Likes
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>POST: Create a Like
   </td>
  </tr>
  <tr>
   <td>/likes/{userId}
   </td>
   <td>GET: Return list of Likes by userId
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>PUT: Update a Like for {userId}
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>DELETE: Delete a like for {userId}
   </td>
  </tr>
</table>
