crypto
======

Python class for interacting with the crypto-trade api


Simple class for interacting with the crypto-trade api.
For full usage make sure to check the crypto trade api documentaion.
https://www.crypto-trade.com/api/documentation

I'll be working on better functrions for some of the examples outlined below.


#Example placing an order  		
cryp.req('trade',{"pair":"ltc_btc","type":"Buy","amount":ltc_bid_amount,"rate":price_to_bid})		
						
#Example Cancelling an order
cryp.req('cancelorder',{"orderid":order_id})

#Example Get Funds
account_info=cryp.req('getinfo')
orig_crypto_ltc_amount=float(account_info['data']['funds']['ltc'])
orig_crypto_btc_amount=float(account_info['data']['funds']['btc'])
orig_crypto_usd_amount=float(account_info['data']['funds']['usd'])


#Example Get and Cancel Last Two Days of Orders
unix_time_lag=int(time.time()-166400)
for order in cryp.req('ordershistory',{'start_date':unix_time_lag})['data']:
	if  order["status"]=="Active" or order["status"]=='Partly Completed':
		cryp.req('cancelorder',{"orderid":int(order["id"])})


Donations
BTC : 115biJEmRzBetyo8MB3epR3ahJpdKLv6Er
LTC : LPRjrB2jivoi1keoAUcQSghepyipZ1wfhG
