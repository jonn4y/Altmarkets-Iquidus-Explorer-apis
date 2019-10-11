Altmarkets Iquidus Explorer apis
================
 Dropin files for to display Altmarkets coin data on listed coins explorers.
 
 Example:
 
 *  [Altmarkets](http://altmarketscoin.xyz:3001/markets/altmarkets)
 
Simply drop `altmarkets.jade` in:

    explorer/views/markets

and `altmarkets.js` in:

    explorer/lib/markets

Now we tell Iquidus where the find the js file by editing `database.js` in:

    explorer/lib/markets

around line 11 (just above poloniex) add:

      , altmarkets = require('./markets/altmarkets')
      
then around line 194 add:

    case 'altmarkets':
      altmarkets.get_data(settings.markets.coin, settings.markets.exchange, function(err, obj){
        return cb(err, obj);
      });
      break;


then in your `settings.json` edit the markets section like so:


       "markets": {
        "coin": "altm", # your coins ticker
        "exchange": "btc", # the market pairing your coin has on altmarkets [btc,doge,eth,ltc,altm]
        "enabled": ["altmarkets"], 
        "default": "altmarkets"
       },
       
and in the menu section of `settings.json` enable markets like so:

     "markets": true,
     
     
Edit the `locale.js` file located:

    explorer/lib/
    
With:
    exports.altmarkets = "Altmarkets",
    
around line #137 and restart.

to get the initial data to pull you may need to call:

    node scripts/sync.js market
    
Then finally keep the market data updated with a cron if not already added:

    */2 * * * * cd /path/to/explorer && /usr/bin/nodejs scripts/sync.js market > /dev/null 2>&1