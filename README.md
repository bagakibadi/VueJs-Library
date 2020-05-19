# Library App

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Usage](#usage-for-development)
- [Create Environment Variable](#create-environment-variable)
- [Related Project](#related-project-backend)

## Features

- Users who are not logged in can only view the book
- Users must sign up and sign in to make a transaction and see their profiles
- User Can't Edit Or Delete Book

## Requirements

- Node.js - Download and Install [Node.js](https://nodejs.org/en/).
- Vue.js - Download and Install [Vue.js](https://vuejs.org/v2/guide/)

## Usage for development

1. Open your terminal or command prompt
2. Type `git clone https://github.com/bagakibadi/VueJs-Library.git`
3. Open the folder and type `npm install` for install dependencies
4. Create Environment Variable [here](#create-environment-variable)
5. Before run this, you must run [Backend First](#related-project-backend)
6. Type `npm run serve` for run this app.

## Create Environment Variable

```
$ touch .env.local
$ nano .env.local
```

```
VUE_APP_ROOT_URL=YOUR_HOST_URL
VUE_APP_SECRET_KEY=YOUR_API_KEY
```

## Related Project (Backend)

* [`Backend-Library-Api`](https://github.com/bagakibadi/Backend-Library-Api)

### License
----

© [Bagus Nur Solayman](https://github.com/bagakibadi/)
MyEmail : solaybagus2@gmail.com
