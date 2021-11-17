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

### Region Tags

Each snippet should be be contained in its own file, with region tags including
all imports used in the sample.

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

### Region Tags 2

Each snippet should be be contained in its own file, with region tags including
all imports used in the sample.

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