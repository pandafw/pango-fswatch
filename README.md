 Pango FSWatch
=====================================================================

![](https://github.com/pandafw/pango/raw/master/logo.png) [![Build Status](https://github.com/pandafw/pango-fswatch/actions/workflows/build.yml/badge.svg)](https://github.com/pandafw/pango-fswatch/actions?query=branch%3Amaster) [![codecov](https://codecov.io/gh/pandafw/pango-fswatch/branch/master/graph/badge.svg)](https://codecov.io/gh/pandafw/pango-fswatch) [![MIT](https://img.shields.io/badge/license-MIT-green)](https://opensource.org/licenses/MIT) ![](https://github.com/pandafw/pango/raw/master/logo.png)



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

