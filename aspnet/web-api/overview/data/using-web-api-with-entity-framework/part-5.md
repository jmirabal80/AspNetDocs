---
uid: web-api/overview/data/using-web-api-with-entity-framework/part-5
title: "Create Data Transfer Objects (DTOs) | Microsoft Docs"
author: MikeWasson
description: ""
ms.author: riande
ms.date: 06/16/2014
ms.assetid: 0fd07176-b74b-48f0-9fac-0f02e3ffa213
msc.legacyurl: /web-api/overview/data/using-web-api-with-entity-framework/part-5
msc.type: authoredcontent
---
# Create Data Transfer Objects (DTOs)

[Download Completed Project](https://github.com/MikeWasson/BookService)

Right now, our web API exposes the database entities to the client. The client receives data that maps directly to your database tables. However, that's not always a good idea. Sometimes you want to change the shape of the data that you send to client. For example, you might want to:

- Remove circular references (see previous section).
- Hide particular properties that clients are not supposed to view.
- Omit some properties in order to reduce payload size.
- Flatten object graphs that contain nested objects, to make them more convenient for clients.
- Avoid "over-posting" vulnerabilities. (See [Model Validation](../../formats-and-model-binding/model-validation-in-aspnet-web-api.md) for a discussion of over-posting.)
- Decouple your service layer from your database layer.

To accomplish this, you can define a *data transfer object* (DTO). A DTO is an object that defines how the data will be sent over the network. Let's see how that works with the Book entity. In the Models folder, add two DTO classes:

[!code-csharp[Main](part-5/samples/sample1.cs)]

The `BookDetailDto` class includes all of the properties from the Book model, except that `AuthorName` is a string that will hold the author name. The `BookDto` class contains a subset of properties from `BookDetailDto`.

Next, replace the two GET methods in the `BooksController` class, with versions that return DTOs. We'll use the LINQ **Select** statement to convert from Book entities into DTOs.

[!code-csharp[Main](part-5/samples/sample2.cs)]

Here is the SQL generated by the new `GetBooks` method. You can see that EF translates the LINQ **Select** into a SQL SELECT statement.

[!code-sql[Main](part-5/samples/sample3.sql)]

Finally, modify the `PostBook` method to return a DTO.

[!code-csharp[Main](part-5/samples/sample4.cs)]

> [!NOTE]
> In this tutorial, we're converting to DTOs manually in code. Another option is to use a library like [AutoMapper](http://automapper.org/) that handles the conversion automatically.
> 
> [!div class="step-by-step"]
> [Previous](part-4.md)
> [Next](part-6.md)
