# Stripe Integration

## Summary

 - This cartridge will let you do payments and create payment method for each transaction.
 - In this cartridge we will use stripe paymentIntents API and paymentsMethod API.

### Create Merchant Account on Stripe

 - Visit this link https://dashboard.stripe.com/login and create your stripe merchant account.
 - When creating new account be sure that you choose your country US because we will be doing payments in US$ for storefront.
 - Fill up the form and choose business type as Individual and add a fake bank account.
 - After coming to Dashboard, goto  customer tab and create a customer for test payment.
### Setup Payment Processor & Preferences
 - Now in metadata.zip extract it & open sites and change the folder name *neeraj-site* to your site ID and then zip it again.
 - Import the metadata with changed folder name and check 
	 - if payment processor name STRIPE and 
	 - 2 custom preferences *Stripe_API_Key* and *Stripe_Test_Customer_ID* is created or not.
 - If not then create manually
	 - Payment Processor name : STRIPE.
	 - Custom Preferences : Admin > System Objects > SitePreference - create attribute with the name provided above and then create attribute group with name STRIPE and add the attributes to it.
 - Then open Home tab in dashboard and copy your secret key and paste it in preference. 
 - Open your Customer Tab and copy the customer ID and paste it in the preference.

### Setup Service

 - There will be 2 service :-
	 - int.stripe.intents
		 - credentials : *int.stripe.intents.credentials* - url : https://api.stripe.com/v1/payment_intents
		 - profile : *int.stripe.intents.profile* - timeout : 7,000 ms
	 - int.stripe.paymentMethod
		 - credentials : *int.stripe.paymentMethod.credentials* - url : https://api.stripe.com/v1/payment_methods
		 - profile : *int.stripe.intents.profile* - timeout : 20,000 ms


 - Now add the cartridge *int_stripe_ns* to the left most of cartridge path, eg :- int_stripe_ns:app_storefront_base.
