# entps

[ent](https://github.com/ent/ent) pure go sqlite3 driver

# example

```go
package main

import (
	"context"
	"log"

	"<project>/ent"
	_ "github.com/xiaoqidun/entps"
)

func main() {
	client, err := ent.Open("sqlite3", "file:ent?mode=memory&cache=shared&_fk=1")
	if err != nil {
		log.Fatalf("failed opening connection to sqlite: %v", err)
	}
	defer client.Close()
	if err := client.Schema.Create(context.Background()); err != nil {
		log.Fatalf("failed creating schema resources: %v", err)
	}
}
```