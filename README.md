# rocket.chat (Mongo 4.2)

Built this using Mongo 4.2 because I could not find an example out there with 4.2. I could only find 4.0 and then you needed to migrate to 4.2. I didn't understand why you had to do that when installing from scratch.

So here you are.

For this example I put the volumes in the root folder. Everyone has a root folder right? so it should work for everyone. **But I would definitely change that.**

Replace **[YOUR URL]** with the URL you are going to use for your website. I'm assuming your using a proxy for this like Nginx Proxy Manager. Setup the proxy to hit the IP address of your docker container/server and use port 3000. You need to use your URL within the docker container otherwise the application won't work properly because your breaking HTTPS. You can investigate your browser’s dev tools to see these errors.

Replace **[IP ADDRESS]** with the IP of your server.

Once you bring up the docker containers it takes some time for rocket.chat to actually come up. Give it a minute or two. The reason for this is because the Mongo Init Replica docker needs to make some changes to the MongoDB container.

Use “docker container logs rocketmongo_replica” to check if the container is done doing its work. Otherwise you should see an error.

Use “docker container logs rocketchat” to check if the rocket.chat container is up. You should see at some point you that local storage is starting and then finally the settings for the rocket.chat container should pop up.

If you see the errors below check the rocketmongo_replica container for errors or wait a bit longer.

**Error: $MONGO_OPLOG_URL must be set to the 'local' database of a Mongo replica set**

**MongoError: not master and slaveOk=false**

# 11/17/2021 Update docker-compose.yml file due to a breaking update caused when using ":latest". Rocket.chat container was producing error below.
Error: Can't find migration version 243
    at migrateDatabase (server/lib/migrations.ts:229:9)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
    at migrateDatabase (server/lib/migrations.ts:181:11)
