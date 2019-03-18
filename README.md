# Comprehensive Technical Assessment (CTA) - FellowBloggerV2

# Table of Contents
  * [Github / App Setup](#github-app-setup)
  * [Instruction Staff Github Accounts](#instruction-staff-accounts)
  * [Project Specifications](#project-specifications)
  * [Resources](#resources)
  * [Collections and Client (iOS App) Model Properties](#mvp-collections)
  * [FellowBloggerV2 MVP Checklist Requirements](#mvp-requirements) 
  * [Saving Images to Storage](#saving-images)
  * [Extra Credit Checklist](#extra-credit-checklist)
  * [MVP Rubric](#mvp-rubric)
  * [Extra Credit Rubric](#extra-credit-rubric)
  * [Extra Credit Collections](#extra-credit-collections)

Welcome to the compreshensive technical assessment iOS final. You will be building a blogging app. The FellowBloggerV2 is a blogging app that enables users to post and view other blogs created by fellow bloggers. The backend is created using Firebase. The database has existing data. You will be using the included GoogleService-Info.plist file to read and write to Firebase. Everyone will be using the same database to give the project a more real life feel with having existing users. Firebase handles authentication, database and storage requirements for the app. 

As you continue to work through this project make regular commits because we will be monitoring your commit history for code consistency and educational integrity. 

Have fun, be creative and huge acknowledgement on your progress throughtout the [Pursuit Core curriculum](https://github.com/joinpursuit/AC-iOS). 

## Github / App Setup <a name="github-app-setup"></a>

- [x] Create a private repo
- [x] Add a link to this repo on your README.md
- [x] Invite the iOS instruction staff as collaborators to your repo
- [x] Create an Xcode project 
- [x] Install the Firebase pods including Kingfisher and Toucan (see Podfile code snippet below)
- [x] After pods are installed open up .xcworkspace
- [x] Download the GoogleService-Info.plist file provided and add to your Xcode project. **Reminder** The .plist file must be named as is **GoogleService-Info.plist** , any parenthethis e.g (2) in the name will result in a runtime crash from Firebase (make sure "copy items as needed" is selected)
- [x] git clone your repo to your computer
- [x] add your Xcode project to your repo
- [x] add this bundle id ```com.alexcpaul.FellowBloggerV2```
- [x] push to master
- [x] Create a "dev-yourname" e.g "dev-alex" branch so you can make pull requests against "master" when needed ```git checkout -b dev-alex```
- [x] Push your dev branch to remote e.g command ```git push --set-upstream origin dev-alex``` 
- [x] We will be monitoring your commits as a way to avoid inconsitencies and educational integrity with your work, commit regularly (at least 3 - 5 commits per day at minimum)
- [ ] You can make your first pull request against "master" as early as Monday 10 am to be reviewed by the instruction staff, the latest day to make your first pull request is Wednesday at 10 am 
- [ ] After your PR (pull request) has been approved by an instruction staff member it will then be merged to the "master" branch
- [ ] You are required to be in class throughout this week while working on this assessment
- [ ] Your commit history and progress will determine if you have the option to work from home next week, however if your commit history is dropping and progress as well you will be required to continue working on the assessment at Pursuit. 
- [ ] Your final pull request should be made on Friday (due date of the assessment)

**Podfile if you (selected unit test) when you created the Xcode Project**   

```c 
platform :ios, '12.0'

use_frameworks!

def fellow_blogger_pods
  pod 'Firebase/Core'
  pod 'Firebase/Auth'
  pod 'Firebase/Firestore'
  pod 'Firebase/Storage'
  pod 'Kingfisher'
  pod 'Toucan'
end

target 'FellowBloggerV2' do
  fellow_blogger_pods
end

target 'FellowBloggerV2Tests' do
  fellow_blogger_pods
end
```

**Podfile if you (did not) select unit test when you created the Xcode Project**   
```c 
platform :ios, '12.0'

use_frameworks!

def fellow_blogger_pods
  pod 'Firebase/Core'
  pod 'Firebase/Auth'
  pod 'Firebase/Firestore'
  pod 'Firebase/Storage'
  pod 'Kingfisher'
  pod 'Toucan'
end

target 'FellowBloggerV2' do
  fellow_blogger_pods
end
```

## Instruction Staff Github Accounts <a name="instruction-staff-accounts"></a>

**Instructors**   
Alan Holguin [Github](https://github.com/lynksdomain) - lynksdomain   
Alex Paul [Github](https://github.com/alexpaul) - alexpaul    

**TAs**   
Iram Fattah [Github](https://github.com/Ifattah94) - Ifattah94    

## Project Specifications <a name="project-specifications"></a>

1. The app requires the user to login or create a new account in order to blog or view blogs.
1. The app's main view consists of a tab bar controller with three tabs. A blog feed tab, a search tab and a profile tab.
1. The blog feed tab shows all bloggers posts.
1. A blog post includes: the blogger's photo, the blog description and a blog photo. 
1. All cells in this app will be required to be a custom cell. You are free to use storyboard, programmatic ui or a .xib file to create your custom cell.
1. The search tab allows a user to search for a fellow blogger by display name (username). 
1. The profile tab includes: the current user's photo, the user's created blog posts, their first and last name, display name, a sign out button, an edit button, their bio and a cover photo. All the user's profile properties are editable.

See the screenshots below for more per screen detail.

## Resources <a name="resources"></a>

- [RaceReviews](https://github.com/joinpursuit/Pursuit-Core-iOS-RaceReviews)
- [NationalDish](https://github.com/alexpaul/NationalDish)
- [Firebase Authentication](https://firebase.google.com/docs/auth/?authuser=1) 
- [Firestore](https://firebase.google.com/docs/firestore/?authuser=1)
- [Firebase Storage](https://firebase.google.com/docs/storage/?authuser=1)

## Collections and Client (iOS App) Model Properties <a name="mvp-collections"></a>

**bloggers collection on firebase, User Model (Swift)**  
- displayName (keep this name consistent with the authenticated user's display name) 
- bloggerId (hint: this should be the same id as the user's id who created the blog)
- email 
- photoURL 
- coverImageURL 
- joinedDate
- firstName 
- lastName 
- bio 

**blogs collection on firebase, Blog Model (Swift)**    
- createdDate
- bloggerId 
- imageURL
- blogDescription
- documentId (hint: first create the documentId when creating a blog and save it as this field)

## FellowBloggerV2 MVP Checklist Requirements <a name="mvp-requirements"></a>

- [ ] user can create an account 
- [ ] user can sign in to an existing account
- [ ] user can sign out of their account
- [ ] user can view all blogs in the blog feed controller (sorted by most recent date, more here for [date helpers](https://github.com/alexpaul/SwiftyHelpers))
- [ ] user can view all their created blogs in the profile view controller (sorted by most recent date)
- [ ] user can edit their profile, edits include: profile photo, cover photo, first name, last name, username and bio 
- [ ] user can create a blog post: post includes adding a photo from camera or photo library 
- [ ] user can edit their blog post 
- [ ] user can delete a blog post
- [ ] selecting a blog post shows a detail view of the blog 
- [ ] user can see more options via an action sheet to carry out the appropriate action e.g delete, edit, save image
- [ ] user can search for other bloggers in the search tab 
- [ ] selecting a blogger from the search takes the user to the blogger's profile page
- [ ] user can view all blogs of a fellow blogger after selecting their profile

## Saving Images to Storage <a name="saving-images"></a>

There will be three key places images are being posted to Firebase Storage: 
1. Profile Image 
1. Cover Image 
1. Blog Image 

The default storage bucket location is **images**   

Pass in the following iamge paths when calling StorageService.postImage

```swift 
postImage(imageData: Data, imageName: String, completion: @escaping (Error?, URL?) -> Void)
```

Here are the imageName paths: 
1. For Profile Image: 
```swift 
imageName: "profileImages/\(user.uid)"
```
2. For Cover Image: 
```swift 
imageName: "coverImages/\(user.uid)"
```
3. For a Blog Image: 
```swift 
imageName: "blogs/\(user.uid)/\(documentId)"
```

**Reminder**: Use Toucan or similar resizing function to resize all images prior to posting to Firebase. 

```swift 
let resizeImage = Toucan(image: image).resize(CGSize(width: 500, height: 500))
```


## Extra Credit Checklist <a name="extra-credit-checklist"></a>

- [ ] user can like a blog and view in a likes view
- [ ] user can share a blog 
- [ ] user can comment on a blog (see database schema for document fields)  
- [ ] user can view comments of a blog
- [ ] user can block a fellow blogger (blogger will no longer appear in blog feed)
- [ ] user can view a bloggers github and social media page (links will be available on the blogger's profile page)

## Dependencies 

1. [Firebase](https://firebase.google.com/docs/ios/setup) (Authentication, Database, Storage)
1. [Kingfisher](https://github.com/onevcat/Kingfisher) (Downloading and Caching Images) 
1. [Toucan](https://github.com/gavinbunney/Toucan) (Image Resizing)

## Bloggers Collection Database Schema 

- a bloggers collection document fields are: 
- bio
- bloggerId
- coverImageURL
- displayName
- email
- firstName
- lastName
- joinedDate
- photoURL 

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/bloggers-collection.png" width="900" height="600" />
</p>

## Blogs Collection Database Schema 

- the blogs collection document fields are: 
- blogDescription
- bloggerId
- createdDate
- documentId
- imageURL 

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/blogs-collection.png" width="900" height="600" />
</p>

# Screens

## Gif 

![fellow blogger app](https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/fellow-blogger-app.gif)

## Account Login Views 

**Create Account View**  

- username **required**  
- email **required**  
- password **required**  

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Account%20Login/create-account-view.png" width="250" height="541" />
</p>

**Login View**  

- email **required**  
- password **required**  

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Account%20Login/login-view.png" width="250" height="541" />
</p>


## Blog Feed Tab  

**Blog Feed View**  

- create a custom blog cell (you are free to use storyboard, programmatic or a .xib file)
- custom blog cell includes: blogger's photo, the blog description and a blog photo
- add bar button item segues to an add blog view (there the user is able to create a blog post) 

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Blog%20Feed%20Tab/blog-feed-view.png" width="250" height="541" />
</p>

**Add Blog**  

- description **required**
- image **required**
- camera button is enabled if device is available otherwise it should be disabled
- photo library button
- post button
- cancel button 

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Blog%20Feed%20Tab/add-blog-view.png" width="250" height="541" />
</p>

**Blog Detail View**  

- more info button (actions include, save image, edit blog, delete blog, cancel)
- edit and delete should only be available if blog was created by current user 
- a photo of the blogger who created the post
- a blog photo
- a blog description
- make sure you account for a longer description by using a scroll view

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Blog%20Feed%20Tab/blog-detail-view.png" width="250" height="541" />
</p>

**Blog Detail Actions**  

- more info button (actions include, save image (save to the simulator or device's photo library), edit blog, delete blog, cancel)    
- the blog description the only required blog edit

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Blog%20Feed%20Tab/blog-detail-actions.png" width="250" height="541" />
</p>

**Edit Blog Post**   

- requirement is to edit the blog description 

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Blog%20Feed%20Tab/edit-blog-post.png" width="250" height="541" />
</p>


**Blog Detail Confirm Delete**  
<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Blog%20Feed%20Tab/blog-detail-confirm-delete.png" width="250" height="541" />
</p>

## Search Tab 

**Search View**  

- search autocompletes as user is typing
- when a blogger is selected from the search, the user is taken to that blogger's profile page

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Search%20Tab/search-view.png" width="250" height="541" />
</p>


## Profile Tab

**Profile View**  

- cover photo 
- profile photo
- full name (first and last name)
- edit button which segues to an edit profile view 
- bio
- all blogs created by the user

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Profile%20Tab/profile-view.png" width="250" height="541" />
</p>

**Edit Profile View**  

- cover photo, profile photo, first name, last name, username and bio are all editable

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Profile%20Tab/edit-profile-view.png" width="250" height="541" />
</p>

**Edit Profile Photo**  
<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Profile%20Tab/edit-profile-photo.png" width="250" height="541" />
</p>

**Edit Bio View**  

- selecting the bio cell segues to an edit bio view

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Profile%20Tab/edit-bio-view.png" width="250" height="541" />
</p>

# Rubric

## MVP Rubric <a name="mvp-rubric"></a>

| Criteria | Points |
|:------:|:-----:|
| adhering to MVC and object oriented principles | 4 |
| adhering to Swift principles | 4 |
| app builds without errors | 4 |
| error states are handled and shown to the user as appropriate instead of print statments | 4 |
| final submission does not have commented out unused code | 4 |
| user can create an account | 4 |
| user can sign in to existing account | 4 |
| user can sign out of account | 4 |
| user can view all blogs in the blog feed controller (sort by most recent date) | 4 |
| user can view all their created blogs in the profile view controller (sort by most recent date) | 4 |
| user can edit their profile, edits include: profile photo, cover photo, first name, last name, username and bio | 4 |
| user can create a blog post: post includes adding a photo from camera or photo library | 4 |
| user can edit their blog post | 4 | 
| user can delete a blog post | 4 | 
| selecting a blog post shows a detail view of the blog | 4 |
| user can see more options via an action sheet to carry out the appropriate action e.g delete, edit, save image | 4|
| user can search for other bloggers in the search tab | 4 |
| selecting a blogger from the search takes the user to the blogger's profile page | 4 |
| user can view all blogs of a fellow blogger after selecting their profile | 4 |

Total 76 Points 

## Extra Credit Rubric <a name="extra-credit-rubric"></a>

| Criteria | Points |
|:------:|:-----:|
| user can like a blog and view in a likes view | 6 |
| user can share a blog | 4 |
| user can comment on a blog and view comments | 6 |
| user can block a fellow blogger (blogger will no longer appear in blog feed) | 6 |
| user can view a bloggers github and social media page (links will be available on the blogger's profile page) | 6 |

Extra Credit 28 Points

## Comments Collection Database Schema <a name="extra-credit-collections"></a>

**Comments Collection**  

- here a blog document has a comments collection (see comments collection details below)

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Extra%20Credit/comments-collection.png" width="900" height="500" />
</p>

**Comments Collection Details**  

- at minimum a comments document fields are: 
- blogId
- commentId
- commentText
- commentedBy
- createdDate 

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Extra%20Credit/comments-collection-details.png" width="900" height="500" />
</p>


## Likes Collection Database Schema 

- likes collection document fields at minimum are: 
- blogId
- createdDate
- likeId
- likedBy

<p align="center">
  <img src="https://github.com/joinpursuit/Pursuit-Core-iOS-Unit6-CTA-FellowBloggerV2/blob/master/Images/Extra%20Credit/likes-collection.png" width="900" height="300" />
</p>
