🎉 Simple AWS Full-Stack app

A simple AWS powered app to manage events and reservations . 
URL : https://staging.dshhu0sa2qcy3.amplifyapp.com

## 🚀 Goal

The goal was to build a fully functionning app with a FE in just HTML/JS and a back end with Lambda Functions.
Data layer uses MySQL RDS and NoSQL DynamoDB.
Routing uses API gateway 
Site storage uses S3 buckets , amplify , CloudFront . 


## 🚀 My miscellaneous notes

- First thing create a budget control in AWS to make sure we stay in free tier
- set the daatabse with RDS : 
    events-rsvp-db : mysql:

    create events table
    CREATE TABLE events(
        event_id VARCHAR(64) PRIMARY KEY, 
        title VARCHAR(200) NOT NULL, 
        description TEXT,
        start_at DATETIME NOT NULL,
        venue VARCHAR(200),
        banner_url VARCHAR(300),
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    )
Inserting Sample Data:

INSERT INTO events (event_id, title, description, start_at, venue, banner_url)
VALUES
(
  'aws-meetup-manila-2025',
  'AWS User Group Manila Monthly Meetup 2025',
  'Join fellow builders for lightning talks, live demos, and networking with AWS enthusiasts in Manila.',
  '2025-10-18 18:00:00',
  'AWS PH Office, Bonifacio Global City',
  ''
),
(
  'aws-buildercards-tournament-2025',
  'AWS BuilderCards Tournament 2025',
  'Learn all about AWS BuilderCards.',
  '2025-11-08 17:00:00',
  'AWS PH Office, Bonifacio Global City',
  ''
),
(
  'aws-community-day-ph-2025',
  'AWS Community Day Philippines 2025',
  'The biggest gathering of AWS builders, user group leaders, and cloud enthusiasts in the Philippines — featuring talks, demos, and community showcases.',
  '2025-11-30 09:00:00',
  'AWS PH Office, Bonifacio Global City',
  ''
);

Create Lambda handler and API gateway

Create Dynamo db take with a PK and SK

in AWS create the DynamoDB table
Create the lamda code , update and deploy 

get all events
curl --location 'https://xxxxxx.execute-api.ca-central-1.amazonaws.com/events'

get events by ID 
curl --location 'https://xxxxxx.execute-api.ca-central-1.amazonaws.com/event/aws-meetup-manila-2025'

create bucket for static site / upload files

set cloudfront : no access , use amplify to get https
so use https://staging.dshhu0sa2qcy3.amplifyapp.com