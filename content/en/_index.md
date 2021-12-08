+++
title = "Samples Style Guide"
linkTitle = "Samples Style Guide"
 
+++
 
 
# Samples Style Guide
 
## Introduction
 
This document serves as a definition of our samples standards for both
standalone snippets and sample applications. It is intended to help encourage
consistency and best practices when authoring code intended to teach others.
 
Even if not specifically mentioned in the guide, all samples should make
best-efforts to achieve the following goals wherever possible:
 
* **Copy-paste-runnable** - Users should be able to copy, paste, and run the
code into their environment with as few changes as possible. Samples should be
easy as possible for a user to run.
 
* **Teach through code** - Samples should teach users both how and _why_
specific best practices should be implemented and performed when interacting
with our services.
 
* **Idiomatic** - Samples should encourage idiomatic and best practices specific
to language, framework, or service.

## Structure

### Region tags
 
Each code snippet should have a region tag to define which parts of the snippet
are displayed from the documentation. Each region tag should be:
* Globally unique
* Consistent across the same snippets in different languages
* Begins with the product's region tag prefix
* In snake case

Region tags should show as much of the sample as possible, so that a user can
easily copy and pase the sample into their own environment to run it. 

### Imports
 
Samples should include any imports used in the sample.
 
This is easiest to enforce/detect when the samples are in their own file, so
samples should be structured as such unless their is a compelling reason not to.
 
{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
   // Region tags should start after the package, but before imports.
   // [START product_example]
   import com.example.resource;
 
   public class exampleSnippet {
   // Snippet methods ...
   }
   // [END product_example]
 {{< /tab >}}
 {{< tab header="Python" >}}
  # [START product_example]
  import com.example.resource
 
  def example_snippet():
       # Snippet Content ...
 
  # [END product_example]
 {{< /tab >}}
{{< /tabpane >}}


## Code 

// TODO

## Testing

// TODO

## Additional best practices

// TODO: Language specific? 