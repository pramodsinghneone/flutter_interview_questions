**1. What is GetX?**

  **Ans -**

    - GetX is an extra-light and powerful solution for Flutter. It is a microframework combined with route management and dependency injection
    - Three pillars of GetX-
    - Route Management
    - Dependency Management
    - State Management


**2. What is GetBuilder?**

  **Ans -**

    - GetBuilder is use for simple state management. 
    - Wrap the widget which we want to rebuild with GetBuilder and it will listen changes from controller class whenever update() called.

**3. Is GetBuilder reactive approach or simple approach?**

**Ans -**

    - Simple approach.


**4. How can we achieve reactive approach in GetX?**

**Ans -** 

    - by using Obx(()=>) widget


**5. What is common properties between GetX,Bloc,Provider?**

**Ans - Dependency Injection**

  - Bloc - BlocProvider.of(context)
  - Provider - Provider.of(context)
  - GetX  - Get.find();

**6. How. Can we achieve Dependency Injection in GetX?**

**Ans -** 

  - First we have to registered 
    Controller controller = Get.put(Controller());
  - Then we can use 
  - Get.find<Controller>();  
  - It will give us the instance controller.

**7. What are  the methods we can override in GetXController?**
 
**Ans -**

  - onInit()
  - onReady()
  - onClose()
  - onDispose()


**8. What is difference between Get.putAsync() and Get.lazyPut()?**

	**Ans -** 

	  Get.putAsync() - 
        - When using SharedPreferences or databases, we need to work with dependencies asynchronously. We can use Get.putAsync for that.

			  Get.putAsync<SharedPreferences>(() async {
			  final prefs = await SharedPreferences.getInstance();
			  await prefs.setString('name', 'Batman');
			  return prefs;
			  }, tag: 'tagsAreEverywhere', permanent: true);
	
			  Get.find<SharedPreferences>().getString('name');

  	Get.lazyPut() - 
        - As the name suggests, it lazy loads the dependencies, which basically means that the dependencies will be created immediately, but will be loaded to memory only when Get.find is called for the first time. 
		
			  class HomeBinding implements Bindings {
  			@override
	  		void dependencies() {
		  	Get.lazyPut<Controller>(() => Controller()); 
			  	}
  			}

        - Get.lazyPut loads dependencies only one time, which means that if the route gets removed, and created again, Get.lazyPut will not load them again. This default behavior might be preferable in some cases while for others, we have the fenix property.
		
			  Get.lazyPut(() => Controller(), fenix: true);
  
**9. How can we achieve listenable variables in GetX controller class?**

**Ans -**
	
	- obs or Rx with Data Type or Object

**10. What is the root widget we write in GetX?**

**Ans - GetMaterialApp**

**11. In the latest update GetX we can also handle UI state using which mixin? what are the status we can use of that mixin?**

**Ans. -** 

	StateMixin<T> 
- The change() method change the State whenever we want
- change(data, status: RxStatus.success());
- Following are the status 
	- RxStatus.loading();
	- RxStatus.success();
	- RxStatus.empty();
	- RxStatus.error('message');

**12. What is difference between GetBuilder,StreamBuilder,BlocBuilder?**

**Ans -** 

GetBuilder - 

- It is used to rebuild the widget whenever the data updates.
- Data updated whenever the update() called from controller class in GetX.

StreamBuilder - 

- StreamBuilder is a widget that builds itself based on the latest snapshot of interaction with a stream.
- It has a builder arguments with two parameters whose types in order are BuildContext and AsyncSnapshot<T>.
- It has a stream arguments which accepts the stream type data.
- AsyncSnapshot has different property with None,Waiting,Done,Active for handling data on UI.

BlocBuilder - 

    - BlocBuilder is a Flutter widget which requires a Bloc and a builder function. BlocBuilder handles building the widget in response to new states. 
    - BlocBuilder is very similar to StreamBuilder but has a more simple API to reduce the amount of boilerplate code needed. 
    - The builder function will potentially be called many times and should be a pure function that returns a widget in response to the state.


**13. What is Fenix and Permanent property in GetX?**

**Ans -** 

  - Fenix -
    - Get.lazyPut loads dependencies only one time, which means that if the route gets removed, and created again, Get.lazyPut will not load them again. This default behavior might be preferable in some cases while for others, we have the fenix property.
    - Get.lazyPut(() => Controller(), fenix: true);
    - It will still delete the dependencies, but it will be able to re-initialize them, when the route is back in stack.

	Permanent - 
    - By default, the dependencies will be deleted if the route using Get.put is removed from the navigation stack. You may want to prevent this and keep the dependencies in memory for the entire app session. You can do that using permanent property.
    - Get.put(Controller(), permanent: true);


**14. What is Binding? Use of Binding?**

**Ans -** 

Binding - 

    - Bindings are classes where we can declare our dependencies and then ‘bind’ them to the routes.
    - We can separate the dependencies to other classes and call the use the instances using Get.find();

		class HomeBinding implements Bindings {
			@override
			void dependencies() {
				Get.put<Controller1>(Controller1());
				Get.put<Controller2>(Controller2());
				}
			}
	
		getPages: [
	  	GetPage(
		  name: '/',
	    	page: () => HomeView(),
	    	binding: HomeBinding(),
		  ),
		]
	
     Use of Binding - 
     - Totally decouple the controller from the UI.
     - Provide the instances of controller to the UI using Get.find<Controller>();

**15. What is difference between Get.put() and Get.lazyPut()?**
	
   **Ans -** 

     Get.put() - 
   	- The controller is created on the memory when the code is executed.

     Get.lazyPut() - 
   	- The controller is created on the memory when the controller is used.

**16. How navigation works in GetX without context?**
	
   **Ans -** 
	
	- It is extending NavigatorState class of the framework.
	
	
**17. What is difference between ValueBuilder and ObxValue?**
	
  **Ans -**  
	
  ValueBuilder - 
   - It rebuild UI whenever it gets updated values.
   - It is simple approach.

  ObxValue - 
  - It is reactive approach.
  - It listen data in asynchronous manner. 

**18. How you will connect to network services using GetX?**

  **Ans -**
	
  - We will extends GetConnect class.
  - Use the GET/POST/PUT/DELETE/SOCKET methods to communicate with your Rest API or websockets.



