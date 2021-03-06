# Team 21 Backend README


## API Documentation v6
###### Luke Whiteley

Be wary when copying directly from here into something such as curl or Postman, it may change the formatting.

### Sign Up

**ENDPOINT**: https://astervo.herokuapp.com/api/registrations

**TYPE:** POST

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` javascript
{ "User" : {
  "email" : "user@example.com",
  "password" : "password",
  "password_confirmation" : "password"
}}
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "success": true,
    "info": "Registered",
    "data": {
        "user": {
            "id": 16,
            "email": "example@user.com",
            "authentication_token": "nvKoWPMwY64cu7Tzrxxm",
            "created_at": "2015-03-04T00:14:50.760Z",
            "updated_at": "2015-03-04T00:14:50.814Z"
        },
        "auth_token": "nvKoWPMwY64cu7Tzrxxm"
    }
}
```

### Log In

**ENDPOINT**: https://astervo.herokuapp.com/api/sessions

**TYPE:** POST

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` javascript
{ "User" : {
  "email" : "user@example.com",
  "password" : "password",
}}
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "success": true,
    "info": "Logged in",
    "data": {
        "auth_token": "rs9bgnHQ8rqXaW6gLGy4", // This is the token used for logging out.
        "accounts": [ // The User's Accounts.
            {
                "id": 1,
                "type": "ISA",
                "balance": 2703,
                "interest": 7.5
            },
            {
                "id": 2,
                "type": "DEBIT",
                "balance": 1597,
                "interest": 7.5
            }
        ]
    }
}
```

### Log Out

**ENDPOINT**: https://astervo.herokuapp.com/api/sessions/?auth_token= `auth_token_here`

**TYPE:** DELETE

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` python
None.
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "success": true,
    "info": "Logged out",
    "data": {}
}
```

### Transfer Money between Accounts.

**ENDPOINT**: https://astervo.herokuapp.com/api/transfers

**TYPE:** POST

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` javascript
{"transfer": {
  "to":"1", // The ID of the account you're transferring from.
  "from":"2" // The ID of the account you're transferring to.
}, "amount":"900"} // The amount you wish to transfer.
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "result": {
        "success": true,
        "message": "Transfer complete."
    },
    "accounts": [ // An array of the User's Accounts with their updated balances.
        {
            "id": 1,
            "type": "ISA",
            "balance": 2703,
            "interest": 7.5
        },
        {
            "id": 2,
            "type": "DEBIT",
            "balance": 1597,
            "interest": 7.5
        }
    ]
}
```

### Get a list of all Transfers for a User.

**ENDPOINT**: https://astervo.herokuapp.com/api/transfers

**TYPE:** GET

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` python
None
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "transfers": [
        {
            "sender_id": "2",
            "receiver_id": "3",
            "amount": 500,
            "date": "2015-02-25T10:47:41.813Z"
        },
        {
            "sender_id": "4",
            "receiver_id": "3",
            "amount": 100,
            "date": "2015-02-27T13:29:29.691Z"
        },
        {
            "sender_id": "2",
            "receiver_id": "3",
            "amount": 100,
            "date": "2015-02-27T15:55:05.507Z"
        },
        {
            "sender_id": "2",
            "receiver_id": "3",
            "amount": 100,
            "date": "2015-02-27T15:55:20.197Z"
        }
    ]
}
```

### Get questions for the Quiz.

**ENDPOINT**: https://astervo.herokuapp.com/api/questions

**TYPE:** GET

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` python
None
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "questions": [
        {
            "id": "1",
            "question": "Question?",
            "answers": [
                "Answer",
                "Answer",
                "Answer",
                "Answer"
            ]
        },
        {
            "id": "1",
            "question": "Question?",
            "answers": [
                "Answer",
                "Answer",
                "Answer",
                "Answer"
            ]
        },
        {
            "id": "1",
            "question": "Question?",
            "answers": [
                "Answer",
                "Answer",
                "Answer",
                "Answer"
            ]
        },
        {
            "id": "1",
            "question": "Question?",
            "answers": [
                "Answer",
                "Answer",
                "Answer",
                "Answer"
            ]
        },
        {
            "id": "1",
            "question": "Question?",
            "answers": [
                "Answer",
                "Answer",
                "Answer",
                "Answer"
            ]
        }
    ]
}
```

### Submit Quiz answers and get a result.

**ENDPOINT**: https://astervo.herokuapp.com/api/answers

**TYPE:** POST

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` javascript
{ "answers" : [
  {
    "id": "1",
    "answer": "Answer"
  },
  {
    "id": "1",
    "answer": "Answer"
  },
  {
    "id": "1",
    "answer": "Answer"
  },
  {
    "id": "1",
    "answer": "Answer"
  },
  {
    "id": "1",
    "answer": "Answer"
  }
        ]
}
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "score": 100
}
```

### Get all available items.

**ENDPOINT**: https://astervo.herokuapp.com/api/items

**TYPE:** GET

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` Python
None
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "items": [
        {
            "id": 1,
            "description": "Tiara",
            "image": "/assets/rewards/tiara-14caa68e5eef44060551095e4ac1000d.png",
            "cost": 1000,
            "consumable": false
        },
        {
            "id": 2,
            "description": "Crown",
            "image": "/assets/rewards/crown-fd90a9ea32701bbe6274c983ad1e3902.png",
            "cost": 1000,
            "consumable": false
        },
        {
            "id": 3,
            "description": "Lei",
            "image": "/assets/rewards/lei-4bd524d8fcdcf80a528050e369523bd9.png",
            "cost": 800,
            "consumable": false
        },
        {
            "id": 4,
            "description": "Santa Hat",
            "image": "/assets/rewards/santahat-960b0f6e818b5fb56f75445fec801314.png",
            "cost": 1000,
            "consumable": false
        },
        {
            "id": 5,
            "description": "Shades",
            "image": "/assets/rewards/shades-8710ee7155b5a0a2dcbc61b9b5101999.png",
            "cost": 350,
            "consumable": false
        },
        {
            "id": 6,
            "description": "Teddy",
            "image": "/assets/rewards/teddy-67005257cd8e624095f93c0968312bfd.png",
            "cost": 250,
            "consumable": true
        }
    ]
}
```

### Get a user's inventory.

**ENDPOINT**: https://astervo.herokuapp.com/api/inventory

**TYPE:** GET

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` Python
None
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "inventory": [
        {
            "id": 2,
            "description": "Crown",
            "consumable": false,
            "image": "/assets/rewards/crown-fd90a9ea32701bbe6274c983ad1e3902.png"
        },
        {
            "id": 3,
            "description": "Lei",
            "consumable": false,
            "image": "/assets/rewards/lei-4bd524d8fcdcf80a528050e369523bd9.png"
        },
        {
            "id": 6,
            "description": "Teddy",
            "consumable": true,
            "image": "/assets/rewards/teddy-67005257cd8e624095f93c0968312bfd.png"
        },
        {
            "id": 6,
            "description": "Teddy",
            "consumable": true,
            "image": "/assets/rewards/teddy-67005257cd8e624095f93c0968312bfd.png"
        }
    ]
}
```

### Purchase an item from the store.

**ENDPOINT**: https://astervo.herokuapp.com/api/buy

**TYPE:** POST

**HEADERS:** 

* ` Content-Type: application/json`
*  `Accept: application/json `

**PAYLOAD:** 
``` javascript
{
  "id" : "6" // Item ID.
}
```

**SAMPLE RETURN STRING:** 
``` javascript
{
    "info": {
        "success": true,
        "message": "You bought a Teddy for £250."
    }
}
```
