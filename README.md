# iv-hafta-odevi
*  Geri dönen bilgiye göre yeşil renkte onay mesajı gösterilmesi. (örneğin:view bag)

*  AddMVC - AddMVCCore - AddDateAnnotations nedir? Nerelerde eklenmelidir?

 * Shanpshot nedir? nasıl değişir? neden alınır?

*  Jquery Calender--> [Datapicker](https://jqueryui.com/datepicker/) --> DueAt'i takvim tipinde eklemek nasıl yapılır? Araştırınız. (DateTimeUffset tipinden atamalar oluşucak)

*  First- FirstOrDefault ve Single- SingleOrDefault nedir? Aralarındaki farkı araştırınız.

*  En kısa null check nasıl yapılır?

* partial view nedir?

* Farklı authentication bulup,aynı işleri farklı yollar ile yapanları araştırınız.

* Ödev- Razor Pages/MVC Projects karşılaştırmasını yapınız.


# Answers

## success message with ViewBag
``
ViewBag.SuccessMessage = "<p>Success!</p>"; // Controller
@ViewBag.SuccessMessage //View
``
## success message with TempData
``
TempData["Message"] = "Operation successful!"; // Controller
@TempData["Message"] // View
``
## AddMvc
AddMvc() which simply registers the entire kitchen sink of all the features. It gives you:

everything that AddControllersWithViews() does
everything that AddRazorPages() does

## AddMvcCore
AddMvcCore() registers all the core services required for the MVC application to work at all. We do not need to list them all, but pretty much everything related to the controller invocation pipeline gets activated there. These are low(er) level services, that only get customized when you are doing something quite complex or unusual (i.e. building a CMS). Some examples of them are: the controller activation services, the MVC options pipeline, application model provider infrastructure, action constraints, filter pipeline, model binder infrastructure, action result executors and a few more.
src: https://www.strathweb.com/2020/02/asp-net-core-mvc-3-x-addmvc-addmvccore-addcontrollers-and-other-bootstrapping-approaches/
## AddDataAnnotations
Data annotations (available as part of the System. ComponentModel. DataAnnotations namespace) are attributes that can be applied to classes or class members to specify the relationship between classes, describe how the data is to be displayed in the UI, and specify validation rules. 
src:https://www.infoworld.com/article/3543302/how-to-use-data-annotations-in-csharp.html#:~:text=Data%20annotations%20(available%20as%20part,UI%2C%20and%20specify%20validation%20rules.

## Snapshot 
The good article about to learn The Model Snapshot In Entity Framework Core
https://www.learnentityframeworkcore.com/migrations/model-snapshot#:~:text=Entity%20Framework%20Core.-,The%20Model%20Snapshot%20In%20Entity%20Framework%20Core,updated%20with%20each%20subsequent%20migration.

## DatePicker
Command calender library in Jquery. It is basic calendar example with DatePicker in jquery
https://www.tutorialspoint.com/jqueryui/jqueryui_datepicker.htm

## Single, SingleOrDefault, First and FirstOrDefault

### Single
It returns a single specific element from a collection of elements if element match found. An exception is thrown, if none or more than one match found for that element in the collection.

### SingleOrDefault
It returns a single specific element from a collection of elements if element match found. An exception is thrown, if more than one match found for that element in the collection. A default value is returned, if no match is found for that element in the collection.
``
List<int> data = new List<int> { 10, 20, 30, 40, 50 };

//Try to get element at specified position
Console.WriteLine(data.ElementAt(1)); //result:20 

//Try to get element at specified position if exist, else returns default value
Console.WriteLine(data.ElementAtOrDefault(10)); //result:0, since default value is 0 

Console.WriteLine(data.First()); //result:10 
Console.WriteLine(data.Last()); //result:50

//try to get first element from matching elements collection
Console.WriteLine(data.First(d => d <= 20)); //result:10 

//try to get first element from matching elements collection else returns default value
Console.WriteLine(data.SingleOrDefault(d => d >= 100)); //result:0, since default value is 0 

//Try to get single element 
// data.Single(); //Exception:Sequence contains more than one element 

//Try to get single element if exist otherwise returns default value
// data.SingleOrDefault(); //Exception:Sequence contains more than one element 

//try to get single element 10 if exist
Console.WriteLine(data.Single(d => d == 10)); //result:10 

//try to get single element 100 if exist otherwise returns default value
Console.WriteLine(data.SingleOrDefault(d => d == 100)); //result:0, since default value is 0
``
### First
It returns first specific element from a collection of elements if one or more than one match found for that element. An exception is thrown, if no match is found for that element in the collection.

### FirstOrDefault
It returns first specific element from a collection of elements if one or more than one match found for that element. A default value is returned, if no match is found for that element in the collection.

src: https://www.dotnettricks.com/learn/linq/understanding-single-singleordefault-first-and-firstordefault#:~:text=When%20you%20want%20an%20exception,records%2C%20use%20Single%20or%20SingleOrDefault.&text=When%20you%20always%20want%20one,contains%20no%20record%2C%20use%20FirstOrDefault.

## How to make shortest Null check?
Use operators ?? and ??= For example;

``
List<int> numbers = null;
int? a = null;

(numbers ??= new List<int>()).Add(5);
Console.WriteLine(string.Join(" ", numbers));  // output: 5

numbers.Add(a ??= 0);
Console.WriteLine(string.Join(" ", numbers));  // output: 5 0
Console.WriteLine(a);  // output: 0
``
src:https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-coalescing-operator

## What is PartialView
Partial view in ASP.NET MVC is special view which renders a portion of view content. It is just like a user control of a web form application. Partial can be reusable in multiple views. It helps us to reduce code duplication. In other word a partial view enables us to render a view within the parent view.

tutorial: https://www.c-sharpcorner.com/UploadFile/ff2f08/partial-view-in-mvc/

## Compare to Razor pages and MVC
### What is Razar Pages? 
A Razor Page is very similar to the view component that ASP.NET MVC developers are used to. It has all the same syntax and functionality.
The key difference is that the model and controller code is also included within the Razor Page itself. It is more an MVVM (Model-View-ViewModel) framework. 
### What is MVC?
The Model-View-Controller (MVC) is an architectural pattern that separates an application into three main logical components: the model, the view, and the controller. Each of these components are built to handle specific development aspects of an application. MVC is one of the most frequently used industry-standard web development framework to create scalable and extensible projects.
### Comparison
The MVC view part of the code is exactly the same except the Razor Page has “@page” in it.
ManagePageModel has OnGetAsync and OnPostAsync which replaced the two MVC controller “ManagePage” actions.
ManagePageModel includes my two properties that were in the separate PageClass before.
In MVC for an HTTP POST, you pass in your object to the MVC action (i.e. “ManagePage(int id, PageClass page)”). With a Razor Page, you are instead using two-way data binding. To get Razor Pages to work correctly with two-way data binding I had to annotate my two properties (PageDataID, Title) with [BindProperty]. My OnPostAsync method only has a single input of the id since the other properties are automatically boun.
src: https://stackify.com/asp-net-razor-pages-vs-mvc/#:~:text=A%20Razor%20Page%20is%20very,%2DView%2DViewModel)%20framework.
