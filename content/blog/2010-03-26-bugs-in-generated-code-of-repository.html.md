--- 
title: "Bugs in the generated code of Repository Factory for Visual Studio 2008" 
date: '2010-03-26T09:54:00.001-05:00' 
tags: 
modified_time: '2010-03-26T10:36:04.870-05:00' 
thumbnail: http://lh4.ggpht.com/\_R1exOFT\_lVs/S6zKqTtOmDI/AAAAAAAAAHY/5GpqcMKnLVg/s72-c/tables\_thumb1.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-7204544663646247028
blogger_orig_url: http://ebeid-soliman.blogspot.com/2010/03/bugs-in-generated-code-of-repository.html
---

If you are considering using repository factory for visual studio 2008
in your next project, please be aware that it had 2 bugs in code
generation. These are in the generated Remove method in the repository
classes of the DAL. This happens only if the corresponding table is a
bridge table that links two tables together.

If you had simple three tables in your database like the following:

[<img src="http://lh4.ggpht.com/_R1exOFT_lVs/S6zKqTtOmDI/AAAAAAAAAHY/5GpqcMKnLVg/tables_thumb1.jpg?imgmax=800" title="tables" width="392" height="273" alt="tables" />](http://lh4.ggpht.com/_R1exOFT_lVs/S6zKpa2im8I/AAAAAAAAAHU/d7SDYuqwKLE/s1600-h/tables3.jpg)

The generated Remove method in User\_RoleRepository class will be like
the following:

    public void Remove(System.Int32 role_IDSystem.Int32 user_ID)

    { 

       IDeleteFactory<DeleteUser_RoleIdentity> deleteFactory = new 

       User_RoleDeleteFactory(); 

       try 

         { 

          DeleteUser_RoleIdentity deleteUser_RoleIdentity = new 

             DeleteUser_RoleIdentity(role_IDField, user_IDField); 

          base.Remove(deleteFactory, deleteUser_RoleIdentity); 

         } 

       catch (SqlException ex) 

         { 

          HandleSqlException(ex, deleteFactory); 

         }            

        }

  
  

-   The parameter separator had been omitted
-   The param eters passed to deleteUser\_RoleIdentity had been suffixed
    by “Field” although it should be the same name as the passed
    parameters.

  
  

Take care of these 2 bugs in the generated code, you have to correct
them in every class.
