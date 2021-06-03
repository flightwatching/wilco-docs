---
description: access to the currently logged in profile
---

# WILCO.user

This field contains some informations on the currently connected user as per defined in the general admin area:

* `login`: "myaccount@mycompany.com". The current login
* `airline`: the current airline the account is linked with
* `profile`: the profile of the user \(READONLY, OFFICER, ADMIN\)
* `trigram`: the trigram of the user if defined in the general admin

```javascript
if (WILCO.user.profile=='ADMIN') {
  //enable some features
}
```

```javascript
//would disable if the connected user is not an admin
MySymbol.disable(WILCO.user.profile!='ADMIN')
```

