# Use With CAUTION and expect something can give error(s). PLEASE BE CAREFUL and TEST YOUR CODE WISELY #
This library is tested with code below on FreeBSD 13.1 and it is worked.
No Further testing applied, because of this, you CAN NOT completely trust this package!!!
I just needed this package to test another application and i created this fork ,in order to help FreeBSD users for Golang Projects which needs this package.

This is the fork of github.com/jsimonetti/berkeleydb which is not maintained anymore but now with this fork, it seems working on FreeBSD 13.1.

This application now using Berkeley DB version 5.x you need to instal it if your system does not have it.



### BerkeleyDB Bindings

This package provides BerkeleyDB wrappers for the C library using `cgo`.

To build, you will need a 5.x version of BerkeleyDB.

It is tested with go version go1.18.2 freebsd/amd64



### Example
```go

package main

import (
        "fmt"

        "github.com/UlasSAYGINIM/berkeleydb5freebsd"
)

func main() {
        var err error

        db, err := berkeleydb.NewDB()
        if err != nil {
                fmt.Printf("Unexpected failure of CreateDB %s\n", err)
        }

        err = db.Open("./test.db", berkeleydb.DbHash, berkeleydb.DbCreate)
        if err != nil {
                fmt.Printf("Could not open test_db.db. Error code %s", err)
                return
        }
        defer db.Close()

        err = db.Put("key", "value")
        if err != nil {
                fmt.Printf("Expected clean Put: %s\n", err)
        }

        value, err := db.Get("key")
        if err != nil {
                fmt.Printf("Unexpected error in Get: %s\n", err)
                return
        }
        fmt.Printf("value: %s\n", value)

}

```
