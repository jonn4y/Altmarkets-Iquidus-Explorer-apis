Altmarkets Iquidus Explorer apis
================
 Dropin files for to display Altmarkets coin data on listed coins explorers.
 
 Example:
 
 *  [Altmarkets](http://altmarketscoin.xyz/markets/altmarkets)
 
Simply drop `altmarkets.jade` in:

    explorer/views/markets

and `altmarkets.js` in:

    explorer/lib/markets


then in your `settings.json` edit the markets section like so:


       "markets": {
        "coin": "altm", # your coins ticker
        "exchange": "btc", # the market pairing your coin has on altmarkets [btc,doge,eth,ltc,altm]
        "enabled": ["altmarkets"], 
        "default": "altmarkets"
       },
       
and in the menu section of `settings.json` enable markets like so:

     "markets": true,
     


