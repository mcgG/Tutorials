# 

Dependency injection

Dependency injection is a software design pattern that implements Inversion of control for resolving dependencies. Formally, if object A depends on object B, object A must not create or import object B directly. Instead of this object A must provide a way for injecting object B. The responsibilities of objects creation and dependencies injection are delegated to external code - the dependency injector.



Popular terminology of dependency injection pattern:

*  Object A, that is dependant on object B, is often called - the client.
* Object B, that is a dependency, is often called - the service.
* External code that is responsible for creation of objects and injection of dependencies is often called - the dependency injector.





There are several ways of how service can be injected into the client:

* by passing it as \_\_init\_\_ argument \(constructor / initializer injection\)
* by setting it as attribute’s value \(attribute injection\)
* by passing it as method’s argument \(method injection\)



Dependency injection pattern has few strict rules that should be followed:

The client delegates to the dependency injector the responsibility of injecting its dependencies - the service\(s\).

* The client doesn’t know how to create the service, it knows only interface of the service. The service doesn’t know that it is used by the client.
* The dependency injector knows how to create the client and the service, it also knows that the client depends on the service, and knows how to inject the service into the client.
* The client and the service know nothing about the dependency injector.



Dependency injection pattern provides the following advantages:

* Control on application structure.
* Decreased coupling between application components.
* Increased code reusability.
* Increased testability.
* Increased maintainability.
* Reconfiguration of system without rebuilding.



