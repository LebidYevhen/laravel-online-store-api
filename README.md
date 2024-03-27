# laravel-online-store-api

## /api/v1/user

### /api/v1/user/login

Fields:

- email: required, string, email
- password: required, string

Example response:

- Fails

        {
            "success": false,
            "message": "Validation failed",
            "fails": {
                "email": [
                    "The email field must be a valid email address."
                ],
                "password": [
                    "The password field is required."
                ]
            }
        }

- Success

        {
            "success": true,
            "message": "The user has successfully logged in.",
            "token": "4|8FZcLWxqCVgnE5taYjEO0XNP9paEO6unt16Ibjdhacc75ca2"
        }

### /api/v1/user/register

Fields:

- name: required, string, max:255
- email: required, string, lowercase, email, max:255, unique
- password: required, confirmed (must match with the password_confirmation field)
- password_confirmation: required

Example response:

- Fails

        {
            "success": false,
            "message": "Validation failed.",
            "fails": {
                "email": [
                    "The email has already been taken."
                ],
                "password": [
                    "The password field confirmation does not match."
                ]
            }
        }

- Success

        {
          "success": true,
          "user_id": 1,
          "message": "New user successfully registered.",
          "token": "5|6FV7VjaDhC6ooZ9mJPHKlLuAbdDnMqtBMgNliMbD463d2693"
        }

### /api/v1/user/token

Authorization: A Bearer Token can be obtained by logging in or registering.

- Fails

        {
            "success": false,
            "message": "Unauthenticated."
        }

- Success

        {
            "success": true,
            "token": "5|6FV7VjaDhC6ooZ9mJPHKlLuAbdDnMqtBMgNliMbD463d2693"
        }

### /api/v1/user/user

Authorization: A Bearer Token can be obtained by logging in or registering.

- Fails

        {
            "success": false,
            "message": "Unauthenticated."
        }

- Success

        {
            "id": 1,
            "name": "User Name",
            "email": "user@email.com",
            "email_verified_at": null,
            "created_at": "2024-03-27T11:19:09.000000Z",
            "updated_at": "2024-03-27T11:19:09.000000Z"
        }

### /api/v1/user/logout

Authorization: A Bearer Token can be obtained by logging in or registering.

- Fails


        {
            "success": false,
            "message": "Unauthenticated."
        }

- Success

        {
          "success": true,
          "message": "User is logged out successfully."
        }