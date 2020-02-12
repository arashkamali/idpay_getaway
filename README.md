# idpay_getaway
use idpay getaway by python &amp; django


powerd by : AraKam Group
https://arakam.ir


# install packages

    pip install zeep
    
# import packages

    from django.views.decorators.csrf import csrf_exempt
    import zeep
    from zeep import Client
    import requests
    import json
    
    
# start payment

      amount = '10000'
      url = 'https://api.idpay.ir/v1.1/payment'
      orderid = '123456'
      callbackurl = 'yourdomain.com/verify'

      data = {'order_id': orderid , 'amount': amount, 'callback':callbackurl}
      headers = {'Content-Type': 'application/json', 'X-API-KEY': api, 'X-SANDBOX':'1'}
      r = requests.post(url, data=json.dumps(data), headers=headers)

      if r.status_code == 201 :

          e = r.json()
          link = e['link']
          pid = e['id']

          b = Main(payment_id=pid, amount=int(amount))
          b.save()

          return redirect(link)
                   
      
