# UT-Tooti

UT-Tooti is a **command-line social media platform** implemented in C, designed for educational purposes as part of the Introduction to Programming course at the University of Tehran. This project demonstrates advanced concepts in data structures, dynamic memory management, and algorithms through the implementation of a mini social network.

## 🚀 Project Overview

UT-Tooti simulates a social media platform where users can:
- **Sign up** and **login** with username/password authentication
- **Create posts** with unique post IDs
- **Like posts** from other users
- **Delete their own posts**
- **Find and view other users'** posts and profiles
- **View their own profile** with all posts and engagement metrics

The project emphasizes **dynamic memory allocation**, **linked list data structures**, and **string manipulation** in C programming.

## 🏗️ Architecture & Data Structures

### Core Data Structure
The application is built around a **USER_INFO** structure that implements a **linked list** for each user's posts:

```c
struct USER_INFO {
    char *User_Pass;     // User password
    char *Username;      // Username
    char *post;          // Post content
    int post_ID;         // Unique post identifier
    int like;            // Number of likes
    USER_INFO *next;     // Pointer to next post (linked list)
};
```

### Memory Management Strategy
- **Dynamic array of pointers** to USER_INFO structures for managing multiple users
- **Dynamic string allocation** for usernames, passwords, and posts
- **Linked lists** for storing multiple posts per user
- **Dummy nodes** as list headers for efficient insertion/deletion

### Key Algorithms Implemented

1. **Dynamic String Input (`dyn_str`)**: Dynamically allocates memory as characters are read
2. **User Authentication**: Linear search through user array with string comparison
3. **Post Management**: Linked list traversal and manipulation
4. **Memory Reallocation**: Dynamic resizing of user array as new users sign up

## 📁 Project Structure

- **`PROJECT3.c`**: Main program with user interface and command parsing
- **`Structs.c`**: Implementation of core data structures and user management functions
- **`Structs.h`**: Header file defining the USER_INFO structure and function prototypes
- **`func.c`**: Utility functions for string manipulation and input validation
- **`func.h`**: Header file for utility functions
- **`Description/CA3_Description.pdf`**: Project requirements and specifications

## ⚡ Key Features & Implementation

### 1. **User Authentication System**
- **Signup**: Validates unique usernames, stores credentials in dynamic array
- **Login**: Authenticates users against stored credentials
- **Input Validation**: Ensures proper format (username password) with space checking

### 2. **Post Management System**
- **Create Posts**: Adds posts to user's linked list with auto-incrementing IDs
- **Delete Posts**: Removes specific posts by ID using linked list deletion
- **Post Viewing**: Displays all posts with metadata (likes, ID, content)

### 3. **Social Features**
- **Like System**: Users can like posts by specifying username and post ID
- **User Discovery**: Find and view any user's profile and posts
- **Personal Profile**: View own posts and engagement statistics

### 4. **Advanced C Programming Concepts**
- **Dynamic Memory Management**: Extensive use of malloc/realloc/free
- **Pointer Manipulation**: Complex pointer operations for linked lists
- **String Processing**: Custom string utilities with dynamic allocation
- **Modular Design**: Clean separation between data structures and utilities

## 🛠️ Usage Instructions

### Commands Available:

#### Authentication Commands:
- **`signup <username> <password>`**: Create a new user account
- **`login <username> <password>`**: Login to existing account

#### Post Management Commands (after login):
- **`post <content>`**: Create a new post
- **`delete <post_id>`**: Delete your own post by ID
- **`info`**: View your profile and all your posts

#### Social Commands (after login):
- **`like <username> <post_id>`**: Like a specific post
- **`find_user <username>`**: View another user's profile and posts

#### System Commands:
- **`logout`**: Return to main menu (signup/login)

### Example Session:
```
- signup alice mypassword123
Signup successful!

- login alice mypassword123
Login successful!

- post Hello everyone, this is my first post!
Post successfully added!

- post Check out this amazing algorithm I learned today
Post successfully added!

- info
user:alice
post_id:1
like:0
post:Hello everyone, this is my first post!
----------------------
user:alice
post_id:2
like:0
post:Check out this amazing algorithm I learned today
----------------------

- find_user bob
user:bob
post_id:1
like:2
post:Learning C programming is fun!
----------------------

- like bob 1
Post liked successfully!

- logout
```

## 🏃‍♂️ How to Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/ut-tooti.git
   cd ut-tooti
   ```

2. **Compile the project:**
   ```bash
   gcc -o ut-tooti PROJECT3.c func.c Structs.c
   ```

3. **Run the application:**
   ```bash
   ./ut-tooti
   ```

## 🔧 Technical Implementation Details

### Memory Management
- **Dynamic User Array**: Starts with space for 2 users, grows via `realloc()`
- **Dynamic Strings**: All strings (usernames, passwords, posts) are dynamically allocated
- **Linked List Posts**: Each user maintains a linked list of posts with dummy header node

### Error Handling
- **Input Validation**: Checks for proper spacing and format in commands
- **User Existence**: Validates usernames during signup and user lookup
- **Post ID Validation**: Ensures numeric post IDs and existence before operations
- **Memory Safety**: Proper allocation/deallocation to prevent memory leaks

### Performance Characteristics
- **User Lookup**: O(n) linear search through user array
- **Post Operations**: O(n) traversal of user's post linked list
- **Memory Usage**: Grows dynamically based on users and posts

## 🤝 Contributing

This project is primarily for educational purposes. However, contributions that improve code clarity, add features, or fix bugs are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add some improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Create a Pull Request
