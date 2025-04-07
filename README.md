## Authentication Development Notes

1. Create `auth` and `user` modules.

2. In `UsersService`:
   - Find a specific user.
   - Export `UserService` to make it accessible outside the module.

3. In `AuthService`:
   - Write a `signIn` function to:
     - Retrieve a user from `UserService`.
     - Verify the user’s password.
   - Use `saltRounds` (a variable determining bcrypt hash processing time; a good value is 10).

4. Define the login route in `AuthController`.

5. In `auth.service.ts` (inside the `auth` folder):
   - Inject the `JwtService`.
   - Update the `signIn` method to generate a JWT token.

6. Prefer `signAsync` for signing:
   - Signs asynchronously to avoid blocking the event loop.

7. In `AuthModule`:
   - Register the JWT module.
   - Set an expiry time and add a secret key for signing.

8. Implement authentication protection:
   - Create a guard to protect endpoints lacking tokens in headers.
   - Register the auth guard to secure protected routes.

9. JWT Signature Verification:
   - **Formula**:
  HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  your-secret
)

- **How it works**: Verifies the token by hashing the header and payload with the secret; the result must match the token’s signature.
