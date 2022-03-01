go-minisat
=================

Golang binding for minisat.



Installation
----------------

### Install minisat


Arch linux

```sh
$ yaourt -S minisat-git
```

Other

```sh
$ git clone https://github.com/niklasso/minisat
$ cd minisat
$ make config prefix="/usr"
$ make
$ sudo make install
```

### Install go-minisat

```sh
$ go get github.com/pocke/go-minisat
```


Usage
-----------


```go
package main

import (
  "fmt"
  "github.com/pocke/go-minisat"
  "math/rand"
	"time"
)

func main() {
  rand.Seed(time.Now().UnixNano())
  s := minisat.NewSolver(rand.Float64())
  v1 := s.NewVar()
  v2 := s.NewVar()
  s.AddClause(v1, v2)
  s.AddClause(v1, v2.Not())
  s.AddClause(v1.Not(), v2.Not())
  fmt.Println(s.Solve())  // => true

  fmt.Println(s.ModelValue(v1))  // => true, nil
  fmt.Println(s.ModelValue(v2))  // => false, nil
}
```


Example
------------

- [sudoku-solver](https://github.com/pocke/sudoku-solver)


License
-----------

Copyright &copy; 2015 Masataka Kuwabara
Licensed [MIT][mit]
[MIT]: http://www.opensource.org/licenses/mit-license.php
