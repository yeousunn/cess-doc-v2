This is the interface to query the number of nominator.

```golang
// QueryNominatorCount query nominator number
//   - block: block number, less than 0 indicates the latest block
//
// Return:
//   - uint32: nominator number
//   - error: error message
func (c *ChainClient) QueryNominatorCount(block int32) (uint32, error)
```

Example code:
```golang
package main

import (
    "context"
    "fmt"
    "time"

    sdkgo "github.com/CESSProject/cess-go-sdk"
    "github.com/CESSProject/cess-go-sdk/utils"
)

var RPC_ADDRS = []string{
    //testnet
    "wss://testnet-rpc.cess.network/ws/",
}

func main() {
    sdk, err := sdkgo.New(
        context.Background(),
        sdkgo.ConnectRpcAddrs(RPC_ADDRS),
    )
    if err != nil {
        panic(err)
    }
    defer sdk.Close()

    fmt.Println(sdk.QueryNominatorCount(-1))
}
```