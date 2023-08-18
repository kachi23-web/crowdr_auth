# **Web Authentication Module with NestJS**

The Web Authentication Module is a comprehensive solution for adding user authentication and authorization features to your NestJS application. This module is designed to streamline the process of integrating various authentication providers and securing your web endpoints.

## **Features**

  * User registration with email confirmation
  * User login with customizable strategies (local, OAuth, etc.)
  * JWT (JSON Web Token) based authentication
  * Role-based authorization
  * Password reset functionality
  * Middleware for protecting routes
  
## **Installation**

  To integrate the Web Authentication Module into your NestJS application, follow these steps:

  - [ ] Install the module package using npm:
  ```npm install @nestjs/web-authentication```
  - [ ] Import the WebAuthenticationModule into your main application module:
 
   ```javascript #000000
   import { Module } from '@nestjs/common';
   import { WebAuthenticationModule } from '@nestjs/web-authentication';

  @Module({
  imports: [WebAuthenticationModule.forRoot({
    // Configure options here
  })],
})
export class AppModule {};
```


- [ ] Configure the module options in the forRoot method.

## **Configuration**

The module supports various configuration options to tailor authentication to your application's needs:

  * secretKey: Your application's secret key for JWT encryption.
  * jwtExpirationTime: Expiration time for JWT tokens (e.g., '1h', '7d', '30d').
  * jwtIssuer: Issuer of the JWT tokens.
  * userEntity: The User entity class.
  * emailConfirmation: Enable/disable email confirmation during user registration.
  * roles: An array of role names used in role-based authorization.
  * emailSender: Configure the email sending service.
  * resetPassword: Enable/disable password reset functionality.
  
## **Usage**

**User Registration:** 

Use the AuthService to register new users with email confirmation.

```javascript
const user = await authService.register({
  email: 'user@example.com',
  password: 'password',
});
```

##### **User Login:** 

Implement various login strategies with the AuthService.

```javascript
  const token = await authService.login({
  email: 'user@example.com',
  password: 'password',
});
```

##### **Protect Routes:**

Use the AuthGuard to protect routes based on user authentication and roles.
* @UseGuards(AuthGuard, RolesGuard)
* @Roles('admin')
* @Get('admin/dashboard')
* async getAdminDashboard() {
  // ...
}

##### **Password Reset: Enable users to reset their passwords with the AuthService.**
```await authService.requestPasswordReset('user@example.com');```

### Contribution

Contributions to this module are welcome! If you encounter any issues, have feature requests, or want to contribute, please open an issue or submit a pull request on our GitHub repository.
    
## **License**

This module is released under the MIT License.

With the Web Authentication Module for NestJS, you can easily add secure authentication and authorization to your web application. Don't hesitate to refer to the documentation for more in-depth information and examples.





