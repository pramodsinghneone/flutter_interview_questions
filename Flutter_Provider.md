
**1. What is Provider?**

  **Ans -**

    - Provider is a Flutter architecture that provides the current data model to the place where we currently need it. It contains some data and notifies observers when a change occurs. 
    - In Flutter SDK, this type is called a ChangeNotifier. For the object of type ChangeNotifier to be available to other widgets, we need ChangeNotifierProvider. 
    - It provides observed objects for all of its descendants. The object which is able to receive current data is Consumer, which has a ChangeNotifier instance in the parameter of its build function that can be used to feed subsequent views with data.

**2. What we have to write on Root Widget for accessing the properties to its child?**
	
  **Ans -**
  
    - MultiProviders 
**3. Common Property Between GetX,Provider,Bloc?**

  **Ans -**
  
  - Bloc - BlocProvider.of(context)
  - Provider - Provider.of(context)
  - GetX  - Get.find();

**4. What is ChangeNotifierProvider,MultiProviders?**
	
  **Ans -**
  
	ChangeNotifierProvider - 
    - ChangeNotifierProvider is the widget that provides an instance of a ChangeNotifier to its descendants.
    - Which is responsible for rendering within the UI the changes that happened in ViewModel class data.
    -  It comes from the provider package.
    - ChangeNotifierProvider listens to a ChangeNotifier. Not only listening but it also expose ChangeNotifier to its descendants and rebuilds dependents when the state changes.
	MultiProviders - 
    - A provider that merges multiple providers into a single linear widget tree. 
    - It is used to improve readability and reduce boilerplate code of having to nest multiple layers of providers.
		MultiProvider(
      			providers: [
        		Provicer<Person>(create: (_) => Person(name: 'Yohan', age: 25)),
			Provider<String>(create: (context) => Home().fetchAddress),
		      ],
    - 

	
**5. What is Consumer Widget?**
	 
   **Ans -**
   
    - Consumer can be understood as a widget holding the reference of ViewModel Class that continually listens for any changes and rebuilds the child widget over which it has been wrapped.
	
		  Consumer<ModelClass>(
      			builder: (context, model, Widget? child) => View(model: model),
    		),

**6. What are the parameters in callbacks for Consumer Widgets?**
	 
   **Ans -**
   
    - builder: (context, model, Widget? child) 
    - Parameters. - BuildContext , Model Class, Widget

**7. Can We use setState with Consumer Widget ?if Yes/No,they Why?**
	 
   **Ans -** 
   
    - Yes we can use but optionally we don’t have to use because SeState will rebuild whole widget unnecessary that is very expensive to use. 
    - Consumer will only rebuild the particular widget on which it is using.


**8. What is context.read(), context.wacth() methods?**
	
  **Ans -** 
  
  **Context.read()-** 
  
    - context.read<ModelClass>() replaces Provider.of<ModelClass>(context, listen: false).
    - which returns T without listening to it. It is used for adding events on button click. 

  **Context.watch() -** 

    - context.watch<ModelClass>() replaces Provider.of<ModelClass>(context).
    - context.watch<ModelClass>(), which makes the widget listen to changes on ModelClass.

**9. How can we achieve Dependency Injection in Provider?**
	
   **Ans -** 
  
    - Add MultiProvider widget to root of the widgets
    - Define the respective model class with ChangeNotifierProvider inside Multiprovider.
    - Access with this syntax - Provider.of<ModelClass>(context) or context.watch<ModelClass>();

**10. How can we listen changes without Consumer widget ?**
	
  **Ans -**
    
  - Provider.of<ModelClass>(context) or ;
  - Context.watch<ModelClass>();

**11. What is ChangeNotifier?**
  
  **Ans -** 
  
  - ChangeNotifier can be understood as a class extended by other classes to provide notification if there is any change in the data of the class.
  - It notify the changes using notifyListeners() method.

**12. What is the name of the method which provides listenable objects ?**
	
  **Ans -**  notifyListeners() 

**13. Can you tell the differences between Provider and Bloc?**

  **Ans -** 
  
    - The difference is that BlocBuilder listens to the bloc and states and fetches the model on every change to rebuild the widget. But Consumer listens as soon as notifyListeners() executes inside the provider class.
  
**14 . Provider has some limitation so, what is the solution which overcome this limitations?**
	
  **Ans -** 
     Riverpod
