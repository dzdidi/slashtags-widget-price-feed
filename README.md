# slashtags-widget-price-feed

Provides price information as a slashtags feed.

Data is provided in a hyperdrive that you can replicate to get the latest information.

The drive contains the following files (example feed files are for the BTCUSD pair, but the list of available pairs are listed in the slashfeed.json file)...

```
slashfeed.json - metadata about the feeds using the type `price_feed`
feeds/
    BTCUSD-last - the last update price of the BTCUSD pair. Updated often.
    BTCUSD-24h - an array of the last 24 hourly candle closing prices (covers the last days trading)
    BTCUSD-7d - an array of the last 14 12h candle closes (covers 1 weeks trading)
    BTCUSD-30d - an array of the last 30 daily candle closes (covers 1 month)
```

The files ending `-last` will contain array of 2 elements, defined as such: 
1. the unix timestamp as string
2. the last price truncated to the integer part as string  

For example `['1670344382195','2322400']`.

Files ending `-24h`, `-7d` and `-30d` will contain an array of strings. Oldest value first. 
For example, `[ ['1670344382195', '1234.45'], ['1670344382195', '1245.78'], ['1670344382195', '1267.78'], ... ]`

The public key and encryption key of the drive are published to the logs when the app is started.
