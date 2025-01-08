# Requirement Document: User Profile Management System

## Overview
This document outlines the requirements for building a **User Profile Management System**, which fetches user data, displays avatars, and includes features like searching, sorting, and deletion confirmation.

## Functional Requirements

### 1. Fetch Users' Profile Data
- **API Endpoint**: `GET https://jsonplaceholder.typicode.com/users`
- **Response Data Structure**: The API returns an array of 10 users, each with the following fields:

```json
[
  {
    "id": "integer",
    "username": "string",
    "name": "string",
    "email": "string",
    "phone": "string",
    "website": "string",
    "address": {
      "street": "string",
      "suite": "string",
      "city": "string",
      "zipcode": "string"
    },
    "company": {
      "name": "string"
    }
  }
]
```

### Key Attributes

- **id**: The unique identifier for the user.
- **username**: A unique username for the user (used for avatar URL generation).
- **name**: The user's full name.
- **email**: The user's email address.
- **phone**: The user's contact number.
- **website**: The user's personal or company website.
- **address**: The user's address including street, suite, city, and zipcode.
- **company**: The company name where the user works.


### 2. Avatar Generation

- **API Endpoint**: `GET https://avatars.dicebear.com/v2/avataaars/{{username}}.svg?options[mood][]=happy`
- **Dynamic URL**: Replace `{{username}}` with the actual username of the user from the fetched data. For example, if the username is `psamd`, the avatar URL will be:

  ```plaintext
  https://avatars.dicebear.com/v2/avataaars/psamd.svg?options[mood][]=happy

### 3. Loading Indicator

- **Requirement**: A loading indicator must be displayed when the app is fetching the user data from the API.
- **Behavior**: The loading indicator should be visible until the data is fetched and ready to be displayed on the screen.
- **Source**: The loading indicator style can be obtained from Tobias Ahlin's Spinkit.
- **Design**: Use a suitable Spinkit animation (such as "Three Bounce" or "Fading Circle") while the data is loading.

### 4. User Search Functionality

- **Search Input**: A search bar should be provided at the top of the user list view to allow users to search for a specific user by name or username.
- **Search Behavior**:
  - As the user types in the search bar, the list of users should filter in real-time, showing only those users whose names or usernames contain the search term.
  - The search should be **case-insensitive**.

### 5. User Sorting Functionality

- **Sort by Name/Username**: Users should be able to sort the displayed users either by their name or username alphabetically.
- **Sorting Behavior**:
  - A sort option should be provided to the user with a dropdown or button to choose between sorting by name or username.
  - Sorting should be in **ascending alphabetical order** by default, with an option to toggle to descending order.

## 6. Delete User Confirmation Popup
  When a user selects the option to delete a user, a confirmation popup should appear to confirm the deletion action.

  **Popup Content**
  - The popup should display the following message:
    "Are you sure you want to delete this user?"

- **Options in the Popup**:
  - Yes, Delete: To confirm the deletion of the user.
  - Cancel: To close the popup and cancel the deletion action.

- **Sorting Behavior**:
  - If the user confirms (Yes, Delete)**: The user is removed from the list.
  - If the user cancels (Cancel)**: The popup closes and the deletion action is not performed.
