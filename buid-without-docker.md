# Build without docker(only for windows)

## requirements

1. [Node.js](https://nodejs.org/)

2. [yarn](https://classic.yarnpkg.com/en/docs/install/)

3. [PostgreSQL](https://www.postgresql.org)

## What you need to do

1. Clone the git like [here](https://docs.google.com/document/d/1LGxfhxptioc653pqJaY5owwpZmzTg4rggqwBYcgO73I/edit#heading=h.v3ad176f7q0j)
2. [PostgreSQL Setup](##PostgreSQL Setup)
3. [Setup your environment](##Setup your environment)
4. Run it

##  PostgreSQL Setup

1. When you download the PostgreSQL,you will see Stack Builder. You can check this list to confirm your install SQL server successful.
2. Run pgAdmin in your Start Menu,it will open your web browser

![image-20210219191602558](\img\pgAdmin)
3. Set your pgAdmin password and find your local server in left list

![image-20210219191853749](\img\SQLServer-list)
4. Select 'Login/Group Roles' and crate a user let Qtweet to use it.
   1. Set the password in Definition
   2. Set "Can login?" to true in Privilges(important)

      ![image-20210219193730251](\img\setlogin)
   
5. Select Databases and create a database to let Qtweet to use.

   1. set "Owner" to the user to just create for Qtweet

   2. Give "ALL" to user

      ![image-20210219194059687](\img\Giveall)

   3. Enter "Query Tool"

      ![image-20210219194153034](Z:\Github\QTweet\img\Query)
      
   4. Open the **db-init/qtweetData.sql** file in Qtweet folder
   
   5. Execute it.
   
      ![image-20210219194517794](Z:\Github\QTweet\img\execute)

6. Leave it to run

## Setup your environment

1. Open a cmd windows at Qtweet folder and run it

   ```
   yarn install
   yarn build
   yarn install --production
   ```

   *Note:when you update QTweet by pull,you need to run it again*

2. You need to rename all *.ftl to *.o.ftl

3. You need to edit global.o.ftl and edit `$BOT_NAME` and `${PREFIX}`(it only effect help text)

4. create a `.bat` file(you can create by create a text file and rename to `.bat`)

5. fill these text and config by example.env

   ```bat
   set PGHOST=
   set PGDATABASE=
   set PGUSER=
   set PGPASSWORD=
   set DISCORD_TOKEN=
   set TWITTER_API_KEY=
   set TWITTER_API_SECRET_KEY=
   set TWITTER_ACCESS_TOKEN=
   set TWITTER_ACCESS_TOKEN_SECRET=
   set DBL_TOKEN=
   set TZ=
   set DEFAULT_LANG=
   set VERBOSE=
   set PREFIX=
   set SHARD_SPAWN_DELAY=
   set SHARD_SPAWN_TIMEOUT=
   set TWITTER_MAX_RECONNECT_DELAY=
   set TWEETS_TIMEOUT=
   set USERS_CHECK_TIMEOUT = 
   set USERS_BATCH_SIZE = 
   set DISABLE_SANITY_CHECK = 
   set DISABLE_STREAMS = 
   node -r esm dist/src/index.js
   ```