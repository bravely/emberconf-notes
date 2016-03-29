Sidenote:

> Check out HospitalRun

# Service Workers

### High level overview

* Service workers manipulate what's going on at the network level
* Key feature: Cache API
* Fetch is the new XHR: https://gauntface.com/blog/2015/02/11/fetch-is-the-new-xhr
* Used to be called NavigationController
* Like WebWorkers in that they run in a separate thread
* Shift+Refresh IS BAD. According to the spec, it disables ServiceWorkers in default!

------------------

### Broccoli-ServiceWorker just works. Mostly.
`ember install broccoli-serviceworker`

#### example config options:

```javascript
ENV.serviceWorker = {
  enabled: true,
  debug: true,
  precacheURLS: ['/mystaticresource'],
  excludePaths: ['test.*', 'robots.txt'],
  fallback: [
    'online.html /offline.html'
  ],
  networkFirstURLs: [
    '/api/todos'
  ],
  swIncludeFiles: [
    'bower_components/couchdbthing'
  ]
}
```

#### Broccoli-ServiceWorker includes the Service Worker Toolbox

https://github.com/GoogleChrome/sw-toolbox


### `//app/serviceworkers/my-sw.js`
Any logic here will run in your app's service worker
* good way to bring in your own code

https://github.com/hospitalrun/hospitalrun-frontend/blob/master/app/serviceworkers/pouchdb-sync.js

### Reason to use Service Workers:
* Network sucks?: https://paul.kinlan.me/using-service-worker-server-side-adaption-based-on-network-type/
* Offline, of course.
* Running PouchDB in a ServiceWorker to help keep the process solid
* Serverless app, possibly? https://glebbahmutov.com/blog/run-express-server-in-your-browser/
* Background Sync: Actions can be deferred until a stable connection is there.

### There's not a great way to test ServiceWorkers in Ember.
Possible example: https://github.com/GoogleChrome/sw-unit-test-sample

### AppCache is on its way out. ServiceWorker can be the future.
https://www.fxsitecompat.com/en-CA/docs/2016/application-cache-support-will-be-removed/
Insecure HTTP model with it.

### Check out PouchDB
https://pouchdb.com/

Talk given by [@jkleinsc](https://twitter.com/jkleinsc)
