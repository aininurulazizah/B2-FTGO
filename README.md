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
