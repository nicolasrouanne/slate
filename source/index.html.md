---
title: ADaM Application Data Manager

language_tabs:
  - curl

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# ADaM

# Authentication

## Login

<p>Session authentication (w/ cookie)</p>

  POST /auth/local


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| identifier      | String      |  <p>User name</p>             |
| password      | String      |  <p>User password</p>             |


# Ads

## Get ad

  `GET /ads/:id`

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Ad unique ID.</p>             |


## List ads

<p>List all ads the user has read permission on</p>

  GET /ads

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

# Apps

## Get app



  GET /apps/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>App unique ID.</p>              |

## List apps

<p>Get list of apps</p>

  GET /apps



# Leads

## Get lead



  GET /leads/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Lead unique ID.</p>             |

## List leads



  GET /leads?from=:from&amp;appId=:appId

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| from      | DateTime      | **optional** <p>Date used to filter leads</p>             |
| appId     | String      | **optional** <p>ID of app to fetch leads from</p>             |

# Media

## List media

<p>Get list of media</p>

  GET /media

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get medium



  GET /media/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Medium unique ID.</p>             |

# Notifications

## Acknowledge reception of a notification

<p>This service should posted to to acknowledge reception of (or click on) a notification.</p>

  POST /notifications/acknowledgment

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| notificationId      | String      |  <p>The unique ID of the notification</p>             |
| appInstallationId     | String      |  <p>The unique ID of the appinstallation</p>              |

## Register or update the app installation

<p>This service should be used by apps to register in ADaM. It is also responsible for receiving the app's registration to push notifications</p>

  POST /appinstallations

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| deviceUUID      | String      |  <p>A unique ID generated at app installation. Unique across re-installations on Android, not on iOS.</p>             |
| deviceOS      | String      |  <p>An identification of the OS</p>             |
| deviceOSVersion     | String      |  <p>The OS version</p>              |
| appVersion      | String      |  <p>The app version</p>             |
| deviceNotificationToken     | String      | **optional** <p>The notification token provided by APNS or GCM</p>              |

# Posts

## Get catalogue apps

<p>Get catalogue app by ID</p>

  GET /catalogapps/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>CatalogApp ID</p>             |

## List catalogue apps

<p>Get list of catalogue app posts</p>

  GET /catalogapps

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## List categories

<p>Get list of categories</p>

  GET /categories

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

### Success Response

Success-Response:

```
HTTP/1.1 200 OK

[
  {
    "appId": "55eef4f8deeafc364ce11718",
    "createdBy": "55eef4f7deeafc364ce116c7",
    "owner": "55eef4f7deeafc364ce116c7",
    "name": "Submenu 1",
    "categories": [
      {
        "id": "55eef4f9deeafc364ce1173a",
        "type": "category",
        "mainParent": true // This is useful to get the full path of an item (e.g breadcrums, tagging...) that has multiple parents. The "mainParent" should be used if it exists.
      },
      {
        "id": "d5eef4f9deeafc364ce1178f",
        "type": "category"
      }
    ],
    "children": [],
    "createdAt": "2015-09-08T14:47:21.911Z",
    "updatedAt": "2015-09-08T14:47:21.911Z",
    "id": "55eef4f9deeafc364ce1173b"
  },
  {
    "appId": "55eef4f8deeafc364ce11718",
    "createdBy": "55eef4f7deeafc364ce116c7",
    "owner": "55eef4f7deeafc364ce116c7",
    "name": "Submenu 2",
    "categories": [
      {
        "id": "55eef4f9deeafc364ce1173a",
        "type": "category"
      }
    ],
    "children": [],
    "createdAt": "2015-09-08T14:47:22.010Z",
    "updatedAt": "2015-09-08T14:47:22.010Z",
    "id": "55eef4fadeeafc364ce1173c"
  },
  {
    "appId": "55eef4f8deeafc364ce11718",
    "createdBy": "55eef4f7deeafc364ce116c7",
    "owner": "55eef4f7deeafc364ce116c7",
    "name": "Menu",
    "categories": [],
    "children": [
      {
        "id": "55eef4f9deeafc364ce1173b",
        "type": "category"
      },
      {
        "id": "55eef4fadeeafc364ce1173c",
        "type": "category"
      }
    ],
    "createdAt": "2015-09-08T14:47:21.821Z",
    "updatedAt": "2015-09-08T14:47:22.332Z",
    "id": "55eef4f9deeafc364ce1173a"
  }
]
```
## Get category

<p>Get category by ID</p>

  GET /categories/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Category ID</p>             |

## Get event

<p>Get event by ID</p>

  GET /events/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Event ID</p>              |

## List events

<p>Get list of events</p>

  GET /events

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get form

<p>Get form by ID</p>

  GET /forms/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Form ID</p>             |

## List forms

<p>Get list of forms</p>

  GET /forms

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get job

<p>Get job by ID</p>

  GET /jobs/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Job ID</p>              |

## List jobs

<p>Get list of jobs</p>

  GET /jobs

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get post

<p>Get post by ID</p>

  GET /posts/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Post ID</p>             |

## List posts

<p>Get list of posts</p>

  GET /posts

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get quiz

<p>Get quiz by ID</p>

  GET /quizzes/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Quiz ID</p>             |

## List quizzes

<p>Get list of quizzes</p>

  GET /quizzes

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get sponsorinfos

<p>Get sponsor infos by ID</p>

  GET /sponsorinfos/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>SponsorInfo ID</p>              |

## List sponsorinfos

<p>Get list of sponsor infos posts</p>

  GET /sponsorinfos

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

## Get tag

<p>Get tag by ID</p>

  GET /tags/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Tag ID</p>              |

## List tags

<p>Get list of tags</p>

  GET /tags


## Submit form

<p>Submit a form to create leads. Designed after the /leads endpoint. appId will be set automatically thanks to the authentication token.</p>

  POST /forms/submit

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| appinstallationId     | String      | **optional** <p>(Highly recommended for tracking) The app installation's id received from the post to appinstallations (<a href="#api-Notifications-RegisterAppInstallation">see registration</a>)</p>              |
| sponsors      | Object[]      | **optional** <p>Array of sponsors' information to create leads.<br /><b>If this is empty, a &quot;registration&quot; lead is created.</b> If not, leads will be created for each sponsor in the array, with the <code>sponsor</code> or <code>opt-in</code> type.<br />An object should be added to this array if the form's <code>sponsorId</code> field is defined. <br />An object should be added to this array if the form contains a field with <code>sponsor_optin</code> <code>type</code> field <b>and the user checked it</b>.</p>              |
| sponsors.sponsorId      | String      |  <p>The sponsor's ID</p>              |
| sponsors.optIn      | Boolean     |  <p>Opt-in param<br /><b>If this is set to <code>true</code> the created lead will have the <code>opt-in</code> type. If not it will have the <code>sponsor</code> type.</b></p>              |
| sponsors.optInOptions     | Array     | **optional** <p>Array of arbitrary options like [&quot;Paris&quot;]...</p>              |
| adId      | String      | **optional** <p>The id of the ad the user clicked to navigate to the</p>              |
| email     | String      | **optional** <p>Validated email address</p>             |
| firstName     | String      | **optional** <p>User's first name</p>             |
| lastName      | String      | **optional** <p>User's family name</p>              |
| phone     | String      | **optional** <p>User's international phone number (e.g +33612345678 for france)</p>             |
| address     | String      | **optional** <p>User's street address (row 1)</p>             |
| address_2     | String      | **optional** <p>User's street address (row 2)</p>             |
| state     | String      | **optional** <p>User's address state / province / regions / departement</p>             |
| zip     | String      | **optional** <p>User's address postal/zip code</p>              |
| country     | String      | **optional** <p>User's address country ISO code (2 chars)</p>             |
| birthdate     | Date      | **optional** <p>User's date of birth</p>              |
| nationality     | String      | **optional** <p>User's nationality</p>              |
| levelOfEducation      | String      | **optional** <p>User's level of education (text)</p>              |
| levelOfEducationAbsolute      | Integer     | **optional** <p>User's absolute level of education (integer)</p>              |
| major     | String      | **optional** <p>User's major</p>              |
| branch      | String      | **optional** <p>User's branch</p>             |
| gender      | String      | **optional** <p>User's gender</p>             |
| rawData     | Object      | **optional** <p>Raw form data (JSON) with field definitions and userValue keys.</p>             |

# Questions

## Get question

<p>Get question by ID</p>

  GET /questions/:id

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| id      | String      |  <p>Question ID</p>             |

## List questions

<p>Get list of quiz questions</p>

  GET /questions

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization     | String      |  <p>Basic + authorization token<br />e.g. 'Basic fqQfg7a6dg5A='</p>             |
| X-Json-MD5      | String      |  <p>Last MD5 hash of the feed. If the feed hasn't changed, the response status will be 304.</p>             |

# Sponsors

## Get sponsor

<p>List all sponsors</p>

  GET /sponsors/:id


## List sponsors



  GET /sponsors


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| root      | Object[]      |  <p>Array of <a href="#api-Sponsors-GetSponsor">sponsors</a></p>              |


