# Swift/SwiftUI Reference Implementation of the MVVM design pattern

## MVC vs MVVM
MVC is basically a mediator pattern where the Controller has knowledge of both the Model and View. As a result, if the View changes 
the Controller also needs to change. Also, if there are multiple implementations of a View (for different devices/form-factors) then 
the Controller needs to know about them. Obviously there are ways to modularize/structure the controller to mitigate this, but 
it still complicates the Controller - and also spreads knowledge abou the device/form-factor of the UI across two major components.


```
            +---------------+
            |   Controller  |
            +---------------+
               /         \
         +---------+   +--------+
         |  Model  |   |  View  |
         +---------+   +--------+
```

MVVM is a layered patern where the layer above only knows about the layer below it (perhaps with some common domain types bleeding 
through to the top layer.

```
       +--------+       | The view is the driver of the application, it essentially acts as a presenter of the ViewModel for
       |  View  |       | a specific user interface, form-factor, etc. So there might be different implementations of for phone, 
       +--------+       | desktop, web user interfaces, all able to share the ViewModel. They should know little-to-nothing about the
           |            | model layer other than possibly fundamental data types. The view model only directly persists view specific
           |            | data, such as display preferences, etc.
           |
    +-------------+     | The ViewModel is a logical, view-agnostic model of the information and behaviour of the application. So it 
    |  ViewModel  |     | knows what the application does, but it doesn't know how this behaviour is actually presented to the user.
    +-------------+     | In other words, the ViewModel contains the _application logic_ of the application. It only knows about
           |            | the domain model below, which persists business data and provides business logic. The ViewModel itself
           |            | only persists application-specific data. 
           |
      +---------+       | The Model is a logical, appliation-agnostic model of the information and behavior of the part 
      |  Model  |       | of the business domain that is relevant to the application (unless the domain model is shared accross multiple
      +---------+       | applications). In other words, the Model contains the _business logic_ of the domain needed for the application.
```

