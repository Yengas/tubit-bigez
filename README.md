# tubit-bigez
This is the main repo for the hackathon project developed at Getir Hackathon 2017 by `tübit`. This repo makes it easy to deploy and develop the project locally. All you need to do is clone the project with: `git clone --recursive` or init it with `git submodule update --init --recursive`. After that you can create the necessary configuration to run the project on your local machine.

## How to run
Create an `application.secret.env` file, and fill the `FACEBOOK_APP_SECRET`, `AUTH_TOKEN_SECRET` fields in the dotenv file format. Facebook secret is required for the facebook login to work, and the `AUTH_TOKEN_SECRET` maybe any arbitrary string to be used while singing auth tokens. You can also set your gmail accounts app login password on the `GMAIL_PASSWORD` field to let the application send mails when users connects their routes to eachother.

Example file content (application.secret.env):
```
FACEBOOK_APP_SECRET=21fc955224edb1a1
AUTH_TOKEN_SECRET=Tubibge0s
GMAIL_PASSWORD=eaasdxyqoaadrhal
```

Not settings these parameters correctly may make the application behave strangely. After creating this file, all you need to do is run `docker-compose up` all necessary installations will be done and you will be able to reach the webserver at `localhost:2000` for the frontend and `localhost:8080` for the backend.

### Note
There is a problem with the mongodump/mongorestore that i couldn't resolve. Mongodump files i try to initialize in the backend docker-compose file are extracted from a working demo. However when the `docker-compose up` command is run, there is a bug that causes the database-seed operation to fail inconsistently(2 out of 10 times). I have wrote about this issue on backend repo [#1](https://github.com/Yengas/tubit-bigez-backend/issues/1). Until there is a solution to this, i will keep this repo with a docker image referenced to the seeded version of mongo, so it can work without any chance to fail.
