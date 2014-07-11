componentview
=============

Component based Laravel4/Blade/View extension

What is componentview?

Componentview is like Blade on steroids; it is built on top of Blade so all your Blade templates will work with componentview.

Componentview adds one construct to the Blade syntax, not surprisingly it is called @component.  You add components to templates just like any Blade construct.

Components are a bit like Partial Views... again, on steroids.  While a partial view is essentially a macro, a component is an actual PHP object, so it can perform complex logic and can interact with other objects in your system (including other components).

Because components are processed in multiple passes (see below), they can also perform all of the functions that would otherwise require callback functions in Blade.

Another way to think about components is that they perform the function of an MVC Controller for a single visual element.  Because components are actual PHP objects, they offer: data hiding, abstraction, inheritance and encapsulation.  When your user interface gets complicated, as happens with many web applications, these benefits become increasingly valuable.

Components may, of course, be combined to create more complex components; using inheritance, these complex components can perform the same function as Blade macros.

Components are reusable; a library of basic components is included.  A scaffold generator is also included to help you build an administrative interface for your application very quickly.  Unlike other scaffold generators, componentviews are production ready; they are fully styled and interactive (using jQuery) right out of the box.  What's more, components are configurable and can be subclassed to tweak their behavior and/or appearance. 

How componentview works

Blade templates are rendered from beginning to end, in a single pass (rendering a Blade template may (or may not) require recompiling to cache).  Componentviews, on the other hand, are processed in multiple passes: 
  assemble - the component objects are created and connected to each other in a tree structure
  load - the components interact with models and collect whatever data they need
  precompile - the components interact with each other
  render - the components generate Blade code 

There's no free lunch

By definition, componentviews require a bit more processing than Blade templates.  Componentviews are designed to be as efficient as possible, but they are doing more work than simple templates.  If performance is absolutely paramount, then componentviews are probably not for you - at least not on the most performance critical pages.  Often though, many pages of a web application do not have such heavy use and view rendering is not the performance bottleneck.  There's a trade-off here: saving developer time versus saving view generation time.  I'm talking about a lot of programmer time and a tiny amount of extra processing time.  In many cases, saving a day or more of development time is worth a tenth of a second in page load time.  Examples of great applications for componentview include: prototyping, UI testing, administrative interfaces, applications that change frequently.  Unlike many prototyping tools, componentviews can be easily converted into more efficient templates (either Blade or pure PHP).
