**SCENARIO PENGUJIAN ORDER SERVICE FTGO**

Sebelum menguji layanan order, diperlukan data consumer dan restaurant terlebih dahulu, berikut dibuat masing-masing satu data consumer dan data restaurant :

**1. Create Consumer**
	
 **Endpoint**
 
 	POST : http://localhost:8081/consumers

  **Data To Input**
  
	{
	   “Name”: {
	      “firstName”: “Gian”,
	      “lastName”: “Sandrova”
	   }
	}

**Output**

![WhatsApp Image 2024-04-05 at 9 52 43 PM](https://github.com/aininurulazizah/B2-FTGO/assets/95160599/1e7f1cfd-65c6-4887-9831-200d4eba43d6)

![WhatsApp Image 2024-04-05 at 9 54 01 PM](https://github.com/aininurulazizah/B2-FTGO/assets/95160599/3161fec8-b25d-4fcc-9d7c-e74cef6e0e52)

**2. Create Restaurant**
	
 **Endpoint**
 
 	POST : http://localhost:8084/restaurants

  **Data To Input**

	{
	   "address": {
	      "city": "Bandung",
	      "state": "Indonesia", 
	      "street1": "Jalan Merdeka",
	      "street2": "Jalan Mawar",
	      "zip": "40535"
	   }, 
	   "menu":{
	      "menuItems": [
	        {
	          "id": "001",
	          "name": "Mie Bakso",
	          "price": "12000"
	        }
	      ]
	   }, 
	    "name" : "Bakso Berkah"
	}	

**Output**

![WhatsApp Image 2024-04-05 at 21 55 25](https://github.com/aininurulazizah/B2-FTGO/assets/95161912/a96b34de-6210-4f04-8052-63919c8b6db2)

![WhatsApp Image 2024-04-05 at 21 55 27](https://github.com/aininurulazizah/B2-FTGO/assets/95161912/3f921882-5e5c-498f-a34b-891272f9648c)

Selanjutnya dilakukan pengujian untuk layanan Create Order, Revise Order, dan Cancel Order dengan beberapa kondisi data.

**1. Create Order**
	
 **Endpoint**
 
 	POST : http://localhost:8082/orders

  **Data To Input**
  1. Create ordeer Valid data test
  
	{
 	   "consumerId": 1,
	   "deliveryAddress": {
	      "city": "Bandung",
	      "state": "Indonesia", 
	      "street1": "Jalan Gelatik",
	      "street2": "Jalan Merpati",
	      "zip": "15413"
	   }, 
	   "deliveryTime": "2024-04-04T16:16:00.125Z",
    	   "lineItems": [
	     {
	      "menuItemId": "001",
	      "quantity": 2
	     }
	    ],
	    "restaurantId": 1
	}

 2. Create Order Invalid consumerId field data test
```
{
  “consumerId”:”asdfghjkl”,
  “deliveryAddress”: {
     “city”: “Bandung”,
     “state” : “Indonesia”,
     “street1”: “Jalan Gelatik”,
     “street2”: “Jalan Merpati”,
     “zip”: “15413”
  },
  “deliveryTime”: “2024-04-04T16:16:00.125Z”,
  “lineItems”: [
    {
      “menuItemId”: “001”,
       “quantity”: 2
    }
   ],
   “restaurantId”: 1
}

```

3. Create order Invalid quantity field data test
```
{
  “consumerId”: 1,
  “deliveryAddress”: {
     “city”: “Bandung”,
     “state” : “Indonesia”,
     “street1”: “Jalan Gelatik”,
     “street2”: “Jalan Merpati”,
     “zip”: “15413”
  },
  “deliveryTime”: “2024-04-04T16:16:00.125Z”,
  “lineItems”: [
    {
      “menuItemId”: “001”,
      “quantity”: “asdfghjkl”
    }
   ],
   “restaurantId”: 1
}
```

4. Create Order Invalid restaurantId field data test
```
{
  “consumerId”: 1,
  “deliveryAddress”: {
     “city”: “Bandung”,
     “state” : “Indonesia”,
     “street1”: “Jalan Gelatik”,
     “street2”: “Jalan Merpati”,
     “zip”: “15413”
  },
  “deliveryTime”: “2024-04-04T16:16:00.125Z”,
  “lineItems”: [
    {
      “menuItemId”: “001”,
      “quantity”: 2
    }
   ],
   “restaurantId”: “asdfghjkl”
}
```

5. Create order Invalid (menuItem haven't registered)
```
{
  “consumerId”: 1,
  “deliveryAddress”: {
     “city”: “Bandung”,
     “state” : “Indonesia”,
     “street1”: “Jalan Gelatik”,
     “street2”: “Jalan Merpati”,
     “zip”: “15413”
  },
  “deliveryTime”: “2024-04-04T16:16:00.125Z”,
  “lineItems”: [
    {
      “menuItemId”: “020”,
      “quantity”: 2
    }
   ],
   “restaurantId”: 1
}	
```

6. Create order Invalid (restaurant haven't registered)
```
{
 “consumerId”: 1,
  “deliveryAddress”: {
     “city”: “Bandung”,
     “state” : “Indonesia”,
     “street1”: “Jalan Gelatik”,
     “street2”: “Jalan Merpati”,
     “zip”: “15413”
  },
  “deliveryTime”: “2024-04-04T16:16:00.125Z”,
  “lineItems”: [
    {
      “menuItemId”: “020”,
      “quantity”: 2
    }
   ],
   “restaurantId”: 55
}
```

**Output**

