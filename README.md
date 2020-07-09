# Distributed-calls-using-eureka-and-ribbon
when the currencyconversionservice invokes currencyexchangeservice we would want to use the naming server 
to find out the details of the currencyexchangeservice, instead of hardcoding the url for ribbon in 
currencyconversionservice, we want ribbon to talk to the naming server and retrieve the details of all the 
instances of the currencyexchangeservice.

To enable ribbon to talk to Naming server
@RibbonClient(name="currency-exchange-service")

disable url in application.properties in currencyconversionservice

#currency-exchange-service.ribbon.listOfServers=http://localhost:8081,http://localhost:8002

no where else in the currencyconversionservice we have hardoded the url of the currencyexchangeservice and 
we dont know about the currencyexchangeservice

Important Note
without configuring the url for the currencyexchangeservice inside currencycalculationservice, we are able
to get the currencycalculationservice to talk to currencyexchangeservice

Ribbon ask the Naming Service, what are the instances of the currencyexchangeservice and it get the list back and
would invoke the appropriate currencyexchangeservice

the setup has been created using eureka and ribbon will be able to easily adjust to the fact that new instances are
coming up and existing instances are going down 

there will be no failure coz the application of server.port=somevalue has been brought down





