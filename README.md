 Pango FSWatch
=====================================================================

![](https://github.com/pandafw/pango/raw/master/logo.png) [![Build Status](https://travis-ci.com/pandafw/pango-fswatch.svg?branch=master)](https://travis-ci.com/pandafw/pango-fswatch) [![Apache 2](https://img.shields.io/badge/license-Apache%202-green)](https://www.apache.org/licenses/LICENSE-2.0.html) ![](https://github.com/pandafw/pango/raw/master/logo.png)



This is a wrapper around https://github.com/fsnotify/fsnotify instead of only monitoring a top level folder,
it allows you to monitor all folders underneath the folder you specify.

### Install:

	go get github.com/pandafw/pango-fswatch


### Example:

(error handling omitted to improve readability)

```golang
import (
	"fmt"
	fswatch "github.com/pandafw/pango-fswatch"
)

// works exactly like fsnotify and implements the same API.
watcher, err := fswatch.NewFileWatcher()

// watch recursive and recieve events with callback function
watcher.AddRecursive("watchdir", fswatch.OpALL, "", func(path string, op fswatch.Op) {
	fmt.Printf("%s %s\n", path, op)
})
```

