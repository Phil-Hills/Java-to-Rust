A Web application that converts Java-Code to Rust. By adding/converting Java to Rust frees up memory because there is no cache key eviction. Java has to do a lot of work to dertermine what memory is free, which can slow the program down. Rust is extremely fast and memorty efficient: with no runtime or garbage collector, it can power performance-critical services, run on embedded deices, and easily integrate with other languages. 
With the safety featrures pre-built into Rust is what makes this conversion feasible, because there is no Garbage Collector(GC)in Rust. 


## How to use


# Crate maven_toolbox


use maven_toolbox::{default_impl::*, *};

// the artifact's GAV
let artifact = ArtifactFqn::pom(
    "com.walmartlabs.concord.plugins.basic",
    "smtp-tasks",
    "1.76.1",
);

let mut resolver = Resolver::default();

// default implementations, you can plug in your own
let url_fetcher = DefaultUrlFetcher {};
let pom_parser = DefaultPomParser {};

let project = resolver
    .build_effective_pom(&artifact, &url_fetcher, &pom_parser)
    .unwrap();

let project = resolver
    .build_effective_pom(&artifact, &url_fetcher, &pom_parser)
    .unwrap();
    

build a snapshot and deploy the war-file into a J2EE-Container.

jar -cvf projectname.war *  

The default Web-Side shows 2 text-fields
The first text-field is for editing and (java-text can be pasted there). 
The second text-field will pop up showing the conversion from Java to Rust

Note:
The java-code can be a class, a part of a class or a simple statement.
The code must be (java-)syntactically correct. The conversion is not perfect and will require some editing. " A work in Progress ".

### functions

    * conversion of **declarations** Java: _"Type name = init"_ to _"let name: Type = init"_
    * **conversion of arrays** type[] to vectors
    * **snake-case** for camelcase-identifiers starting with lower case
    * mapping of **primitive** types
    * **&amp;self** as first parameter in non static methods
    * **new** type becomes type::new
    * **class becomes struct** with its instance-variables
    * class-methods can be found in extra block **impl for** <class-name> { }
    * decide about usage of **mut**
    * conversion of **integer-constants** to float-constants where necessary
    * conversion of **Exceptions** into Results
    * **static methods** are called using ::
    * **@Test** is converted to #[test]
    * **interfaces** become traits
    * Java methods with declared **throws** return Result&lt;_,Rc&lt;Exception&gt;&gt; used
      rust code can be found in directory rust.


Note:
    * javadoc-comments do not convert


