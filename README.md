
# Assignment for full-stack/backend developer.

Dukaan is a tech platform that enables a business to quickly set up and run an online retail store.

A typical seller installs the Dukaan app, Signs up using his mobile number and creates his store. He can then start uploading inventory (as products) to his store.
Once the store is created, he can share the store link with his/her customers on social media and starts accepting online orders.  
  
Your assignment is to Design a very basic API (Django DRF) & database (any SQL db works) structure which supports above work-flow.

### Detailed breakdown of the workflow -

 ### endpoints for seller side. (Words in Bold indicates table names)

 
1.  seller signs up using his mobile number that creates an **account**
	1.  Take mobile number & OTP (random) as input to the API
	2.  Create customer account in accounts table.
	3.  Issue a token.
	    

2.  seller creates his **store**
	1.  Take store name & address as input.  
	2.  Create store in store table. One seller can have multiple stores.
	3.  Generate a unique store link based on his store name.
	4.  Respond back with storeid and link.

3.  seller starts uploading inventory in the form of **products** and **categories**.
  
	1.  Take product name, description, MRP, Sale price, image & category as input.  
	2.  Create a category if it doesn't exist.
	3.  Create product
	4.  Respond back with id, name and image.
	 
  
4.  Seller can accept **orders** from his **customers**.
   
	1.  Create a customer table with a mobile number as unique and address details.    
	2.  Create a order table to store orders data.
	3.  When someone places an order from the buyer side, the records will be saved here.
	   

### Endpoints for Buyer side

 
1.  Seller shares his store link with his customers. To get basic store details
    
	1.  Take store link as input    
	2.  Respond back with storeId, store name, address

2.  To get product catalog & categories
   
	1.  Take storelink as input    
	2.  Respond back with the catelog, grouped by categories & sorted by number of products in the category.


3.  people (Un-authenticated users) can add items into their cart.
   
	1.  Maintain a cart on the server in either DB or redis or MongoDb    
	2.  On cart change (add / remove item) update the cart on server
	3.  For cart line items take product id, qty, storeLink as input and fetch product meta data from the DB and save them.
  

4.  Customer place an order for a product. 

	1.  Identity customer using JWT or token which can be generated using his mobile number and a OTP 
	2. Bypass the actual OTP validation flow and issue a token on any random number & OTP combination
	3.  Create a customer record if didn’t already exist for that mobile number.
	4.  Take the cart object as input and convert that into an order.
	5.  Create an order for that store & customer and return back the order id.
