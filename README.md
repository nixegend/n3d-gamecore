## n3d-gamecore (0.0.3-alpha)

**Warning:**
The codebase is currently considered **ALPHA quality** only, should be OK to use but is 'unstable' because the API will probably change without notice.

**Note:**
You will need to install the *Three.js* library wherever you are hosting the server because it is not bundled with this component.

_screenshot_
![0.0.2-alpha screenshot](img/n3d-gamecore-alpha2-orange-and-lemon-players-screenshot.png)


####3D WebGL Multi-Player Game Engine (Node.js / Three.js / HTML5)
This is a Node.js websockets application which provides the core functionality of a 3D multi-player game engine, most of  the original 2D code remains, it has been re-purposed to provide the player mini-map overhead view, the client and server messaging subsystem implements client prediction and responds to client input with authoritative server update packets using socket.io (Express is included but its only doing basic routing to serve the 'public/' folder files at the moment) and all of the 3D scene rendering in the browser is provided by Three.js, all connected clients will need to be running a modern WebGL/HTML5 compatible browser (such as Chrome or Firefox)

This is **not** a fully functional game, it is intended to be a scalable realtime massively multi-player component to incorporate into your game project, my goal is to support up to 512k concurrent connections (at a future stage of the project). The concept will be to keep this core component as lean and efficient as possible without adding many additional features (i.e. sophisticated collision physics) but to also include a stable API so that those extra features can easily be provided by other Node.js modules.


#### Change history
* _Aug.2013_  Forked and extended to support 3D (as well as 2D) by [joates](https://github.com/joates)
* _Apr.2013_  Forked and updated by [Asad Memon](https://github.com/asadlionpk)
* _Aug.2012_  Original Source by [Sven Bergström](https://github.com/underscorediscovery)


## Realtime Multiplayer In HTML5

Read the original article here (2D only): 
http://buildnewgames.com/real-time-multiplayer/

#### Getting started

##### using node / npm ( _easiest method_ )
* `npm install n3d-gamecore`
* `cd n3d-gamecore`
* `npm install` ( _to fetch dependencies_ )
* ( **you will still need to make the Three.js library files available at the paths expected by** `public/index.html`)
* `npm start` ( _this builds the bundle.js file needed by clients & starts the game server running_ )
* visit `http://localhost:8000` with your browser
  * use `http://localhost:8000/?debug` as the URL if you want to enable the debug interface.

##### download from github / git clone
* there are different ways to get files from github or by using git..
  * grab the most recent release bundle from [here](https://github.com/joates/n3d-gamecore/releases)
    extract all the files (from the zip/tarball)
    _rename_ `n3d-gamecore-<release_name>` to just `n3d-gamecore`
  * the terminal command `git clone git@github.com:joates/n3d-gamecore.git` will download the files but
    you **also** need to type `cd n3d-gamecore` and then `git checkout dev` to switch branches.
* Grab the latest three.js release from [here](https://github.com/mrdoob/three.js/releases)
  extract all the files (from three.js zip/tarball)
  check that the links in `n3d-gamecore/public/index.html` can access `three.min.js` (& `dat.gui.min.js` is optional)
  * you will probably just need to _rename_ the `three.js-r??` folder to `three.js`
* type `cd ..` to get back to the `n3d-gamecore` root folder
* run `npm install` ( _to fetch dependencies_ )
* run `npm start` ( _this builds the bundle.js file needed by clients & starts the game server running_ )
* Visit `http://localhost:8000` with your browser
  * use `http://localhost:8000/?debug` as the URL if you want to enable the debug interface.

NOTE: the movement controller is designed for a device with a touchscreen,
but if you have a normal (non-touch) screen it will fallback to normal mouse control ( _just click and drag to move_ ).

#### Plugin API (example)

```javascript
  var PluginExample_Client = (function() {

    function PluginExample_Client() {
      /* code which runs on the clients here */
    }

    return PluginExample_Client

  })()

  var PluginExample_Server = (function() {

    function PluginExample_Server() {
      /* server plugin code here */
    }

    return PluginExample_Server

  })()

  module.exports = {
    client:  PluginExample_Client,
    server:  PluginExample_Server,
    options: {},
    enabled: true,
    weight:  0
  }
```


MIT Licensed.

