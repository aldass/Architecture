- Conventions
  - Repository Names
    - Preferably no spaces, use a `-` (dash, hyphen) as a substitute
  - Branch Names
    - All attempts will be made to automate the creation of branches for users based on the initiative/epic/story/task|bug|hotfix
    - Pattern should be as follows:
      - `[category]`/`[ticket key]`/`brief description`
      - Where:
        - `[category]` can be `initiative`, `epic`, `story`, `task` or `bug`.
           Note in rare cases `category` can also be `misc` for miscellaneous code mutations 
        - `[ticket key]` is the ALM (Jira, Azure DevOps) Id. e.g. `XYZ-1024` for Jira or `1024` for Azure DevOps
        - `brief description` preferably 7 or less words
  - Names: Classes, Modules, Functions, Methods, Variables, Name Spaces, Folders and Files 
    - [Pascal Case for C#](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)
    - Camel Case for JavasSript/TypeScript/JSON
      - [Google JavasSript Style Guide](https://google.github.io/styleguide/jsguide.html)
      - [Google JSON Style Guide](https://google.github.io/styleguide/jsoncstyleguide.xml)
    - [.Net Core Naming Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/naming-guidelines)
    - [Angular Style Guide](https://angular.io/guide/styleguide)
  - Code Formatting (C#, JavaScript, 
    - Strongly suggest using [Prettier](https://prettier.io/). It has plug-ins for all the common IDEs
  - Pull Requests
    - We'll use Pull Requests templates to drive better detail
- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
  - _**S**ingle Responsibility principle_ - A class should only have a single responsibility, that is, only changes to one part of the software's specification should be able to affect the specification of the class.
  - _**O**pen–Closed principle_ - "Software entities ... should be _open_ for extension, but _closed_ for modification."
  - _**L**iskov Substitution principle_ - "Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program." See also design by contract.
  - _**I**nterface Segregation principle_ - "Many client-specific interfaces are better than one general-purpose interface."
  - _**D**ependency Inversion principle_ - One should "depend upon abstractions, not concretions." Use _Dependency Injection_ to wire in the concretions.
- [Composition over Inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance)
  - Example:
    - For [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) patterns please **don't** do something like this:
      ```
      namespace Repo...
      public abstract class BaseCrudRepo<T> {
        public T Create(T o) {...}
        public List<T> Read() {...}
        public T Update(T o) {...}
        public T Delete(T o) {...}
      }
      public class MyRepo: BaseCrudRepo {...}
      ```
      ...instead **do** this:
      ```
      namespace Repo...
      public interface Create<T> { T Create(T o); }
      public interface Read<T> {
        List<T> GetAll();
        T Get(T o);
        List<T> Search(Object o);
      }
      public interface Update<T> { T Update(T o); }
      public interface Delete<T> { T Delete(T o); }
      }
      public class MyRepo: Create, Read, Update, Delete
      ```

- [Monad](https://en.wikipedia.org/wiki/Monad_(functional_programming))
- [NodaTime (for anything Date or Time related in C#)](https://www.nuget.org/packages/NodaTime)
  - [Old but good write up about it](https://msdn.microsoft.com/en-us/magazine/jj991981.aspx)
  - [Storing UTC is not a silver bullet - Jon Skeet](https://codeblog.jonskeet.uk/category/nodatime/)
- Unit Tests
  - [Angular](https://angular.io/guide/testing)
    - TBD.1
    - TBD.2
    - TBD.3
  - [DotNet](https://docs.microsoft.com/en-us/dotnet/core/testing/)
    - [Moq - Mocking data for testing](https://www.nuget.org/packages/moq/)
    - [xUnit](https://www.nuget.org/packages/xunit)
      - [xBehave.net - Natural Language Test Syntax](https://xbehave.github.io/)
        - [For DotNet Core 2.x](https://www.nuget.org/packages/Xbehave.Core/)
        - [For .Net Framework 4.x](https://www.nuget.org/packages/Xbehave/)
      - [Xunit.Gherkin.Quick](https://xbehave.github.io/)
    - TBD.1
    - TBD.2
    - TBD.3
