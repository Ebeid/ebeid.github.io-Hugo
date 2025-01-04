---
title: 'Bugs in the generated code of Repository Factory for Visual Studio 2008'
date: 2010-03-26T09:54:00.001-05:00
draft: false
url: /2010/03/bugs-in-generated-code-of-repository.html
---

If you are considering using repository factory for visual studio 2008 in your next project, please be aware that it had 2 bugs in code generation. These are in the generated Remove method in the repository classes of the DAL. This happens only if the corresponding table is a bridge table that links two tables together.

If you had simple three tables in your database like the following:

[![tables](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj_6EIe6Yun55OC-FgoqO1t63gNgNGj4Wk-GwrKnNx1Gn5EhZ008EOmZ6G5TLyPFQUcnsqI4UF3vYaQsPqr-6q3NLwInthmWecem95l726tf3tpu9qMkX1qXlJPyzpdtyVyqnhSRZICeg/?imgmax=800 "tables")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjzSGl_iPCKrFnmxYBf9es9LPp6ZrlPshsizeN7TRqPtCFESYL1LIL5BH-t4YlQrVYph1hCxY6Ht-5Dlf8dHyKnUUxUsqGHBmvVy902TSxBwFwtc_SWUACVOrE8ZEiy1muW43_ctDoo_g/s1600-h/tables3.jpg)

The generated Remove method in User\_RoleRepository class will be like the following:

```
```
public void Remove(System.Int32 role\_IDSystem.Int32 user\_ID)  

``````
{   

``````
   IDeleteFactory<DeleteUser\_RoleIdentity> deleteFactory = new   

``````
   User\_RoleDeleteFactory();   

``````
   try   

``````
     {   

``````
      DeleteUser\_RoleIdentity deleteUser\_RoleIdentity = new   

``````
         DeleteUser\_RoleIdentity(role\_IDField, user\_IDField);   

``````
      base.Remove(deleteFactory, deleteUser\_RoleIdentity);   

``````
     }   

``````
   catch (SqlException ex)   

``````
     {   

``````
      HandleSqlException(ex, deleteFactory);   

``````
     }              

``````
    }  

```
```  
  

  
*   The parameter separator had been omitted
  
  
*   The parameters passed to deleteUser\_RoleIdentity had been suffixed by “Field” although it should be the same name as the passed parameters.
  

  
  

Take care of these 2 bugs in the generated code, you have to correct them in every class.