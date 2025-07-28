#### User

1. Create user (Sign in)
	- POST `/api/v1/signup`
	- Request body: 
	
	```json
	{
		"username": "jai",
		"password": "password",
		"type": "admin"
	}
```

2. Login user (Log in)
	- POST `/api/v1/signin`
	- Request body:

	```json
	{
		"username": "jai",
		"password": "password"
	}
```
	
	- Response body:
	
	```json
	{
		"token": "<token-generated>"
	}
```

#### User info

1. Update metadata 
	- POST  `/api/v1/metadata`
	- Request body:
	
	```json
	{
		"avatarId": "123"
	}
	```

2. Get available avatar
	- GET `/api/v1/avatars`
	- Response body:

	```json
	{
		"avatars": [
			{
				"id": 1,
				"imageUrl": "<url>"
			}
		]
	}
	```

3. Get other users metadata (name and avatar url)
	- GET `/api/v1/user/metadata/bulk?ids=[1, 3, 55]`
	- Response body:
	
	```json
	{
		"avatars": [
			{
				"userId": 1,
				"imageUrl": "<image-url>"
			}
		]
	}
	```
#### Space dashboard

1. Create a space 
	 - POST `/api/v1/space`
	 - Response body:
	 
	```json
	{
		"name": "Test",
		"dimensions": "100x200",
		"mapId": "<id> | empty"
	}
	```

2. Get all spaces
	- GET `/api/v1/space/all`
	- Response body:
	
	```json
	{
		"Spaces": [
			{
				"name": "Test",
				"dimensions": "100x200",
				"mapId": "<id> | empty",
				"thumbnail": "<image>"
			}
		]
	}
	```

3. Delete a space
	- DELETE `/api/v1/space/:spaceid`
	- Request body:
	
	```json
	{
		"userId": "<userId>"
	}
	```

#### Arena

1. Get a space
	- GET `/api/v1/space/:spaceId`
	- Response body:

	```json
	{
		"dimensions": "100x200",
		"elements": [
			{
				"id": 1,
				"element": {
					"id": "chair1",
					"imageUrl": "<image-url>",
					"static": false ,
					"dimensions": "100x200"
				}
				"x": 20,
				"y": 20
			}
		]
	}
	```

2. Add an element
	- POST `/api/v1/space/element`
	- Request body:

	```json
	{
		"elementId": "chair1",
		"spaceId": "123",
		"x": 50,
		"y": 20
	}
	```


3. See all available elements
	- GET `/api/v1/elements`
	- Response body:

	```json
	{
		"elements": [
			{
				"id": 1,
				"imageUrl": "<image-url>",
				"dimensions": "100x200"
			}
		]
	}
	```


4. Delete an element
	- DELETE  `/api/v1/space/element` 
	- Request body:

	```json
	{
		"spaceId": "123",
		"elementId": "1"
	}
	```

#### Admin/Map creator endpoints

1. Create an element
	- POST `/api/v1/admin/element`
	- Request body:
	
	```json
	{
		"iamgeUrl": "<image-url>",
		"width": 1,
		"height": 1,
		"static": true
	}
	```

2. Update an element
	- PUT `/api/v1/admin/element:elementId` - (can't update the dimensions once created)
	- Request body:

	```json
	{
		"imageUrl": "<image-url>"
	}
	```

3. Create an avatar
	- POST `/api/v1/admin/avatar`
	- Request body:
	
	```json
	{
		"iamgeUrl": "<image-url>"
	}
	```

	- Response body:

	```json
	{
		"avatarId": "123"
	}
	```

4. Create a map
	- POST `/api/v1/admin/map`
	- Request body
	
	```json
	{
		"thumbnail": "<thum-image>",
		"dimensions": "100x200",
		"defaultElements": [
			{
				"id": 1,
				"elementId": "chair1",
				"x": 20,
				"y": 20
			}
		]
	}
	```


