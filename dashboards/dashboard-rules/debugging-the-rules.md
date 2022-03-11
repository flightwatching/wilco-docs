# Debugging the rules



OK, you wrote a dashboard rule and nothing happens? here are some tips to figure out what did not happens

### use the chrome inspector

Your friend is the chrome inspector. The Dashboard and Symbol IFTs are executed by you browser, not by the server. That's why it is necessary to debug it from the client browser. To access the chrome inspector, go to the page that represents your dashboard in conditions, for example an event page with the dashboard activated. Right-click on any element and choose `inspect element`

WILCO names each one of your IFT so that it is accessible within the inspector (see [this thread](https://developer.chrome.com/devtools/docs/javascript-debugging#breakpoints-dynamic-javascript))

When your page is loaded, activate the inspector. Since in the inspector, you can ctrl+p (or cmd+p on mac). Type IFT (prefix) and a combo list will display all the loaded IFTs. choose your IFT, it will be fetched in the inspector. On the left, click on the line numbers to add/remove breakpoints. Make the IFTs to be evaluated by refreshing your page, changing the event or moving around with the samples timeline. The ITFs will be called and breakpoints activated. Hover with your mouse or right-click -> watch. You will actually see your IFT working live with access to each step.

### use no-cache

WILCO creates a cache with your dashboards, symbols and rules to accelerate the loading process. When designing rules, this is not very efficient as computing the cache is slow. add a no-cache url parameter to directly use your ongoing version of the dashboard/IFTs.

e.g convert `http://localhost:9000/#/RAF-11/events/11857` to `http://localhost:9000/#/RAF-11/events/11857?no-cache`

### use the debug option

debug option logs more things in the console (chrome inspector tab) about the context and rules. e.g convert `http://localhost:9000/#/RAF-11/events/11857` to `http://localhost:9000/#/RAF-11/events/11857?debug`

you can use both options with e.g convert `http://localhost:9000/#/RAF-11/events/11857` to `http://localhost:9000/#/RAF-11/events/11857?no-cache&debug`

### console.log

In your IFT, add some `console.log(anything)` and it will appear in your inspector (console tab)
