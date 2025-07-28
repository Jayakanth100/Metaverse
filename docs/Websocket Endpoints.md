#### Client side events

1. Join a space

	```json
	{
		"type": "join",
		"payload": {
			"spaceId": "123",
			"token": "<jwt-token>"
		}
	}
```

2. Movement

	```json
	{
		"type": "move",
		"payload": {
			"x": 2,
			"y": 3
		}
	}
```

#### Server sent events

1. Space joined

	```json
	{
		"type": "space-joined",
		"payload": {
			"spawn": {
				"x": 2,
				"y": 3
			},
			"users": [
				{
					"id": 1,
				}
			]
		}
	}
```

2. Movement rejected
	- User moves beyond the wall
	- User collided with a different user
	- User tried to sit on an element that is st
	
	```json
	{
		"type": "movement-rejected",
		"paylaod": {
			"x": 2,
			"y": 3
		}
	}
```

3. Movement

	```json
	{
		"type": "movement",
		"paylaod": {
			"x": 1,
			"y": 2,
			"userId": "123"
		}
	}
```

4. Leave

	```json
	{
		"type": "user-left",
		"paylaod": {
			"userId": 1
		}
	}
```
