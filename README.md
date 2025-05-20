Kraken GO API Client
====================

A simple API Client for the [Kraken](https://www.kraken.com/ "Kraken") Trading platform.

## Introduction

This is a customised / updated version of [Beldur's Kraken Go API Client](https://github.com/beldur/kraken-go-api-client). I have incorporated changes submitted by me and other users into this main repository, as well as any updates that may be required along the way for my use. I will upstream the fixes if the maintainers of the upstream repository are active again in accepting PRs.

## Changelogs

[x] Updated all the assets and asset pairs except for 1INCH
[x] Updated AssetPairInfo type to add `wsname`, `cost_decimals`, `costmin`, `tick_size`, `status`, `long_position_limit` & `short_position_limit` fields
[x] Updated TradeBalanceResponse type to add `uv` (UnexecutedValue)
[x] Changed import `io/ioutil` to `io` as ioutil is now deprecated
[x] Added time-in-force param to the AddOrder function
[x] Changed APIUserAgent from `https://github.com/beldur/kraken-go-api-client` to `https://github.com/chironjit/kraken-go-api-client`
[x] Updated minimum order values for tokens

** 1Inch asset / asset pairs cannot be added due to limitation of consts not allowing items to start with a number



Example usage:

```go
package main

import (
	"fmt"
	"log"

	"github.com/chironjit/kraken-go-api-client"
)

func main() {
	api := krakenapi.New("KEY", "SECRET")
	result, err := api.Query("Ticker", map[string]string{
		"pair": "XXBTZEUR",
	})

	if err != nil {
		log.Fatal(err)
	}

	fmt.Printf("Result: %+v\n", result)

	// There are also some strongly typed methods available
	ticker, err := api.Ticker(krakenapi.XXBTZEUR)
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(ticker.XXBTZEUR.OpeningPrice)
}
```

## Contributors
 - Piega
 - Glavic
 - MarinX
 - bjorand
 - [khezen](https://github.com/khezen)
 