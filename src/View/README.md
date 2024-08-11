# Views

Views should be extensions of the _primary_ ViewModel that represents the activity being performed, although a view can interact with
multiple ViewModels. 

```
import SwiftUI

extension SomeViewModel {

  // A view that works on various devices (tailored using conditional macros, etc)
  struct SomeView : View {
  }

  // A view for a specific device and/or form-factor
  struct SomeMacSpecificView : View {
  }

  // Common view elements 
  struct SharedView : View {
  }

}
```


