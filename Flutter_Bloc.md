

1. **What is bloc**

	**Ans** - 
    -  Bloc stands for Business Logic Component.
    - Bloc separates the UI from the business logic. When we build an application without any architecture, we most probably write our logic directly inside the UI. But when we use Bloc we have to write the business logic in a separate file, i.e separated from UI and then we link it to the UI.
    - Bloc makes the application easily testable, fast, reactive.


2. **Explain the Layers of Bloc**

	**Ans** - 
    - Using Bloc, we can easily seperate the application into multiple layers, first we would have the presentation layer which would contain the UI/Views/widgets, then the business logic layer (Bloc) which will take care about the state changes and will have a dependency on the data access layer.
    - The data access layer will be the last layer in the application, it can contain a repository class which will act as an abstract class above the data access object classes.


3. **How Bloc is differ with other reactive framework**

	**Ans** - 
    - BLoC is a reactive programming framework that uses streams to emit data in response to events. This is different from other frameworks like ReactJS, which use a more traditional event-based model.
    - The advantage of using a stream-based approach is that it allows for a more declarative style of programming, where the developer does not need to worry about explicitly handling events.


4. **Common property between Bloc, Provider, GetX**

	**Ans** - Dependency Injection 
		Bloc - BlocProvider.of(context)
		Provider - Provider.of(context)
		GetX  - Get.find();

5. **Can we use setState while using BlocBuilder? If No/Yes then Why?**

	**Ans** - Yes we can use but optionally we don’t have to use because SeState will rebuild whole widget unnecessary that is very expensive to use. 
		BlocBuilder will only rebuild the particular widget on which it is using.


6. **What are the common Bloc patterns widgets while using the bloc?**

	**Ans** - 
    - Some common Bloc patterns that are used when developing an             application in Flutter include the following:
    - The use of a StreamController to emit events that will be processed by the Bloc. -The use of a StreamBuilder to listen for events emitted by the StreamController and rebuild the UI in response to those events. -The use of a Sink to provide input to the Bloc from outside sources.
    - BlocBuilder
    - BlocListener
    - BlocConsumer


7. **What is difference between BlocListener,BlocConsumer,BlocBuilder?**

	**Ans** - 
	BlocBuilder - 
    - BlocBuilder is a Flutter widget which requires a Bloc and a builder function. BlocBuilder handles building the widget in response to new states. BlocBuilder is very similar to StreamBuilder but has a more simple API to reduce the amount of boilerplate code needed. The builder function will potentially be called many times and should be a pure function that returns a widget in response to the state.

	BlocListener - 
    - BlocListener is a Flutter widget which takes a BlocWidgetListener and an optional Bloc and invokes the listener in response to state changes in the bloc. It should be used for functionality that needs to occur once per state change such as navigation, showing a SnackBar, showing a Dialog, etc...
    - listener is only called once for each state change (NOT including the initial state) unlike builder in BlocBuilder and is a void function.

	BlocConsumer
    - BlocConsumer exposes a builder and a listener. BlocConsumer works similarly to nested BlocListener and BlocBuilder, but with less boilerplate.
    - BlocConsumer should only be used when both rebuilding the UI and performing additional reactions to state changes in the bloc are required.


8. **What is MultiBlocProvider and difference between BlocProvider?**

	**Ans** - 
	MultiBlocProvider - 
    - MultiBlocProvider is a Flutter widget that merges multiple BlocProvider widgets into one. MultiBlocProvider improves the readability and eliminates the need to nest multiple BlocProviders. 
    - Difference - BlocProvider is a single provider widget I.e.which provides only single bloc or cubit.



9. **What is MultiRepositoryProvider and difference between RepositoryProvider?**

	**Ans** - 
	MultiRepositoryProvider - 
    - MultiRepositoryProvider is a Flutter widget that merges multiple RepositoryProvider widgets into one. MultiRepositoryProvider improves the readability and eliminates the need to nest multiple RepositoryProvider.
    - Difference - Repository is single repository provider.

10. **What is hydrated bloc?**

	**Ans** - 
    - Hydrated BLoC is an extension of the bloc package which provides out-of-the-box persistence for our blocs or cubits.
    - It persisting the state of our applications.
    -  It makes our applications easier for users to make use of, especially when they do not have to re-enter certain data every time they launch our application.
    - For instance, most users would prefer using a weather application that by default, shows the weather situation of your recent location or the last location you checked, rather than having to manually search your location anytime they open it.
    - If you are using the BLoC library for state management in Flutter, then you do not need to write a lot of code to save and restore your state. You can simply make use of the hydrated BLoC from the BLoC library.



11. **What is blocObserver ?**

	**Ans** - 
    - BlocObserver is a abstract class for monitoring BloC instances behavior. This me**Ans** we can track anytime an event is triggered or a state is emitted.


12. **What are the method it overrides and use of it?**

	**Ans** - 
	onChange() - 
    - In order to see the change when a new state is emitted.
    - A Change represents the change from one State to another.
    - A Change consists of the currentState and nextState.

	onTransition - 
    - If you want to observe a bloc whenever a new event is added and a new state is added, you can override onTransition method.
    - A tr**Ans**ition occurs when a new event is added and a new state is emitted from a corresponding EventHandler executed.
    - onTronTransition is called before a Bloc's state has been updated.

	onError - 
    - To track a bloc's error whenever it happens.

	onEvent -
    - Whenever an event is added to the Bloc this method is triggered.



13. **Tell me the difference between StreamBuilder and BlocBuilder?**

	**Ans**- 
	StreamBuilder - 
    - It takes stream as a input
    - It has a builder callback with BuildContext and AsyncSnapshots parameters.
    - AsyncSnapshots provide different enum values like waiting, done, active, none.
    - AsyncSnapshots provides data property if hasData property is true.

	BlocBuilder - 
    - BlocBuilder is a Flutter widget which requires a Bloc and a builder function. BlocBuilder handles building the widget in response to new states. 
    - BlocBuilder is very similar to StreamBuilder but has a more simple API to reduce the amount of boilerplate code needed.
    - The builder function will potentially be called many times and should be a pure function that returns a widget in response to the state.

14. **What is Cubit?**

	**Ans** - 
    - Cubit is a lightweight state management solution. It is a subset of the bloc package that does not rely on events and instead uses methods to emit new states.
    - Every cubit requires an initial state which will be the state of the cubit before emit has been called. The current state of a cubit can be accessed via the state getter.


15. **Why is the cubit comes in the picture?**

	**Ans** - 
    - Bloc contains some boilerplate code
    - For reducing the boilerplate code cubit is used.
    - Cubit is more simplified in which we only have to define functions, and states.


16. **Can we use events in cubit?if No then Why?**

	**Ans** - NO. Because it exposes direct functions.


17. **Tell me the flow for calling api or some other functions using bloc and cubit.**

	**Ans** - 
	**Bloc flow** - 
    - In bloc we use Events and State for communicating for API calls.
    - BlocProvider.of<BlocName>(context).add(EventName) for adding event into bloc we have to use this signature.
    - Then it will return the processed States to UI.

	**Cubit flow** -
    - In cubit we  use  instance of cubit in direct function mode.
    - So in that we don’t have to use events for adding into cubit.
    - Function communicate with Repository and return with States to UI.

18. **What is RxDart and how is differ with Bloc?**

	**Ans** - 
	RxDart - 
    - RxDart is an implementation of the popular reactiveX api for asynchronous programming, leveraging the native Dart Streams api.
    - RxDart is a reactive functional programming library for Dart language, based on ReactiveX Api.
    - RxDart is not differ with Streams but  it offers several additional Subjects, Stream Classes and Extension Methods on the Stream Classes (Operators of Rx).
    - In Dart, if we’ve to send data, error and done events to its stream we use StreamController but, in RxDart we have to use Subject which is the same as StreamController but with additional stuff.
    - all the subjects of RxDart is similar to broadcast StreamController which me**Ans** we can listened to the subject’s stream as many time as we want.
    - Types of Subjects
        - BehaviorSubject
        - PublishSubject
        - ReplaySubject

	Difference - Bloc does not support subjects classes but it supports Streams.


19. **What is the buildWhen  Blocbuilder widget?**

	**Ans** - 

	**buildWhen** - 
    - buildWhen parameter takes the previous bloc state and current bloc state and returns a boolean. 
    - If buildWhen returns true, builder will be called with state and the widget will rebuild.

20. **In buildWhen if the provided state is false then builder will call or not?**

	**Ans** - If buildWhen returns false, builder will not be called with state and no rebuild will occur.


21. **What is context.Read() and context.Watch() and context.Select()?**

	**Ans** - 
	
	**Context.Read()** - 
    - context.read<T>() looks up the closest ancestor instance of type T and is functionally equivalent to BlocProvider.of<T>(context). context.read is most commonly used for retrieving a bloc instance in order to add an event within onPressed callbacks.

	**Context.watch()** - 
    - Like context.read<T>(), context.watch<T>() provides the closest ancestor instance of type T, however it also listens to changes on the instance. It is functionally equivalent to BlocProvider.of<T>(context, listen: true).

	**Context.select()** - 
    - Just like context.watch<T>(), context.select<T, R>(R function(T value)) provides the closest ancestor instance of type T and listens to changes on T. Unlike context.watch, context.select allows you listen for changes in a smaller part of a state.
