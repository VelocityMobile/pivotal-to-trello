pivotal-to-trello [![Build Status](https://travis-ci.org/recurser/pivotal-to-trello.png?branch=master)](https://travis-ci.org/recurser/pivotal-to-trello)
=================

This project of fork of [pivotal-trello gem](https://github.com/recurser/pivotal-to-trello) though it includes lots of fixes and it's done as a standalone ruby project, not a gem.

Fixes my fork includes:

* Bulk migration won't stop if exception raised
* SSL enabled for Pivotal API: https://github.com/recurser/pivotal-to-trello/pull/3
* Tasks migration added: https://github.com/recurser/pivotal-to-trello/pull/1

This project provides a script for exporting a [Pivotal Tracker](https://www.pivotaltracker.com/) project to [Trello](https://trello.com/).

Getting started
---------------

1. Install the gem:

        > git clone git@github.com/kirs/pivotal-to-trello.git

2. Install dependecies:

        > bundle install

3. Run the importer:

        > bin/pivotal-to-trello import --trello-key TRELLO_API_KEY --trello-token TRELLO_TOKEN --pivotal-token PIVOTAL_TOKEN

  See the [Obtaining API credentials](#obtaining-api-credentials) section for details on how to obtain these credentials.

  The importer will ask you a series of questions to identify which Trello lists you want to import certain classes of stories into. It will then import the stories into Trello, along with any associated comments. It does not currently have the ability to import attachments.

  For example :

        > bin/pivotal-to-trello import --trello-key TRELLO_API_KEY --trello-token TRELLO_TOKEN --pivotal-token PIVOTAL_TOKEN

        Which Pivotal project would you like to export?
        1. Android App
        2. IOS App
        3. Tech Support
        4. Web App
        Please select an option : 4

        Which Trello board would you like to import into?
        1. Development
        2. Welcome Board
        3. Wish List
        Please select an option : 1

        Which Trello list would you like to put 'icebox' stories into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 6

        Which Trello list would you like to put 'current' stories into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 7

        Which Trello list would you like to put 'finished' stories into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 5

        Which Trello list would you like to put 'delivered' stories into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 4

        Which Trello list would you like to put 'accepted' stories into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 10

        Which Trello list would you like to put 'rejected' stories into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 10

        Which Trello list would you like to put 'backlog' bugs into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 2

        Which Trello list would you like to put 'backlog' chores into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 2

        Which Trello list would you like to put 'backlog' features into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 2

        Which Trello list would you like to put 'backlog' releases into?
        1. Accepted
        2. Backlog
        3. Bugs
        4. Delivered
        5. Finished
        6. Icebox
        7. In Progress
        8. Rejected
        9. Releases
        10. [don't import these stories]
        Please select an option : 2

        What color would you like to label bugs with?
        1. Blue
        2. Green
        3. Orange
        4. Purple
        5. Red
        6. Yellow
        7. [none]
        Please select an option : 5

        What color would you like to label features with?
        1. Blue
        2. Green
        3. Orange
        4. Purple
        5. Red
        6. Yellow
        7. [none]
        Please select an option : 2

        What color would you like to label chores with?
        1. Blue
        2. Green
        3. Orange
        4. Purple
        5. Red
        6. Yellow
        7. [none]
        Please select an option : 6

        What color would you like to label releases with?
        1. Blue
        2. Green
        3. Orange
        4. Purple
        5. Red
        6. Yellow
        7. [none]
        Please select an option : 4

        Beginning import...
        Creating a card for chore 'My example chore'.
        ...

Obtaining API credentials
-------------------------

You can get your Trello application key by logging into Trello, and then visiting [https://trello.com/1/appKey/generate](https://trello.com/1/appKey/generate)

Your 32-character application key will be listed in the first box.

To obtain your Trello member token, visit the following URL, substuting your Trello application key for *APP_KEY*:

[https://trello.com/1/authorize?key=APP_KEY&name=Pivotal%20To%20Trello&response_type=token&scope=read,write](https://trello.com/1/authorize?key=APP_KEY&name=Pivotal%20To%20Trello&response_type=token&scope=read,write)

Click the *Allow* button, and you will be presented with a 64-character token.

See the [Trello documentation](https://trello.com/docs/gettingstarted/index.html#getting-an-application-key) for more details.

The Pivotal Tracker token can be found at the bottom of your [Pivotal profile page](https://www.pivotaltracker.com/profile).


Authors & license
------

*Original gem:*

Dave Perrett :: hello@daveperrett.com :: [@daveperrett](http://twitter.com/daveperrett)

Original license: [LICENSE.txt](https://github.com/kirs/pivotal-to-trello/blob/master/LICENSE.txt)

*This fork:*

[Kir Shatrov](http://github.com/kirs)

