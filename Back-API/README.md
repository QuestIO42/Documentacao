#  Docs API

##  Endpoints

- **User**
[/user](./user.md)
/user/{id}
/user/update/{id}
/user/delete/{id}

- **Auth**
/auth/login
/auth/register
/auth/token/refresh
/auth/logout
/auth/clear-cookie

- **Course**
/course
/course/{id}
/course/create
/course/update/{id}
/course/delete/{id}

- **SchoolRoom**
/schoolroom
/schoolroom/{id}
/schoolroom/create
/schoolroom/update/{id}
/schoolroom/delete/{id}

- **Post**
/post
/post/{id}
/post/user/{idUser}
/post/schoolroom/{idSchoolroom}
/post/create
/post/update/{id}
/post/delete/{id}

- **Comment**
/comment
/comment/{id}
/comment/post/{idPost}
/comment/create
/comment/update/{id}
/comment/delete/{id}
