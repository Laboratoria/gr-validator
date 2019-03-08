![Gordon Ramsay, my hero](https://media.giphy.com/media/l4pLY0zySvluEvr0c/giphy.gif)

# __gr-validator__

Take a student repositorie of Laboratoria, clone it and test it with `Laboratoria's` tests/linter in google cloud functions and send results to Laboratoria's DB.

__Important:__ gr-validator work with a `Laboratoria's` private tests repositorie in git hub, he search him with project id with `-test` suffixe, this repositorie need a standard structure you can see this structure in: https://github.com/Laboratoria/pblms-cipher-test (private repo `Laboratoria's` permissions needed)

## __Install__

Using NPM:

> $> npm install --save Laboratoria/gr-validator

Using yarn:

> $> yarn add Laboratoria/gr-validator

## __Usage__

```javascript

const validator = require('gr-validator')

validator(data, firestoreAccess, githubToken);

```

__Important:__ if you are using `gr-validator` in local environment you need to set an environment var `GITHUB_TOKEN` with Github token with `laboratoria's` read permissions

## __API__

__Data__

Type: object

Content Schema:
``` javascript

data = {
  studentUid: String,
  studentRepoUrl: String,
  studentCohortId: String,
  studentProjectId: String,
};

```

__firestoreAccess__

Type: object

Content: firestore methods for CRUD on DB

__githubToken__

Type: string

Content: Github token with `laboratoria's` read permissions

default: if `githubToken` are undefined, `gr-validator` search an take the value in `GITHUB_TOKEN` of environment variables

## __Requisites__

Upgrade memory to `2 GB` and timeout at `540 seconds` of function in `Google Cloud Platform`

link: https://console.cloud.google.com/functions/

__How?__ Click on link, choose your project, click on the function are using
`gr-validator` in my case `firestoreProjectsOnWrite`, if you see `Memory Allocated`
are `255 MB` and i want change that for `2 GB`


![Screenshot showing node version setting](https://user-images.githubusercontent.com/27020601/53919201-49f9d700-4037-11e9-87d6-e1bbd1f92ef5.png)

For default my functions have `256 MB` of Memory Allocated and timeout at `60 seconds`, so i click on `EDIT`

![Screenshot showing node version setting](https://user-images.githubusercontent.com/27020601/53919434-00f65280-4038-11e9-96b6-cc103a9f3c8a.png)

And here finally a can set Memory Allocated at `2 GB` (Max authorized), and `540 seconds` (Max authorized)

![Screenshot showing node version setting](https://user-images.githubusercontent.com/27020601/53919724-e7a1d600-4038-11e9-8776-2ab41b3a9fb0.png)

For more information of quotas of `Google Cloud Functions`: https://cloud.google.com/functions/quotas
