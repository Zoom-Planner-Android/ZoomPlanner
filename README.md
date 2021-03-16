# Zoom Planner

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
This app will be a planner/organizer dedicated to organizing Zoom links in one location. 

### App Evaluation
- **Category:** Productivity
- **Mobile:** Push notifications, 
- **Story:** Zoom isn't going away anytime soon, so the reception of a Zoom link organizer would appeal to our audience very well. Students and peers would find the usefulness in assuaging Zoom fatigue by removing a barrier to accessing Zoom links. 
- **Market:** Large size and scope. Audience is students, professionals, and anyone using Zoom recreationally. 
- **Habit:** The user can create events and populate their Zoom link organizer. The user will access the app multiple times a day depending on their needs. 
- **Scope:** The concept of the app is similar to a Calendar but using a Zoom API. The front-end part of the application should be easy to complete by the deadline. The back-end part of the application will make use of the Zoom API and populate the front-end with useful data. 

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**
* User must be able to add and store a given zoom link within the app
* User must be able to see day and time of a given zoom link
* Users should see all stored zoom links in one tab in a vertical fashion
* User should get a push notification alert X minutes before the meeting starts.
* Allow users to give a "name/nickname" for a zoom link so they know which link corresponds to what class/meeting
* User should view Zoom meetings in a calendar form

**Optional Nice-to-have Stories**

* User could be able to find the iCloud recording link for a given zoom link in the app.
* Organize links by time/day that they are scheduled.
* User could be able to link their Calendar to find best time to create Zoom link.

### 2. Screen Archetypes

* Stream 
    * Users should see all stored zoom links in one tab in a vertical fashion   
    * User must be able to see day and time of a given zoom link
    * User could be able to find the iCloud recording link for a given zoom link in the app.
    * Organize links by time/day that they are scheduled.
* Creation
    * User must be able to add and store a given zoom link within the app
    * Allow users to give a "name/nickname" for a zoom link so they know which link corresponds to what class/meeting
* Settings
    * User should get a push notification alert X minutes before the meeting starts.
* Calendar
    * User should view Zoom meetings in a calendar form

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Home tab that contains all of the zoom links
* A tab that allows a user to add a new zoom link
* A tab for settings to allow push notifications 
* (Optional) tab that allows to see cloud recent cloud recordings

**Flow Navigation** (Screen to Screen)

* Calendar
  => Creation Screen, Stream Screen
* Creation Screen
  => Calendar, Creation Screen (after posting link)
* Stream Screen
  => None
* Settings
  => None 

## Wireframes
<img src= "https://user-images.githubusercontent.com/77361496/111385297-f4724f00-8680-11eb-923a-674f43a0ec26.jpg" width="500" height="200"> 

### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype

## Schema 
### Models
#### ZoomPost
   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | ZoomURL      | String   | unique id for the Zoom link (default field) |
   | host        | String | name of meeting host |
   | image         | File     | image of host profile |
   | meetingStart     | DateTime | date and time when meeting starts |
   | meetingEnd     | DateTime | date when time when meeting ends |
   | meetingID     | String | Zoom meeting ID |
   | title | String | Zoom meeting name | 
   
### Networking
- Stream Screen
    - (Read/GET) Query all ZoomPosts
         ```swift
         let query = PFQuery(className:"ZoomPost")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) Zoom links.")
           // TODO: Do something with posts...
            }
         }
         ```
    - (Delete) Delete existing ZoomPost (after meeting ends automatically or manually) 
- Creation Screen
    - (Create/POST) Create a new ZoomPost object
- Calendar Screen
    - (Read/GET) Query all Zoom Posts and put in a Calendar format 
    - (Delete) Delete existing ZoomPost (after meeting ends automatically or manually) 
- Settings Screen
    - None 

#### [OPTIONAL:] Existing API Endpoints- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
