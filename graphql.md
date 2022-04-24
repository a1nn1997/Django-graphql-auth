# 1
## to extract all users
query {
  users{
    edges{
      node {
        pk
        firstName
        lastName
        username
        email
        isStaff
        isActive
      }
    }
  }
}

# 2
## to extract current login user
query {
    me{
        pk
        firstName
        lastName
        username
        email
        isStaff
        isActive
    }
}

# 3
## create user with graphql
mutation{
  register(
    email : "2@2.com",
    username : "user2",
    password1: "Admin123admin123",
    password2: "Admin123admin123"
  )
  {
    success,
    errors,
    token,
    refreshToken,    
  }

# 4
  ## verify user 
  mutation{
  verifyAccount(token:"eyJ1c2VybmFtZSI6InVzZXIyIiwiYWN0aW9uIjoiYWN0aXZhdGlvbiJ9:1nidXe:Z03D5i-YqzpoMTOCZvq8Wpv2MYgt87JOH5qEJSi_pEg") 
  # varification token taken from previous part
  {
    success
    errors
  }
}

# 5
## token refresh
mutation{
  tokenAuth(username: "ann",password: "123"){
    success,
    errors,
    token,
    refreshToken,
    user{
      pk,
      id,
      username,
      email,
      isStaff,
      isActive,
    }
  }
}  

# 6
## update account credential

### Authorization in postman

mutation{
  updateAccount(firstName: "ann1")
  {
    success
    errors
  }
}

# 7
## verify email

## if email registered it will show error else register email

mutation{
  resendActivationEmail(email: "b@b.com"){
    success
    errors
  }
}

# 8
## send password email link if email is registered

mutation{
  sendPasswordResetEmail (email: "b@b.com"){
   success
    errors
  }
}

# 9
## reset password

mutation{
  passwordReset(
    token:"eyJ1c2VybmFtZSI6InVzZXIxIiwiYWN0aW9uIjoicGFzc3dvcmRfcmVzZXQifQ:1nieWG:HxvwU4-II2CfeNRVV5KWjfQtL29lghMnxef8rc8C4Y4",
    newPassword1: "admin123Admin123",
    newPassword2: "admin123Admin123"
  ){
    success
    errors
  }
}

# 10
