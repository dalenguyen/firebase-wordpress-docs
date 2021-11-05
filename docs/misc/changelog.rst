CHANGELOG
=============

All notable changes to this project will be documented in this file.

## v2.14.1 (2021-11-05)
----------------------------------

#### - :bug: [Bug Fix]

- `PRO - v2.19.1`
   -  show default WooCommerce login when Firebase Auth is disabled

## v2.14.0 (2021-10-31)
----------------------------------

#### - :nail_care: [Polish]

- `PRO - v2.19.0`
   - Check for null value before saving to firebase
   - Deprecate user register API

- `FUNCTIONS - v1.3.0`
   - Update packages


## v2.13.0 (2021-09-26)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.18.0`
  - Allow extending post object when saving to firebase

## v2.12.0 (2021-09-19)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.17.0`
  - Allow extending user object when saving to firebase

- `WOO - v2.5.0`
  - Add filter hooks for subscriptions

## v2.11.0 (2021-08-30)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.16.0`
   - Added id key when saving data to firebase
   - Check for users configuration before saving to firebase


## v2.10.0 (2021-08-26)
----------------------------------

#### - :rocket: [New Feature]

- `FUNCTIONS - v1.2.0`
   - Used user_login for uid when importing users


#### - :rocket: [New Feature]

- `USERS - v1.2.0`
   - Support for import more than 10,000 users

## v2.9.0 (2021-08-08)
----------------------------------

#### - :rocket: [New Feature]

- `WOO - v2.3.0`
  - Use onWrite trigger for syncing products
  - Use onWrite trigger for syncing categories
  - Delete images when delete product

## v2.8.0 (2021-08-02)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.15.0`
   - added custom registration form (Contact 7)
   - added confirmation email check to Login form

## v2.7.0 (2021-07-12)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.14.0`
   - Improved send email verification flow for firebaseUI Web

#### - :nail_care: [Polish]

- `PRO - v2.14.0`
   - Updated firebase version to v8.7.1

## v2.6.0 (2021-06-20)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.13.0`
   - Added get data from firebase filter hooks

- `WOO - v2.2.0`

   - Sync Subscription to Firebase

## v2.5.0 (2021-05-29)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.12.0`
   - Added support for not default Realtime Database URL
   - Updated styles for error components

- `FUNCTIONS - v1.1.0`

   - Added support for secondary Realtime database


## v2.4.0 (2021-05-22)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.11.0`
  - Deleted category on firebase when deleting in WordPress
  - Enabled Microsoft login

- `WOO - v2.1.0`
   - Changed product update hook when saving product to firebase

#### - :nail_care: [Polish]

- `PRO - v2.11.0`
  - Removed product key warning

## v2.3.0 (2021-05-16)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.10.0`
   - supported syncing category to firebase
   - updated firebase version to 8.6.1

## v2.2.0 (2021-05-01)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.9.0`

   - Added product key settings for auto-update

## v2.1.0 (2021-04-24)
----------------------------------

#### - :rocket: [New Feature]

- `FUNCTIONS - v1.0.0`
   - Updated import users from WordPress logic
   - Used randomized string for UID when importing users

- `USERS - v1.1.0`
  - Updated get users function

- `WOO - v2.0.0`
   - Added flags to disable delete / sync to firebase
   - Added cloud functions for syncing (CRUD) products & categories from Firebase to WordPress
   - Product data structure will be synced based on WooCommerce API
   - Delete product on WordPress will also delete product on Firebase

## v2.0.0 (2021-04-11)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.8.0`
   - Hided single sign-on after log in
   - Exposed custom text for Sign out button

- `WOO - v2.0.0`
   - Added flags to disable sync to firebase
   - Added cloud functions for syncing products & categories from Firebase to WordPress

#### - :nail_care: [Polish]

- `PRO - v2.8.0`
   - Removed warning for not supported post types

## v1.21.0 (2021-04-02)
----------------------------------

#### - :nail_care: [Polish]

- `PRO - v2.7.2`
   - Change base domain name on the Settings tab

- `FUNCTIONS - v0.20.0`
   - Refactored firebase functions service
   - Updated packages

## v1.20.0 (2021-03-27)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.7.0`
   - Added support for multi-files uploader to cloud storage

#### :bug: [Bug Fix]

- `PRO - v2.7.0`
   - Fixed sendEmailVerification error (firebaseUI Web)

## v1.19.0 (2021-03-21)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.6.0`
   - Enabled email verification for FirebaseUI Web

- `WOO - v1.9.0`
   - Added support for syncing Membership to Firebase

#### - :nail_care: [Polish]

- `PRO - v2.6.0`
   - Improve login check

## v1.18.0 (2021-03-14)
----------------------------------

#### - :rocket: [New Feature]

- `WOO - v1.7.0 + v1.8.0`
   - Added firebase login to My Account page
   - Added line items when syncing to firebase
   - Synced order by editing order

## v1.17.0 (2021-03-06)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.5.0`
   - Added support for jwt token login
   - Added updatedAt when updating data to Firebase

#### :bug: [Bug Fix]

- `PRO - v2.5.0`
   - Fixed createdAt when updating data to Firebase

## v1.16.0 (2021-02-20)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.4.0`
   - Added delete database hooks
   - Removed delete post to firebase database

- `FUNCTIONS - v0.19.0`
   - Added delete document endpoint

#### - :nail_care: [Polish]

- `PRO - v2.4.0`
   - Increased security check in time for autologin
   - Improved login logic handler
   - Updated firebase scripts version

## v1.15.0 (2021-01-30)
----------------------------------

#### - :rocket: [New Feature]

- `WOO - v1.6.0`
   - Added attributes when syncing products

## v1.14.1 (2021-01-24)
----------------------------------

#### - :nail_care: [Polish]

- `PRO - v2.3.1`
   - Only run security check when cloud functions are deployed

## v1.14.0 (2021-01-23)
----------------------------------

#### - :boom: [Breaking Change]

- `PRO - v2.3.0`
   - Improved autologin security to WordPress (need cloud functions v.0.18.0)

#### - :rocket: [New Feature]

- `PRO - v2.3.0`
   - Allowed getting full URL when uploading a file to Firebase Storage

- `FUNCTIONS - v0.18.0`
   - Added getUser endpoint (with fields params)

#### - :bug: [Bug Fix]

- `WOO - v1.5.0`
   - Fixed typo when syncing Order to Firebase

## v1.13.0 (2021-01-17)
----------------------------------

#### - :rocket: [New Feature]

- `WOO - v1.4.0`
   - Added createdAt & updatedAt when syncing order
   - Added phone number to billing when syncing order

#### - :nail_care: [Polish]

- `FUNCTIONS - v0.17.0`
   - Update packages

- `PRO - v2.1.0`
   - Improved Login / Logout Styling

## v1.12.0 (2021-01-09)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.1.0`
   - Added support for display data type Boolean & Number
   - Added id to the display fields (firestore)
   - Deprecated formAction when saving / updating data
   - Data will be upsert to firebase

#### - :nail_care: [Polish]

- `PRO - v2.1.0`
   - Hide logout link when login with Firebase is disabled
   - Improved error mesages & security

## v1.11.0 (2021-01-03)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v2.0.0`
   - Updated synced user function when logging to WordPress is disabled
   - Added createdAt field when saving data to firebase
   - Added integer type when saving data to firebase
   - Hided login & register page when login with WordPress is enabled

#### - :nail_care: [Polish]

- `PRO - v2.0.0`
   - Updated firebase script to v8.2.1

## v1.10.0 (2020-12-19)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.26.0`
   - Improved logged in session between WordPress & Firebase

## v1.9.0 (2020-12-13)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.25.0`
   - Added custom redirect to firebaseui web

- `WOO - v1.2.0`
   - Added currency to synced order to firebase
   - Enabled synced product to firebase

## v1.8.0 (2020-12-05)
----------------------------------

#### - :rocket: [New Feature]

- `WOO - v1.1.0`
   - Sync order to firebase

## v1.7.0 (2020-11-28)
----------------------------------

#### - :nail_care: [Polish]

- `PRO - v1.24.0`
   - Used update rather than create for syncing data to firebase

## v1.6.0 (2020-11-21)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.23.0`
   - Converted timestamp to date format (firestore)
   - Improved security for auto login

#### - :nail_care: [Polish]

- `FUNCTIONS - v0.16.0`
  - Updated packages
  - Required node 12 for cloud functions

## v1.5.0 (2020-11-14)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.22.0`
   - Allowed getting firestore value from a deep level object key

#### - :nail_care: [Polish]

- `PRO - v1.22.0`
  - Updated firebase scripts to v8.0.2
  - Updated firebaseui web scripts to v4.7.1

## v1.4.0 (2020-11-08)
----------------------------------

#### - :rocket: [New Feature]

- `PRO - v1.21.0`
   - Added Filter Hook to Import Users to Firebase
   - Added createdAt & SignedOn to the exported users in WP dashboard

- `USERS - v1.0.0`
   - Added import WP users to Firebase

- `FUNCTIONS - v0.15.0`
   - Added import users endpoint
   - Allowed to signout with frontend token

## v1.3.0 (2020-11-01)
----------------------------------

#### :nail_care: [Polish]

- `PRO - v1.20.0`
    - Updated firebase scripts to v8.0.0

#### - :bug: [Bug Fix]

- `PRO - v1.20.0`
    - Check for firebase functions before syncing WordPress users

## [v1.2.0] - (2020-10-18)
----------------------------------

#### :nail_care: [Polish]

- `PRO - v1.19.0`
    - Updated firebaseUI Web to 4.7.0

#### - :bug: [Bug Fix]

- `PRO - v1.19.0`
    - Fixed Beaver Builder conflict

## [v1.1.0] - (2020-10-12)
----------------------------------

#### :rocket: [New Feature]

- `PRO - v1.18.0`
    - Added Filter Hook to Save Data to Firebase

## [v1.0.0] - (2020-10-11)
----------------------------------

#### :rocket: [New Feature]

- `PRO - v1.17.0`
    - Added loading state after logging in

## [ 1.16.0 ] - 27-09-2020
----------------------------------

#### - :rocket: [New Feature]

- Use phone number as display name for phone authentication
- Added User to Firestore (No WordPress User flow)

#### - :nail_care: [Polish]

- Updated check version condition

## [ 1.15.0 ] - 20-09-2020
----------------------------------

#### - :rocket: [New Feature]

- Added not-in & not equal (!=) to filter Firestore
- Added limit when getting Firestore data
- Added dynamic link when displaying firestore data

#### - :nail_care: [Polish]

- Updated firebase scripts to 7.21.0

## [ 1.14.0 ] - 30-08-2020
----------------------------------

#### - :rocket: [New Feature]

- Updated display name if it exists in Firebase
- Ability to sync Users to Firestore / Realtime Database

**Notice:** You have to deploy cloud functions (v0.14.0) in order to sync user data

## [ 1.13.0 ] - 22-08-2020
----------------------------------

#### - :rocket: [New Feature]

- Added Created On and Signed In to the Users table
- Added UPDATE option for Contact Form 7 (Firestore)

#### - :nail_care: [Polish]

- Added check for new version in WordPress dashboard
- Added guide URL under Auth tab

## [ 1.12.0 ] - 13-08-2020
----------------------------------

#### - :bug: [Bug Fix]

- Fixed Firebase Account doesn't save
- Fixed "missing the required permission_callback argument" (WordPress 5.5)
- Fixed user cannot register to WordPress using [firebase_login] shortcode

## [ 1.11.0 ] - 03-08-2020
----------------------------------

#### - :rocket: [New Feature]

- Added redirect after logging out
- Added send confirmation email in [firebase_register] shortcode

#### - :nail_care: [Polish]

- Reorganized scripts for W3 Cache performance

## [ 1.10.0 ] - 01-08-2020
----------------------------------

#### - :rocket: [New Feature]

- Added authentication support for multisite

#### - :nail_care: [Polish]

- Updated firebaseui web to v4.6.1
- Improved performance by putting scripts in body

## [ 1.9.0 ] - 25-07-2020
----------------------------------

#### - :rocket: [New Feature]

- Added Firebase Analytics script
- Added author info when syncing post data to Firebase
- Updated firebase scripts to v7.17.1

## [ 1.8.0 ] - 20-07-2020
----------------------------------

#### - :rocket: [New Feature]

- Added support for file upload (Contact 7 Form)

#### - :bug: [Bug Fix]

- Fixed error when initialize Storage Bucket

## [ 1.7.0 ] - 19-07-2020
----------------------------------

#### - :rocket: [New Feature]

- Added support for Storage bucket
- Support WooCommerce Authentication

## [ 1.6.0 ] - 12-07-2020
----------------------------------

#### - :rocket: [New Feature]

- Added support for custom fields when syncing post types
- Supported orderby when displaying firestore data
- Supported orderby when displaying realtime data (orderByChild)

#### - :nail_care: [Polish]

- Updated FirebaseUI Web version to v4.5.2
- Updated development packages

## [ 1.5.0 ] - 05-07-2020
----------------------------------

**If your Contact7 is >= v.5.2, please use update this plugin to the latest version (>= v1.5.0).**

#### - :rocket: [New Feature]

- Support newline when display from textarea
- Collection name is generated from post_type plural label

#### - :bug: [Bug Fix]

- Fixed sending error in Contact Form 7 v5.2

## [ 1.4.0 ] - 28-06-2020
----------------------------------

#### - :bug: [Bug Fix]

- Edited the broken docs link

#### - :rocket: [New Feature]

- Allow phone user to login to WordPress
- Improved security for logging to WordPress
- WordPress username is default to Firebase UID

## [ 1.3.1 ] - 21-06-2020
----------------------------------

#### - :bug: [Bug Fix]

- Fixed PHP Notices


## [ 1.3.0 ] - 21-06-2020
----------------------------------

#### - :rocket: [New Feature]

- Added one-tap signup feature (Google)
- Added popup for social login
- Allowed login via email link

## [ 1.2.0 ] - 15-06-2020
----------------------------------

#### - :rocket: [New Feature]

- Added dynamic User UID when searching for Firestore data
- Added custom post types support when syncing data to Firebase
- Added taxonomies when saving data to Firebase

## [ 1.1.0 ] - 06-06-2020
----------------------------------

#### - :boom: [Breaking Change]

- Optimized scripts loaded for Firestore / Realtime

#### - :bug: [Bug Fix]

- Sanitized string before displaying on the frontend

#### - :rocket: [New Feature]

- Retrieved data dynamically with firebase uid as document id
- Added search shortcode for Firestore
- Added options to deploy cloud functions to different regions

#### - :nail_care: [Polish]

- Updated FirebaseUI Web version to v4.5.1
- Updated Firebase scripts to v7.15.0

## [ 1.0.0 ] - 30-05-2020
----------------------------------

- Autofill firebase UID to input form
- Added account management shortcode
- Added phone number authentication
- Added language support for FirebaseUI Web
- Localization the plugin

## [ 0.20.0 ] - 24-05-2020
----------------------------------

- Added wp logout link to Logout button
- Allowed to change log in text button
- Added reset password link to login form
- Display fields must be filled for display items for realtime/firstore
- Allowed multi realtime/firestore shortcodes on one page
- Dynamic show firestore/realtime data through query params

## [ 0.19.0 ] - 17-05-2020
----------------------------------

- Separated registration & Login form
- Allow login to WordPress through social media platforms
- Added images support for Realtime / Firestore Document
- Fixed access array offset notice error

## [ 0.18.0 ] - 09-05-2020
----------------------------------

- Showed deep level object when searching for database
- Added ability to download Users table
- Redirect to defined page after login
- Enable login through apple
- Added map type when saving data to firebase
- Added display types for realtime / firestore document
- Displayed data from firestore / realtime as blocks

## [ 0.17.0 ] - 27-04-2020
----------------------------------

- Applied security rules when saving data to firebase
- Only sync public post to firebase

## [ 0.16.0 ] - 26-04-2020
----------------------------------

- Added BuddyPress extension

## [ 0.15.0 ] - 18-04-2020
----------------------------------

- Added Maps extension

## [ 0.14.0 ] - 12-04-2020
----------------------------------

- Removed custom claims when empty
- Added shortcodes for displaying realtime & firestore collection

## [ 0.13.0 ] - 11-04-2020
----------------------------------

- Added table structure for Users tab
- Make email uneditable for search purpose
- Functions (0.11.0): increased get users limit (> 1000 users)

## [ 0.12.0 ] - 08-04-2020
----------------------------------

- Added filter feature for Users #29

## [ 0.11.1 ] - 07-04-2020
----------------------------------

- Showed warning if base domain is not set
- Check for undefined in order to pass error check
- Updated options for plugin deletion

## [ 0.11.0 ] - 02-04-2020
----------------------------------

- Used wait for element rather than setTimeOut
- Added logout event to all logout links
- Added post thumbnail and author name to Firebase Sync
- Updated Firebase script from 7.9.3 to 7.13.1

## [ 0.10.0 ] - 01-04-2020
----------------------------------

- Added date type for saving data to Firebase
- Increase time wait for error in form submit to Firebase

Dependency: cloud functions: v0.9.0

## [ 0.9.1 ] - 29-03-2020
----------------------------------

- Fixed ArrayType when saving data to Realtime/Firestore
- Fixed WP post type is null when sync data to Firebase
- Removed notice warning for post types

Dependency: cloud functions: v0.8.0

## [ 0.9.0 ] - 28-03-2020
----------------------------------

- Fixed save data to realtime / firestore token error
- Added document id option when saving data
- Added trigger for syncing post and page to Firebase

Dependency: cloud functions: v0.8.0

## [ 0.8.0 ] - 24-03-2020
----------------------------------

- Logout of everything when clicking signout buttons
- Added warning before deleting a Firebase user
- Added user role (Customer) for WooCommerce sites
- Prevent user to change password when login through firebase is active
- User password will be dominated by Firebase procedure

Dependency: cloud functions: v0.7.0

## [ 0.7.0 ] - 13-03-2020
----------------------------------

- Styled add new user button
- Created and log in Firebase Users to WordPress
- Redirect login page feature
- Added Rest API for creating new Users (Subscriber)
- Updated FirebaseUI Web to 4.5.0
- Bring Firebase Menu to the front
- Prevent normal user to see dashboard token when they log in
- Updated about page
- Show realtime & firestore data based on security rules

## [ 0.6.0 ] - 01-03-2020
----------------------------------

- Update firebase scripts from 7.8.2 to 7.9.3
- Added send cloud message to a topic feature

## [ 0.5.8 ] - 20-02-2020
----------------------------------

- Breaking change for getting database: you need to update wordpress firebase functions to 0.5.8.
- Added create data for Realtime database & firestore with Contact Form 7
- Added warning for missing [firebaseui_web] globally
- Moved environment variables to one source

## [ 0.5.7 ] - 16-02-2020
----------------------------------

- Updated firebase scripts to v7.8.2
- Hide greetings when signing out

## [ 0.5.6 ] - 21-12-2019
----------------------------------
 
- Display data with claims

## [ 0.5.5 ] - 21-12-2019
----------------------------------

- Breaking changes
- Deprecated authention process and replaced with firebasui-web

## [ 0.5.4 ] - 01-12-2019
----------------------------------

- Updated packages
- Moved error and message to the top of dashboard
- Add CRUD to manage Firebase User from Dashboard

## [ 0.5.3 ] - 22-09-2019
----------------------------------

- Added user register form to frontend #4
- Show firestore database after login #10
- Added delete user from dashboard #11
- Search document from firestore or realtime
- Update firebase version

## [ 0.5.2 ] - 30-03-2019
----------------------------------

- Show realtime database after login

## [ 0.5.1 ] - 11-08-2018
----------------------------------

- Hide login form after logging in

## [ 0.5.0 ] - 04-08-2018
----------------------------------

- Add shortcode to display when not login
- Add error handling shortcode

## [ 0.4.0 ] - 17-07-2018
----------------------------------

- Added Firestore database support in Dashboard

## [ 0.3.2 ] - 17-07-2018
----------------------------------

- Fixed firebase-show shortcode

## [ 0.3.1 ] - 17-07-2018
----------------------------------

- Fixed getting credentials

## [ 0.3.0 ] - 02-07-2018
----------------------------------

- Added about information
- Added Real Time database support in Dashboard

## [ 0.2.0 ] - 25-5-2018
----------------------------------

- Added firebase scripts and styles to header
- Implement login and logout features

## [ 0.1.0 ] - 20-4-2018
----------------------------------

- Started the project and add an authentication method