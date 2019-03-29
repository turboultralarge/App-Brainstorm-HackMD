# App-Brainstorm-HackMD
Initial group meeting / app brainstorming

# TurboUltraLarge brainstorming

Possible areas of interest: education, productivity, lifestyle, entertainment

## 1.) Education
- Angry birds but you use the birds to either strike or be your answer to solve a problem. 

- Stock app that allows you to compete with friends while you embark on your investment advuenture game.

- 

## 2.) Productivity
- 

## 3.) Lifestyle
- Automate my room door

- An app that gives you a morale boost whenever you need it

- 

## 4.) Entertainment
- Lit - Las Vegas app to find popular, hot places to visit baswed on a heatwave map detaling where other users are

## 5. ) Travel

### TurboTravel

- An ultrafast method of walking to your destination. User is directed to fastest route using real-time waypoints 
    - Directions are voted on based on user's experience to ensure the correct path is marked
    - Using Google Map's API and ARKit


## Wireframes
<img src="https://imgur.com/rH7Prfx" width=800><br>

### [BONUS] Digital Wireframes & Mockups
<img src="" height=200>

### [BONUS] Interactive Prototype
<img src="" width=200>

## Schema 
### Models
#### Post

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | UserID        | String   | unique id for the user |
   | ParentImageID | int      | references a KeyImageID connected to userID |
   | ChildImageID  | int      | photos attached to KeyImageID |
   | CollectionTitle|String   | Title for a collection of images |
   
### Networking
#### List of network requests by screen
   - Home Feed Screen
      - (Read/GET) Query all posts where user is author
         ```swift
         let query = PFQuery(className:"Post")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) posts.")
           // TODO: Do something with posts...
            }
         }
         ```
      - (Create/POST) Create a new like on a post
      - (Delete) Delete existing like
      - (Create/POST) Create a new comment on a post
      - (Delete) Delete existing comment
   - Create Post Screen
      - (Create/POST) Create a new post object
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile image
      
