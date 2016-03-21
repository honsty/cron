[![GoDoc](http://godoc.org/github.com/robfig/cron?status.png)](http://godoc.org/github.com/robfig/cron) 
[![Build Status](https://travis-ci.org/robfig/cron.svg?branch=master)](https://travis-ci.org/robfig/cron)

# cron
crontab for golang

## usage
```go
import (
	"fmt"
	"time"
	
	ncron "github.com/niean/cron"
)

func main() {
	// init cron
	c := ncron.New()

	// add cron job
	c.AddFunc("* * * * * *", func() { fmt.Println("Every second") })
	c.AddFuncCC("* * * * * *", func() { fmt.Println("Every second, with max Concurrrent 2"); time.Sleep(10 * time.Second)}, 2)

	// start cron
	c.Start()

	// keep alive
	select {}
}
```

