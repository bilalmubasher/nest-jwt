<!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
[![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## JWT Signing and Verification

create auth and user modules

In UsersService, find a specific user
Export UserService so we can see it outside the module

Write sign-in function in authService, which will reterieve user from UserService, verify its password.
saltRounds is a variable that determines how much processing time is needed to calculate a single bcrypt hash(good value is 10).

Now define the login route in authcontroller

Open the auth.service.ts file in the auth folder, inject the JwtService, and update the signIn method to generate a JWT token

signAsync( sign asynchronous way and not block the event loop) preferable

Register JWT module in auth module and set expiry time and add secret key to sign it.

After that, implement guard to guard the endpoint who don't have tokens in headers.
Now - register auth guard to protect protected routes.

JWT Signature verification:-

HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  your-secret
)
